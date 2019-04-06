---
title: __ll_lshift
ms.date: 11/04/2016
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 5a91ce5db46b19be570f8d48a584a2caeabcc163
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024459"
---
# <a name="lllshift"></a>__ll_lshift

**Específico da Microsoft**

Desloca o valor fornecido de 64 bits para a esquerda pelo número especificado de bits.

## <a name="syntax"></a>Sintaxe

```
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

#### <a name="parameters"></a>Parâmetros

*Máscara*<br/>
[in] O valor de inteiro de 64 bits para deslocar para a esquerda.

*nBit*<br/>
[in] O número de bits a deslocar.

## <a name="return-value"></a>Valor de retorno

A máscara deslocados para a esquerda pelo `nBit` bits.

## <a name="requirements"></a>Requisitos

|Intrínseco|Arquitetura|
|---------------|------------------|
|`__ll_lshift`|x86, x64|

**Arquivo de cabeçalho** \<intrin. h >

## <a name="remarks"></a>Comentários

Se você compilar seu programa usando a arquitetura de 64 bits e `nBit` é maior do que 63, é o número de bits a deslocar `nBit` módulo 64. Se você compilar seu programa usando a arquitetura de 32 bits e `nBit` é maior do que 31, o número de bits a deslocar é `nBit` módulo 32.

O `ll` o nome indica que esta é uma operação no `long long` (`__int64`).

## <a name="example"></a>Exemplo

```
// ll_lshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_lshift)

int main()
{
   unsigned __int64 Mask = 0x100;
   int nBit = 8;
   Mask = __ll_lshift(Mask, nBit);
   cout << hex << Mask << endl;
}
```

## <a name="output"></a>Saída

```
10000
```

**Observação** há nenhuma versão sem sinal da operação de deslocamento à esquerda. Isso ocorre porque `__ll_lshift` já usa um parâmetro de entrada sem sinal. Ao contrário o deslocamento para a direita, não há nenhuma dependência de entrada para o deslocamento à esquerda, porque o bit menos significativo no resultado é sempre definido como zero, independentemente do sinal do valor deslocado.

**FIM de Específico da Microsoft**

## <a name="see-also"></a>Consulte também

[__ll_rshift](../intrinsics/ll-rshift.md)<br/>
[__ull_rshift](../intrinsics/ull-rshift.md)<br/>
[Intrínsecos do compilador](../intrinsics/compiler-intrinsics.md)