---
title: __readfsbyte, __readfsdword, __readfsqword, __readfsword
ms.date: 11/04/2016
f1_keywords:
- __readfsword
- __readfsdword
- __readfsbyte
- __readfsqword
helpviewer_keywords:
- __readfsword intrinsic
- readfsword intrinsic
- __readfsdword intrinsic
- readfsbyte intrinsic
- __readfsbyte intrinsic
- readfsdword intrinsic
- readfsqword intrinsic
- __readfsqword intrinsic
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
ms.openlocfilehash: f291747d1f46ebdf3ea1f71cd9ab7e074058201d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036806"
---
# <a name="readfsbyte-readfsdword-readfsqword-readfsword"></a>__readfsbyte, __readfsdword, __readfsqword, __readfsword

**Seção específica da Microsoft**

Ler a memória de um local especificado por um deslocamento relativo ao início do segmento FS.

## <a name="syntax"></a>Sintaxe

```
unsigned char __readfsbyte(
   unsigned long Offset
);
unsigned short __readfsword(
   unsigned long Offset
);
unsigned long __readfsdword(
   unsigned long Offset
);
unsigned __int64 __readfsqword(
   unsigned long Offset
);
```

#### <a name="parameters"></a>Parâmetros

*Offset*<br/>
[in] O deslocamento do início do `FS` leiam.

## <a name="return-value"></a>Valor de retorno

O conteúdo da memória do byte, word, palavras duplas ou quadword (conforme indicado pelo nome da função chamada) no local `FS:[Offset]`.

## <a name="requirements"></a>Requisitos

|Intrínseco|Arquitetura|
|---------------|------------------|
|`__readfsbyte`|x86|
|`__readfsdword`|x86|
|`__readfsqword`|x86|
|`__readfsword`|x86|

**Arquivo de cabeçalho** \<intrin. h >

## <a name="remarks"></a>Comentários

Essas rotinas estão disponíveis apenas como intrínsecos.

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)<br/>
[Intrínsecos do compilador](../intrinsics/compiler-intrinsics.md)