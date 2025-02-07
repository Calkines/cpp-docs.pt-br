---
title: namespace padrão
ms.date: 12/30/2016
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
ms.openlocfilehash: b67aedc791ed41e93268d9e9f44492781940d55e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740510"
---
# <a name="default-namespace"></a>namespace padrão

Os `default` escopos de namespace são os tipos internos com suporte do C++/CX.

## <a name="syntax"></a>Sintaxe

```
namespace default;
```

### <a name="members"></a>Membros

Todos os tipos internos herdam os membros a seguir.

|||
|-|-|
|[default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md)|Determina se o objeto especificado é igual ao objeto atual.|
|[default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|Retorna o código hash para essa instância.|
|[default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md)|Retorna uma cadeia de caracteres que representa o tipo atual.|
|[default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md)|Retorna uma cadeia de caracteres que representa o tipo atual.|

### <a name="built-in-types"></a>Tipos internos

|Nome|Descrição|
|----------|-----------------|
|`char16`|Um valor não numérico de 16 bits que representa um ponto de código Unicode (UTF-16).|
|`float32`|Um número de ponto flutuante IEEE 754 de 32 bits.|
|`float64`|Um número de ponto flutuante IEEE 754 de 64 bits.|
|`int16`|Um inteiro de 16 bits com sinal.|
|`int32`|Um inteiro com sinal de 32 bits.|
|`int64`|Um inteiro com sinal de 64 bits.|
|`int8`|Um valor numérico com sinal de 8 bits.|
|`uint16`|Um inteiro de 16 bits sem sinal.|
|`uint32`|Um inteiro sem sinal de 32 bits.|
|`uint64`|Um inteiro sem sinal de 64 bits.|
|`uint8`|Um valor numérico sem sinal de 8 bits.|

### <a name="requirements"></a>Requisitos

**Cabeçalho:** vccorlib.h

## <a name="see-also"></a>Consulte também

[Referência da linguagem C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
