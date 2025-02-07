---
title: 'Como: Gerenciar símbolos'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
- vc.editors.symbol.changing.unassigned
- vc.editors.symbol.shared.calculated
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
- numeric values
- symbols [C++], numeric values
- numeric values, changing symbols
- symbols [C++], value restrictions
- restrictions, symbol values
- resource files [C++], multiple
- Resource Includes dialog box [C++]
- symbol header files [C++], changing names
- symbols [C++], symbol header files
- Resource.h
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: ebf10ade734d321c5a83644110d3511e4b6c827a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406971"
---
# <a name="how-to-manage-symbols"></a>Como: Gerenciar símbolos

Quando você cria um novo recurso ou objeto de recurso, o ambiente de desenvolvimento atribui a ele um nome de símbolo padrão, por exemplo, `IDD_DIALOG1`. Você pode usar o [janela de propriedades](/visualstudio/ide/reference/properties-window) para alterar o nome de símbolo padrão ou para alterar o nome de qualquer símbolo já está associado com um recurso.

Símbolos associados com um único recurso, você também pode usar o **propriedades** janela para alterar o valor de símbolo. Você pode usar o [caixa de diálogo símbolos de recurso](../windows/resource-symbols-dialog-box.md) para alterar o valor de símbolos que não estão atribuídos a um recurso.

Normalmente, todos os símbolos definições são salvos no `Resource.h`. No entanto, talvez você precise alterar isso incluir o nome de arquivo para que você pode, por exemplo, trabalhar com mais de um arquivo de recurso no mesmo diretório.

> [!NOTE]
> Se seu projeto já não contiver um arquivo. RC, consulte [como: Criar recursos](../windows/how-to-create-a-resource-script-file.md).

## <a name="symbol-name-restrictions"></a>Restrições de nome do símbolo

As restrições em nomes de símbolos são da seguinte maneira:

- Todos os [símbolos](../windows/symbols-resource-identifiers.md) deve ser exclusivo dentro do escopo do aplicativo para evitar definições conflitantes do símbolo nos arquivos de cabeçalho.

- Caracteres válidos para um nome de símbolo incluem A-Z, a-z, 0 a 9 e sublinhados (_).

- Nomes de símbolo não podem começar com um número e são limitados a 247 caracteres.

- Nomes de símbolo não podem conter espaços.

- Nomes de símbolos não diferencia maiusculas de minúsculas, mas no caso da primeira definição de símbolo é preservado.

   O arquivo de cabeçalho que define os símbolos é usado pelo compilador/editor de recursos e programas do C++ para fazer referência a recursos definidos em um arquivo de recurso. Dois nomes de símbolo que diferem apenas em maiusculas, o programa de C++ verá dois símbolos separados, enquanto o compilador/editor de recurso verá os dois nomes como uma referência a um único símbolo.

> [!NOTE]
> Se você não seguir o esquema de nome de símbolo padrão (ID*_[keyword]) descritas abaixo e o nome do símbolo, por acaso, é o mesmo como uma palavra-chave conhecida do compilador do script de recurso, tentar criar o arquivo de script de recurso resulta na geração de erro aparentemente aleatório Isso é difícil de diagnosticar. Para evitar isso, seguem o esquema de nomenclatura padrão.

Nomes de símbolos têm prefixos descritivos que indicam o tipo de recurso ou objeto que eles representam. Esses prefixos descritivos começam com a ID da combinação de texto. A biblioteca Microsoft Foundation Class (MFC) usa o símbolo mostradas na tabela a seguir de convenções de nomenclatura:

|Categoria|Prefixo|Use|
|--------------|------------|---------|
|Recursos|IDR_, IDD_, IDC_, IDI_, IDB_|Acelerador ou menu (e recursos associados ou personalizados), caixa de diálogo, cursor, ícone, bitmap|
|Itens de menu|ID_|Item de menu|
|Comandos|ID_|Comando|
|Controles e janelas filho|IDC_|Controle|
|Cadeias de caracteres|IDS_|Cadeia de caracteres na tabela de cadeia de caracteres|
|MFC|AFX_|Reservado para símbolos predefinidos do MFC|

### <a name="to-change-a-symbol-name-id"></a>Para alterar um nome de símbolo (ID)

1. Na [exibição de recurso](how-to-create-a-resource-script-file.md#create-resources), selecione o recurso.

1. No **propriedades** janela, digite um novo nome de símbolo ou selecione na lista de símbolos existentes na **ID** caixa.

   Se você digitar um novo nome de símbolo, que foi atribuído automaticamente um valor.

> [!NOTE]
> Você pode usar o [caixa de diálogo símbolos de recurso](../windows/resource-symbols-dialog-box.md) para alterar os nomes de símbolos que não estão atribuídos a um recurso.

## <a name="symbol-value-restrictions"></a>Restrições de valor do símbolo

Um valor de símbolo pode ser qualquer inteiro expressado da maneira normal para `#define` diretivas de pré-processador. Aqui estão alguns exemplos de valores de símbolo:

```
18
4001
0x0012
-3456
```

Valores de símbolo para recursos como aceleradores, bitmaps, cursores, caixas de diálogo, ícones, menus, tabelas de cadeia de caracteres e versão devem ser números decimais no intervalo entre 0 e 32.767 de informações, mas não pode ser hexadecimais. Valores de símbolo para partes de recursos, como controles de caixa de diálogo ou cadeias de caracteres individuais na tabela de cadeia de caracteres, podem ser de 0 a 65.534 ou de -32.768 a 32.767. Para obter mais informações sobre intervalos de número, consulte [TN023: Recursos MFC padrão](../mfc/tn023-standard-mfc-resources.md).

Símbolos de recurso são números de 16 bits. Você pode inseri-las como com ou sem sinal, no entanto, eles são usados internamente como inteiros sem sinal, portanto, os números negativos serão convertidos em seu valor positivo correspondente.

Algumas limitações de valores de símbolo são:

- O ambiente de desenvolvimento do Visual Studio e o MFC usam alguns intervalos de número para fins especiais. Todos os números com o conjunto de bits mais significativo (-32.768 a -1 ou 32.768 para 65.534, dependendo do sinal) são reservados pelo MFC.

- Você não pode definir um valor de símbolo usando outras cadeias de caracteres de símbolo. Por exemplo, a seguinte definição de símbolo não tem suporte:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Você não pode usar macros de pré-processador com argumentos como definições de valor. O exemplo a seguir não é uma expressão válida, independentemente de qual `ID` é avaliada como em tempo de compilação:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

- Seu aplicativo pode ter um arquivo existente que contém símbolos definidos com expressões.

### <a name="to-change-a-symbol-value"></a>Para alterar um valor de símbolo

1. Na [exibição de recurso](how-to-create-a-resource-script-file.md#create-resources), selecione o recurso.

1. No **propriedades** , digite o nome do símbolo seguido por um sinal de igual e um número inteiro na **ID** caixa, por exemplo:

    ```
    IDC_EDITNAME=5100
    ```

   O novo valor é armazenado no arquivo de cabeçalho de símbolo na próxima vez que você salvar o projeto. Somente o nome do símbolo permanece visível na caixa ID e o sinal de igual e o valor não são exibidos depois que eles são validados.

## <a name="change-or-delete-symbols"></a>Alterar ou excluir símbolos

Enquanto estiver na [caixa de diálogo símbolos de recurso](../windows/resource-symbols-dialog-box.md), você pode editar ou excluir símbolos existentes que já não são atribuídos a um recurso ou objeto.

### <a name="to-change-an-unassigned-symbol"></a>Para alterar um símbolo não atribuído

1. No **nome** caixa, selecione o símbolo não atribuído e escolha **alteração**.

1. Editar o nome do símbolo ou um valor nas caixas fornecidas na **alterar símbolo** caixa de diálogo.

> [!NOTE]
> Para alterar um símbolo que é atribuído a um recurso ou objeto, você deve usar o editor de recurso ou **propriedades** janela.

### <a name="to-delete-an-unassigned-unused-symbol"></a>Para excluir um símbolo (não usado) não atribuído

No **símbolos de recurso** caixa de diálogo, selecione o símbolo que você deseja excluir e escolha **excluir**.

> [!NOTE]
> Antes de excluir um símbolo não utilizado em um arquivo de recurso, verifique se que ele não é usado em outro lugar no programa ou pelos arquivos de recursos incluídos no tempo de compilação.

## <a name="include-symbols"></a>Incluir símbolos

Na primeira vez em que o ambiente de desenvolvimento lê um arquivo de recurso criado por outro aplicativo, ele marca todos os arquivos de cabeçalho incluídos como somente leitura. Embora você possa usar o [caixa de diálogo recurso inclui](../windows/resource-includes-dialog-box.md) para adicionar arquivos de cabeçalho de símbolo somente leitura adicionais.

Um motivo que você talvez queira usar definições de símbolo somente leitura é para arquivos de símbolo que você planeja compartilhar entre vários projetos.

Você também pode usar arquivos de símbolo incluídos quando você tiver recursos existentes com as definições de símbolo que usam expressões em vez de inteiros simples para definir o valor de símbolo. Por exemplo:

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

O ambiente será interprete corretamente esses símbolos calculados, desde que:

- Os símbolos calculados são colocados em um arquivo de símbolos somente leitura.

- Seu arquivo de recursos contém recursos aos quais esses símbolos calculados já estão atribuídos.

- Uma expressão numérica é esperada.

> [!NOTE]
> Se uma cadeia de caracteres ou uma expressão numérica é esperada, a expressão não é avaliada.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Para incluir símbolos compartilhados de (somente leitura) no seu arquivo de recurso

1. Na [exibição de recurso](how-to-create-a-resource-script-file.md#create-resources), clique com botão direito seu *. rc* arquivo e selecione [recurso inclui](../windows/resource-includes-dialog-box.md).

1. No **diretivas de símbolo somente leitura** caixa, use o `#include` diretiva do compilador para especificar o arquivo onde você deseja que os símbolos somente leitura sejam mantidos.

   Não chame o arquivo `Resource.h`, já que é o nome de arquivo normalmente usado pelo arquivo de cabeçalho de símbolo principal.

   > [!NOTE]
   > O que você digitar o **diretivas de símbolo somente leitura** caixa está incluída no arquivo de recurso exatamente conforme você o digita. Certifique-se de que você digitou não contém erros de ortografia ou de sintaxe.

   Use o **diretivas de símbolo somente leitura** caixa para incluir arquivos com apenas definições de símbolo. Não inclua definições de recursos, definições de recurso duplicados else serão criadas quando o arquivo é salvo.

1. Coloque os símbolos no arquivo especificado por você.

   Os símbolos nos arquivos incluídos dessa maneira são avaliados sempre que você abrir o arquivo de recurso, mas eles não são substituídos no disco quando você salvar o arquivo.

1. Selecione **OK**.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Para alterar o nome do arquivo de cabeçalho de símbolo de recurso

1. Na [exibição de recurso](how-to-create-a-resource-script-file.md#create-resources), clique com botão direito seu *. rc* arquivo e escolha [recurso inclui](../windows/resource-includes-dialog-box.md).

1. No **arquivo de cabeçalho de símbolo** , digite o novo nome para o arquivo de inclusão.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte também

[Identificadores de recursos (símbolos)](../windows/symbols-resource-identifiers.md)<br/>
[Como: criar símbolos](../windows/creating-new-symbols.md)<br/>
[IDs de símbolos predefinidos](../windows/predefined-symbol-ids.md)<br/>