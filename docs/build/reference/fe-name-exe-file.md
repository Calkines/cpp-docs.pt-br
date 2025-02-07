---
title: /Fe (nomear arquivo EXE)
ms.date: 11/04/2016
f1_keywords:
- /fe
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
ms.openlocfilehash: 5901ef1997cfea84c97b6d91b30335ff7dbc1d9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292609"
---
# <a name="fe-name-exe-file"></a>/Fe (nomear arquivo EXE)

Especifica um nome e um diretório para o arquivo de .exe ou a DLL criada pelo compilador.

## <a name="syntax"></a>Sintaxe

> **/Fe**[_pathname_] **/Fe:** _pathname_

### <a name="arguments"></a>Arguments

*pathname*<br/>
O caminho relativo ou absoluto e o nome de arquivo base ou o caminho relativo ou absoluto para um diretório ou o nome de arquivo base a ser usado para o executável gerado.

## <a name="remarks"></a>Comentários

O **/Fe** opção permite que você especifique o diretório de saída, o nome do executável de saída ou ambos, para o arquivo executável gerado. Se *pathname* termina em um separador de caminho (**&#92;**), supõe-se especificar somente o diretório de saída. Caso contrário, o último componente do *pathname* é usado como o nome base do arquivo de saída e o restante das *pathname* Especifica o diretório de saída. Se *pathname* não tem qualquer separador de caminho, supõe-se para especificar o nome do arquivo de saída no diretório atual. O *pathname* deve ser colocado entre aspas duplas (**"**) se ele contiver quaisquer caracteres que não podem ser um caminho curto, como espaços, caracteres ou componentes de caminho mais de oito caracteres estendidos longa.

Quando o **/Fe** opção não for especificada, ou quando um arquivo base nome não for especificado em *pathname*, o compilador fornece o arquivo de saída de um nome padrão usando o nome base do que o primeiro arquivo de origem ou de objeto especificado na linha de comando e a extensão .exe ou. dll.

Se você especificar o [/c (compilar sem vinculação)](c-compile-without-linking.md) opção **/Fe** não tem nenhum efeito.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. Abra o **propriedades de configuração** > **vinculador** > **geral** página de propriedades.

1. Modificar a **arquivo de saída** propriedade. Escolha **OK** para salvar suas alterações.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="example"></a>Exemplo

A linha de comando a seguir compila e vincula todos os arquivos de origem de C no diretório atual. O arquivo executável resultante é denominado PROCESS.exe e é criado no diretório "C:\Users\User Name\repos\My Project\bin".

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>Exemplo

A linha de comando a seguir cria um arquivo executável em `C:\BIN` com o mesmo nome base do primeiro arquivo de origem no diretório atual:

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>Consulte também

[Opções do arquivo de saída (/F)](output-file-f-options.md)<br/>
[Opções do compilador MSVC](compiler-options.md)<br/>
[Sintaxe da linha de comando do compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificando o nome de caminho](specifying-the-pathname.md)<br/>
