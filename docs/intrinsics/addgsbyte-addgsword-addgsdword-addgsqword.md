---
title: __addgsbyte, __addgsword, __addgsdword, __addgsqword
ms.date: 11/04/2016
f1_keywords:
- __addgsdword
- __addgsqword
- __addgsword_cpp
- __addgsword
- __addgsbyte_cpp
- __addgsqword_cpp
- __addgsbyte
- __addgsdword_cpp
helpviewer_keywords:
- __addgsword intrinsic
- __addgsqword intrinsic
- __addgsdword intrinsic
- __addgsbyte intrinsic
ms.assetid: 4fa03e69-d849-49ed-ba37-1d3aa23c2a21
ms.openlocfilehash: 2439e541332705ec5330a7ee6e703c99712f7e8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667594"
---
# <a name="addgsbyte-addgsword-addgsdword-addgsqword"></a>__addgsbyte, __addgsword, __addgsdword, __addgsqword

**Seção específica da Microsoft**

Adicione um valor para um local de memória especificado por um deslocamento em relação ao início do `GS` segmento.

## <a name="syntax"></a>Sintaxe

```
void __addgsbyte( 
   unsigned long Offset, 
   unsigned char Data 
);
void __addgsword( 
   unsigned long Offset, 
   unsigned short Data 
);
void __addgsdword( 
   unsigned long Offset, 
   unsigned long Data 
);
void __addgsqword( 
   unsigned long Offset, 
   unsigned __int64 Data 
);
```

#### <a name="parameters"></a>Parâmetros

*deslocamento*<br/>
[in] O deslocamento do início do `GS`.

*Dados*<br/>
[in] O valor a ser adicionado ao local da memória.

## <a name="requirements"></a>Requisitos

|Intrínseco|Arquitetura|
|---------------|------------------|
|`__addgsbyte`|X64|
|`__addgsword`|X64|
|`__addgsdword`|X64|
|`__addgsqword`|X64|

## <a name="remarks"></a>Comentários

Esses intrínsecos estão disponíveis no modo de kernel apenas, e essas rotinas somente estão disponíveis como intrínsecos.

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[__incgsbyte, \__incgsword, \__incgsdword, \__incgsqword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)<br/>
[__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)<br/>
[__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)<br/>
[Intrínsecos do compilador](../intrinsics/compiler-intrinsics.md)