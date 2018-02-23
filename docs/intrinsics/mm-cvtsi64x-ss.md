---
title: _mm_cvtsi64x_ss | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mm_cvtsi64x_ss
dev_langs: C++
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a567b33e55092e7e8e0361faa0ce54b2498827a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss
**Seção específica da Microsoft**  
  
 Gera o [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] versão estendida do inteiro converter 64 bits para o valor de ponto flutuante de precisão única escalares (`cvtsi2ss`) instrução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
__m128 _mm_cvtsi64x_ss(   
   __m128 a,   
   __int64 b   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 [in] `a`  
 Um `__m128` estrutura que contém quatro valores de ponto flutuantes de precisão simples.  
  
 [in] `b`  
 Um inteiro de 64 bits a ser convertido em um valor de ponto flutuante.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `__m128` estrutura cujo primeiro valor de ponto flutuante é o resultado da conversão. Os três valores são copiados inalterado desde `a`.  
  
## <a name="requirements"></a>Requisitos  
  
|Intrínseco|Arquitetura|  
|---------------|------------------|  
|`_mm_cvtsi64x_ss`|X64|  
  
 **Arquivo de cabeçalho** \<intrin.h >  
  
## <a name="remarks"></a>Comentários  
 O `__m128` estrutura representa um registro XMM, portanto nesse intrínseco permite que o valor `b` da memória de sistema a ser movido para um XMM registrar.  
  
 Essa rotina só está disponível como função intrínseca.  
  
## <a name="example"></a>Exemplo  
  
```  
// _mm_cvtsi64x_ss.cpp  
// processor: x64  
  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtsi64x_ss)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    a.m128_f32[0] = 0;  
    a.m128_f32[1] = 0;  
    a.m128_f32[2] = 0;  
    a.m128_f32[3] = 0;  
    a = _mm_cvtsi64x_ss(a, b);  
  
    printf_s( "%lf %lf %lf %lf\n",  
              a.m128_f32[0], a.m128_f32[1],   
              a.m128_f32[2], a.m128_f32[3] );  
}  
```  
  
```Output  
54.000000 0.000000 0.000000 0.000000  
```  
  
**Fim da seção específica da Microsoft**  
  
## <a name="see-also"></a>Consulte também  
 [m128](../cpp/m128.md)   
 [Intrínsecos do compilador](../intrinsics/compiler-intrinsics.md)