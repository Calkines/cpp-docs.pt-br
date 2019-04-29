---
title: /guard (habilitar proteção do fluxo de controle)
ms.date: 11/04/2016
f1_keywords:
- /guard
- VC.Project.VCCLCompilerTool.ControlFlowGuard
ms.assetid: be495323-f59f-4cf3-a6b6-8ee69e6a19dd
ms.openlocfilehash: e6a8a1545b97976cbe82d1c81b0e70c3dac3a266
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270796"
---
# <a name="guard-enable-control-flow-guard"></a>/guard (habilitar proteção do fluxo de controle)

Habilite a geração de compilador de verificações de segurança de proteção de fluxo de controle.

## <a name="syntax"></a>Sintaxe

```
/guard:cf[-]
```

## <a name="remarks"></a>Comentários

O **/Guard: CF** opção faz com que o compilador analisar o fluxo de controle para destinos de chamada indireta em tempo de compilação e, em seguida, inserir o código para verificar se os destinos em tempo de execução. Por padrão, **/Guard: CF** está desativado e deve ser habilitado explicitamente. Para desabilitar explicitamente essa opção, use **/guard:cf-**.

**Visual Studio 2017 e posterior**: Essa opção adiciona proteções para **alternar** instruções que geram saltar tabelas.

Quando o **/Guard: CF** opção de proteção de fluxo de controle (CFG) for especificada, o compilador e vinculador inserir verificações de segurança de tempo de execução extra para detectar tentativas de comprometer seu código. Durante a compilação e vinculação, todas as chamadas indiretas em seu código são analisadas para localizar todos os locais que o código pode acessar quando ele é executado corretamente. Essas informações são armazenadas em estruturas adicionais nos cabeçalhos de seus binários. O compilador também injeta uma verificação antes de cada chamada indireta em seu código que garante que o destino é um dos locais verificados. Se a verificação falhar em tempo de execução em um sistema operacional com suporte a CFG, o sistema operacional fecha o programa.

Um ataque comum no software tira proveito de bugs na manipulação de entradas extremas ou inesperadas. Concebidas cuidadosamente entrada para o aplicativo pode substituir um local que contém um ponteiro para o código executável. Isso pode ser usado para redirecionar o fluxo de controle para o código controlado pelo invasor. As verificações de tempo de execução CFG não corrigir os bugs de corrupção de dados em seu executável. Eles em vez disso, torna mais difícil para um invasor usá-los para executar código arbitrário. CFG é uma ferramenta de atenuação que impede chamadas para locais diferentes pontos de entrada de função em seu código. Ele é semelhante a como prevenção de execução de dados (DEP), [/GS](gs-buffer-security-check.md) , as verificações de pilha e [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) e [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) randomização de layout de espaço (ASLR) mais baixa de endereços a chances de que seu código se torna um vetor de exploração.

O **/Guard: CF** opção deve ser passada para os dois o compilador e vinculador para compilar o código que usa o CFG explorar técnica de mitigação. Se o binário é criado usando um único `cl` de comando, o compilador passa a opção para o vinculador. Se você compilar e vincular separadamente, a opção deve ser definida em comandos do compilador e vinculador. A opção de vinculador /DYNAMICBASE também é necessária. Para verificar se o seu binário tem dados CFG, use o `dumpbin /headers /loadconfig` comando. Tem habilitado o CFG binários `Guard` na lista de características EXE ou DLL e os sinalizadores de proteção incluem `CF Instrumented` e `FID table present`.

O **/Guard: CF** opção é incompatível com [/ZI](z7-zi-zi-debug-information-format.md) (Edit and Continue informações de depuração) ou [/clr](clr-common-language-runtime-compilation.md) (Common Language Runtime Compilation).

Código compilado usando **/Guard: CF** podem ser vinculados a bibliotecas e arquivos que não são compilados usando a opção de objeto. Somente nesse código, quando também vinculado usando o **/Guard: CF** opção e executar em um sistema operacional com suporte a CFG, tem proteção CFG. Porque o código compilado sem a opção não irá parar um ataque, é recomendável que você use a opção em todo o código que você compilar. Há um pequeno tempo de execução de custo para CFG verificações, mas a análise do compilador tenta otimizar as verificações de saltos indiretos que podem ser comprovados para ser seguro.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. Selecione **propriedades de configuração**, **C/C++**, **geração de código**.

1. Selecione o **proteção de fluxo de controle** propriedade.

1. No controle de lista suspensa, escolha **Yes** para habilitar a proteção de fluxo de controle, ou **não** para desabilitá-lo.

## <a name="see-also"></a>Consulte também

[Opções do compilador MSVC](compiler-options.md)<br/>
[Sintaxe da linha de comando do compilador MSVC](compiler-command-line-syntax.md)
