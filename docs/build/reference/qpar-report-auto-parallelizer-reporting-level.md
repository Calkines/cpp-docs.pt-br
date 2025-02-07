---
title: /Qpar-report (nível de relatórios do paralelizador automático)
ms.date: 11/04/2016
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
ms.openlocfilehash: 25732900fa201258331dcb8eee96af9ba97a6def
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319948"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-report (nível de relatórios do paralelizador automático)

Habilita o recurso de relatório do compilador [Paralelizador automático](../../parallel/auto-parallelization-and-auto-vectorization.md) e especifica o nível de mensagens informativas de saída durante a compilação.

## <a name="syntax"></a>Sintaxe

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>Comentários

**/Qpar-report:1**<br/>
Gera uma mensagem informativa para loops que são colocados em paralelo.

**/Qpar-report:2**<br/>
Gera uma mensagem informativa para loops que são colocados em paralelo e também para loops que não são colocados em paralelo, juntamente com um código de motivo.

As mensagens são relatadas para stdout. Se nenhuma mensagem informativa for relatada, o código não contém nenhum loops ou o nível de relatório não foi definido para loops de relatório que não são colocados em paralelo. Para obter mais informações sobre códigos de motivo e mensagens, consulte [mensagens do Vetorizador e Paralelizador](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>Para definir a opção de compilador /Qpar-report no Visual Studio

1. No **Gerenciador de Soluções**, abra o menu de atalho para o projeto e escolha **Propriedades**.

1. No **páginas de propriedades** caixa de diálogo **C/C++**, selecione **linha de comando**.

1. No **opções adicionais** , digite `/Qpar-report:1` ou `/Qpar-report:2`.

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>Para definir a opção do compilador /Qpar-report programaticamente

- Use o exemplo de código em <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte também

[Opções /Q (operações de nível baixo)](q-options-low-level-operations.md)<br/>
[Opções do compilador MSVC](compiler-options.md)<br/>
[Sintaxe da linha de comando do compilador MSVC](compiler-command-line-syntax.md)<br/>
[Programação paralela em código nativo](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)
