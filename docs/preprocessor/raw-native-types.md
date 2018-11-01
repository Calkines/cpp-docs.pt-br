---
title: raw_native_types
ms.date: 11/04/2016
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: e48aa2ca1469d38b67dcb06a3377713141a158e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620435"
---
# <a name="rawnativetypes"></a>raw_native_types
**Específico do C++**

Desabilita o uso de classes de suporte COM nas funções wrapper de alto nível e força o uso de tipos de dados de nível baixo.

## <a name="syntax"></a>Sintaxe

```
raw_native_types
```

## <a name="remarks"></a>Comentários

Por padrão, os métodos de tratamento de erros de alto nível usam as classes de suporte COM [bstr_t](../cpp/bstr-t-class.md) e [variant_t](../cpp/variant-t-class.md) em vez da `BSTR` e `VARIANT` ponteiros de interface bruto COM e tipos de dados. Essas classes encapsulam os detalhes da alocação e da desalocação do armazenamento de memória para esses tipos de dados e simplificam significativamente as operações de conversão e de conversão de tipos.

**FIM de específico de C++**

## <a name="see-also"></a>Consulte também

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import diretiva](../preprocessor/hash-import-directive-cpp.md)