---
title: '/ZC: externconstexpr (habilitar variáveis de constexpr externas)'
ms.date: 02/28/2018
f1_keywords:
- /Zc:externConstexpr
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
ms.openlocfilehash: 3c18a5310646ea39c0599f709e9fddc3990b7a2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315749"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/ZC: externconstexpr (habilitar variáveis de constexpr externas)

O **/ZC: externconstexpr** opção de compilador instrui o compilador a estar em conformidade com o padrão de C++ e permitir que a vinculação externa para `constexpr` variáveis. Por padrão, o Visual Studio sempre oferece uma `constexpr` ligação interna variável, mesmo se você especificar o `extern` palavra-chave.

## <a name="syntax"></a>Sintaxe

> **/Zc:externConstexpr**[**-**]

## <a name="remarks"></a>Comentários

O **/ZC: externconstexpr** opção de compilador faz com que o compilador aplicar a vinculação externa para as variáveis declaradas usando `extern constexpr`. Em versões anteriores do Visual Studio e, por padrão ou se **/Zc:externConstexpr-** for especificado, vinculação interna para o Visual Studio aplicará `constexpr` mesmo variáveis a `extern` palavra-chave é usada. O **/ZC: externconstexpr** opção está disponível a partir do Visual Studio 2017 15.6 de atualização. e é desativado por padrão. O [/permissive--](permissive-standards-conformance.md) opção não permite **/ZC: externconstexpr**.

Se um arquivo de cabeçalho contém uma variável declarada `extern constexpr`, ele deve ser marcado [__declspec(selectany)](../../cpp/selectany.md) para mesclar as declarações duplicadas em uma única instância no binário vinculado. Caso contrário, você poderá ver erros de vinculador, por exemplo, LNK2005, quanto a violações de regra de definição.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para definir essa opção do compilador no Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. Selecione o **propriedades de configuração** > **C/C++** > **linha de comando** página de propriedades.

1. Adicione **/ZC: externconstexpr** ou **/Zc:externConstexpr-** para o **opções adicionais:** painel.

## <a name="see-also"></a>Consulte também

[/Zc (conformidade)](zc-conformance.md)<br/>
[Palavra-chave auto](../../cpp/auto-keyword.md)
