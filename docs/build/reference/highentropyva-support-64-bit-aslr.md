---
title: /HIGHENTROPYVA (dar suporte a ASLR de 64 bits)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 5ecbbf8bbd8e74f80f2f5b2d7df0d2ef544112fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291594"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (dar suporte a ASLR de 64 bits)

Especifica se a imagem executável dá suporte a randomização de layout de espaço de endereço de 64 bits de alta entropia (ASLR).

## <a name="syntax"></a>Sintaxe

> **/HIGHENTROPYVA**[**:NO**]

## <a name="remarks"></a>Comentários

**/ HIGHENTROPYVA** modifica o cabeçalho de uma *imagem executável*, um arquivo. dll ou .exe, para indicar se o ASLR pode usar o espaço de endereço inteiro de 64 bits. Quando essa opção é definida em um arquivo executável e todos os módulos dos quais depende, um sistema operacional que dê suporte a ASLR de 64 bits pode rebasear os segmentos da imagem executável no tempo de carregamento usando endereços aleatórios em um espaço de endereço virtual de 64 bits. Esse grande espaço de endereço torna mais difícil para um invasor adivinhar a localização de uma região de memória específica.

Por padrão, **/HIGHENTROPYVA** está habilitado para imagens executáveis de 64 bits. Essa opção exige [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md), que também é habilitado por padrão para as imagens de 64 bits. **/ HIGHENTROPYVA** não é aplicável para imagens executáveis de 32 bits, em que o vinculador ignora a opção. Para desabilitar explicitamente essa opção, use **/highentropyva: no**.

Para **/HIGHENTROPYVA** terem um efeito em tempo de carregamento [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) também deve ser habilitado. **/DYNAMICBASE** é habilitado por padrão e é necessário para habilitar ASLR no Windows Vista e sistemas operacionais posteriores. Versões anteriores do Windows ignoram este sinalizador.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para definir essa opção do vinculador no Visual Studio

1. Abra o projeto **páginas de propriedade** caixa de diálogo. Para obter mais informações, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. Selecione o **propriedades de configuração** > **vinculador** > **linha de comando** página de propriedades.

1. Na **opções adicionais**, insira `/HIGHENTROPYVA` ou `/HIGHENTROPYVA:NO`.

## <a name="see-also"></a>Consulte também

- [Referência de vinculador MSVC](linking.md)
- [Opções de vinculador MSVC](linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Defesas de segurança de Software ISV do Windows](https://msdn.microsoft.com/library/bb430720.aspx)
