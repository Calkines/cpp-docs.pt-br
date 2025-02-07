---
title: /WHOLEARCHIVE (incluir todos os arquivos de objeto de biblioteca)
ms.date: 11/04/2016
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: db99816b18110b424647603196040997044e7fbd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316425"
---
# <a name="wholearchive-include-all-library-object-files"></a>/WHOLEARCHIVE (incluir todos os arquivos de objeto de biblioteca)

Força o vinculador a incluir todos os arquivos de objeto na biblioteca estática no executável vinculado.

## <a name="syntax"></a>Sintaxe

> /WHOLEARCHIVE[:*library*]

## <a name="remarks"></a>Comentários

A opção /WHOLEARCHIVE força o vinculador a incluir todos os arquivos de objeto de qualquer um uma biblioteca estática especificada ou se nenhuma biblioteca for especificada, em todas as bibliotecas estáticas especificadas para o LINK de comando. Para especificar a opção /WHOLEARCHIVE para várias bibliotecas, você pode usar mais de uma opção /WHOLEARCHIVE na linha de comando do vinculador. Por padrão, o vinculador inclui arquivos de objeto na saída vinculada somente se eles exportam símbolos referenciados por outros arquivos de objeto no executável. A opção /WHOLEARCHIVE faz com que o vinculador trate todos os arquivos de objeto arquivados em uma biblioteca estática, como se eles foram especificados individualmente na linha de comando do vinculador.

A opção /WHOLEARCHIVE pode ser usada para exportar novamente todos os símbolos de uma biblioteca estática. Isso permite que você certifique-se de que todos os seu código de biblioteca, recursos e metadados são incluídos quando você cria um componente de mais de uma biblioteca estática. Se você vir o aviso LNK4264 quando você cria uma biblioteca estática que contém os componentes de tempo de execução do Windows para exportação, use a opção de /WHOLEARCHIVE ao vincular essa biblioteca em outro aplicativo ou componente.

A opção /WHOLEARCHIVE foi introduzida no Visual Studio 2015 atualização 2.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para definir essa opção do vinculador no Visual Studio

1. Abra o projeto **páginas de propriedade** caixa de diálogo. Para obter mais informações, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. Selecione o **linha de comando** página de propriedade sob **propriedades de configuração**, **vinculador**.

1. Adicione a opção /WHOLEARCHIVE para o **opções adicionais** caixa de texto.

## <a name="see-also"></a>Consulte também

[Referência de vinculador MSVC](linking.md)<br/>
[Opções de vinculador MSVC](linker-options.md)
