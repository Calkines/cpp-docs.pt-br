---
title: Classe Platform::DisconnectedException
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
helpviewer_keywords:
- Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
ms.openlocfilehash: 2d4f8f4cb52fdb7e50c36eb3f0255bd85c15dbb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477136"
---
# <a name="platformdisconnectedexception-class"></a>Classe Platform::DisconnectedException

Gerada quando um objeto de proxy COM tenta referenciar um servidor COM que não existe

## <a name="syntax"></a>Sintaxe

```
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Comentários

Quando a classe A referencia outra classe (classe B), que está em um processo separado, a classe A exige um objeto de proxy para se comunicar com o servidor COM fora do processo que contém a classe B. Às vezes, o servidor pode ficar sem memória sem o reconhecimento da classe A. Neste caso, a exceção RPC_E_DISCONNECTED é gerada e é traduzida como Platform::DisconnectedException. Um cenário no qual isso pode ocorrer é quando uma fonte de evento invoca um representante que lhe foi passado, porém o representante foi destruído em algum momento após ser inscrito no evento. Quando isso ocorre, a fonte do evento remove o representante da sua lista de invocação.

Para obter mais informações, consulte a classe [COMException](../cppcx/platform-comexception-class.md) .

### <a name="requirements"></a>Requisitos

**Mínimo de cliente com suporte:** Windows 8

**Mínimo de servidor com suporte:** Windows Server 2012

**Namespace:** Platform

**Metadados:** platform.winmd

## <a name="see-also"></a>Consulte também

[Classe Platform::COMException](../cppcx/platform-comexception-class.md)