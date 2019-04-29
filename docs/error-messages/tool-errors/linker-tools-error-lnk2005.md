---
title: Erro das Ferramentas de Vinculador LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 8b4f75b90254c702ecb2afb65108278a59df69ed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299199"
---
# <a name="linker-tools-error-lnk2005"></a>Erro das Ferramentas de Vinculador LNK2005

> *símbolo* já definido no objeto

O símbolo *símbolo* foi definido mais de uma vez.

Esse erro é seguido por um erro fatal [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).

### <a name="possible-causes-and-solutions"></a>Possíveis causas e soluções

Em geral, esse erro significa que você tiver danificado o *regra de definição de um*, que permite que apenas uma definição para qualquer modelo usado, a função, o tipo ou o objeto em um arquivo de objeto fornecido e apenas uma definição entre o executável inteiro para objetos visíveis externamente ou funções.

Aqui estão algumas causas comuns desse erro.

- Esse erro pode ocorrer quando um arquivo de cabeçalho define uma variável. Por exemplo, se você incluir esse arquivo de cabeçalho em mais de um arquivo de origem em seu projeto, ocorrerá um erro:

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   As possíveis soluções incluem:

   - Declarar a variável `extern` no arquivo de cabeçalho: `extern int global_int;`, em seguida, defini-lo e, opcionalmente, inicializá-la em apenas um arquivo de origem: `int global_int = 17;`. Essa variável é agora um objeto global que você pode usar em qualquer arquivo de origem, declarando- `extern`, por exemplo, incluindo o arquivo de cabeçalho. Recomendamos essa solução para variáveis que devem ser globais, mas a prática de engenharia de software bom minimiza as variáveis globais.

   - Declarar a variável [estáticos](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;`. Isso restringe o escopo da definição no arquivo de objeto atual e permite que vários arquivos de objeto têm sua própria cópia da variável. Não recomendamos que você definir as variáveis estáticas em arquivos de cabeçalho por causa do potencial de confusão com variáveis globais. Prefira para mover as definições de variáveis estáticas para os arquivos de origem que usá-los.

   - Declarar a variável [selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;`. Isso instrui o vinculador para escolher uma definição para uso por todas as referências externas e descartar o resto. Essa solução às vezes é útil ao combinar as bibliotecas de importação. Caso contrário, não recomendamos-lo como uma maneira de evitar erros de vinculador.

- Esse erro pode ocorrer quando um arquivo de cabeçalho define uma função que não seja `inline`. Se você incluir esse arquivo de cabeçalho em mais de um arquivo de origem, você receberá várias definições da função no executável.

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   As possíveis soluções incluem:

   - Adicionar o `inline` palavra-chave para a função:

        ```h
        // LNK2005_func_inline.h
        inline int sample_function(int k) { return 42 * (k % 167); }
        ```

   - Remova o corpo da função do arquivo de cabeçalho e deixar somente a declaração e implementar a função em apenas um arquivo de origem:

        ```h
        // LNK2005_func_decl.h
        int sample_function(int);
        ```

        ```cpp
        // LNK2005_func_impl.cpp
        int sample_function(int k) { return 42 * (k % 167); }
        ```

- Esse erro também pode ocorrer se você definir funções de membro fora da declaração de classe em um arquivo de cabeçalho:

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Para corrigir esse problema, mova as definições de função de membro dentro da classe. Funções de membro definidas dentro de uma declaração de classe são implicitamente embutidas.

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- Esse erro pode ocorrer se você vincular mais de uma versão da biblioteca padrão ou CRT. Por exemplo, se você tentar vincular tanto a edição de varejo e bibliotecas do CRT debug ou versões estáticas e dinâmicas de uma biblioteca, ou duas versões diferentes de uma biblioteca padrão para seu executável, esse erro pode ser relatado muitas vezes. Para corrigir esse problema, remova apenas uma cópia de cada biblioteca o comando de link. Não recomendamos misturar varejo e bibliotecas ou diferentes versões de uma biblioteca, no mesmo executável de depuração.

   Para informar ao vinculador para usar bibliotecas diferentes dos padrões, na linha de comando, especifique as bibliotecas para usar e, em seguida, usar o [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) opção de desabilitar as bibliotecas padrão. No IDE, adicione referências ao seu projeto para especificar as bibliotecas para usar e, em seguida, abra o **páginas de propriedades** caixa de diálogo para o seu projeto e nos **vinculador**, **entrada** propriedade Defina a **ignorar todas as bibliotecas padrão**, ou **ignorar bibliotecas específicas de padrão** propriedades para desabilitar as bibliotecas padrão.

- Esse erro pode ocorrer se você combinar o uso de bibliotecas estáticas e dinâmicas ao usar o [/clr](../../build/reference/clr-common-language-runtime-compilation.md) opção. Por exemplo, esse erro pode ocorrer se você compilar uma DLL para uso em seu executável que vincula no CRT estático. Para corrigir esse problema, use apenas as bibliotecas estáticas ou apenas as bibliotecas dinâmicas para todo o executável e para quaisquer bibliotecas de que compilação para usar no executável.

- Esse erro pode ocorrer se o símbolo é uma função empacotada (criada compilando com [/Gy](../../build/reference/gy-enable-function-level-linking.md)) e foi incluído em mais de um arquivo, mas foi alterado entre compilações. Para corrigir esse problema, recompile todos os arquivos que incluem a função empacotada.

- Esse erro pode ocorrer se o símbolo é definido de forma diferente em dois objetos de membro em bibliotecas diferentes, e os dois objetos membro são usados. Uma maneira de corrigir esse problema quando as bibliotecas são vinculadas estaticamente é usar o objeto de membro de apenas uma biblioteca e incluir essa biblioteca pela primeira vez na linha de comando do vinculador. Para usar ambos os símbolos, você deve criar uma maneira para diferenciá-los. Por exemplo, se você puder criar as bibliotecas de código-fonte, você pode encapsular cada biblioteca em um namespace exclusivo. Como alternativa, você pode criar uma nova biblioteca de wrapper que usa nomes exclusivos para encapsular as referências a uma das bibliotecas do originais, a nova biblioteca de vínculo para a biblioteca original, em seguida, vincule o executável para sua nova biblioteca, em vez de biblioteca original.

- Esse erro pode ocorrer se um `extern const` variável é definida duas vezes e tem um valor diferente em cada definição. Para corrigir esse problema, defina a constante apenas uma única vez ou usar namespaces ou `enum class` definições para distinguir as constantes.

- Esse erro pode ocorrer se você usar o UUID em combinação com outros arquivos. lib que definam GUIDs (por exemplo, lib e adsiid). Por exemplo:

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   Para corrigir esse problema, adicione [Multiple](../../build/reference/force-force-file-output.md) às opções de linha de comando do vinculador e verifique se o UUID é a primeira biblioteca mencionada.
