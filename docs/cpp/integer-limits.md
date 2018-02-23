---
title: Limites de inteiro | Microsoft Docs
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5fc79f225d340777751ca513c0fb47dd33e17ad
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="integer-limits"></a>Limites de inteiro

**Seção específica da Microsoft**

Os limites para tipos de inteiros estão listadas na tabela a seguir. Esses limites também são definidos no arquivo de cabeçalho padrão < Limits. h >.

## <a name="limits-on-integer-constants"></a>Limites em constantes de inteiro

|Constante|Significado|Valor|
|--------------|-------------|-----------|
|**CHAR_BIT**|Número de bits na menor variável que não é um campo de bit.|8|
|**SCHAR_MIN**|Valor mínimo para uma variável do tipo **signed char**.|-128|
|**SCHAR_MAX**|Valor máximo para uma variável do tipo **signed char**.|127|
|**UCHAR_MAX**|Valor máximo para uma variável do tipo **unsigned char**.|255 (0xff)|
|**CHAR_MIN**|Valor mínimo para uma variável do tipo **char**.|-128; 0 se a opção /J for usada|
|**CHAR_MAX**|Valor máximo para uma variável do tipo **char**.|127; 255 se a opção /J for usada|
|**MB_LEN_MAX**|Número máximo de bytes em uma constante de vários caracteres.|5|
|**SHRT_MIN**|Valor mínimo para uma variável do tipo **short**.|-32768|
|**SHRT_MAX**|Valor máximo para uma variável do tipo **short**.|32767|
|**USHRT_MAX**|Valor máximo para uma variável do tipo **unsigned short**.|65535 (0xffff)|
|**INT_MIN**|Valor mínimo para uma variável do tipo **int**.|-2147483648|
|**INT_MAX**|Valor máximo para uma variável do tipo **int**.|2147483647|
|**UINT_MAX**|Valor máximo para uma variável do tipo **int não assinado**.|4294967295 (0xffffffff)|
|**LONG_MIN**|Valor mínimo para uma variável do tipo **long**.|-2147483648|
|**LONG_MAX**|Valor máximo para uma variável do tipo **long**.|2147483647|
|**ULONG_MAX**|Valor máximo para uma variável do tipo **unsigned longa**.|4294967295 (0xffffffff)|
|**LLONG_MIN**|Valor mínimo para uma variável do tipo **muito longa**|-9223372036854775808|
|**LLONG_MAX**|Valor máximo para uma variável do tipo **muito longa**|9223372036854775807|
|**ULLONG_MAX**|Valor máximo para uma variável do tipo **longo longo sem sinal**|18446744073709551615 (0xffffffffffffffff)|

Se um valor exceder a representação do maior inteiro, o compilador da Microsoft gera um erro.

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[Limites flutuantes](../cpp/floating-limits.md)  