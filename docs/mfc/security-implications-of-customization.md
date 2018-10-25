---
title: Implicações de segurança da personalização | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2035e665bd7d8cba502c3516498934f32c2b3dd0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080839"
---
# <a name="security-implications-of-customization"></a>Implicações de segurança da personalização

Este tópico discute uma potencial vulnerabilidade de segurança no MFC.

## <a name="potential-security-weakness"></a>Falha de segurança potencial

MFC permite que o usuário personalize a aparência de uma interface de usuário do aplicativo, por exemplo, a aparência de botões e ícones. MFC também oferece suporte a ferramentas definidas pelo usuário, que permitem ao usuário executar comandos do shell. Uma vulnerabilidade de segurança surge porque as configurações personalizadas do aplicativo são salvos no perfil do usuário no registro. Qualquer pessoa que pode acessar o registro pode editar essas configurações e alterar a aparência do aplicativo ou o comportamento. Por exemplo, um administrador no computador poderia representar um usuário, fazendo com que o aplicativo do usuário executar programas arbitrários (até mesmo de um compartilhamento de rede).

## <a name="workarounds"></a>Soluções alternativas

É recomendável que qualquer uma destas três maneiras para fechar as vulnerabilidades no registro:

- Criptografar os dados armazenados ali

- Store os dados em um arquivo seguro em vez de no registro.

   Para realizar qualquer uma das maneiras duas primeiras, derive uma classe de [classe CSettingsStore](../mfc/reference/csettingsstore-class.md) e substituir seus métodos para implementar a criptografia ou armazenamento fora do registro.

- Você também pode desabilitar as personalizações em seu aplicativo.

## <a name="see-also"></a>Consulte também

[Personalização para MFC](../mfc/customization-for-mfc.md)

