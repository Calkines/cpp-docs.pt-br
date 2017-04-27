---
title: _aligned_realloc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_realloc
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _aligned_realloc
- aligned_realloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_realloc function
- _aligned_realloc function
ms.assetid: 80ce96e8-6087-416f-88aa-4dbb8cb1d218
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: b385fd07e76aad108765c83c1404e28ac0c9138e
ms.lasthandoff: 02/25/2017

---
# <a name="alignedrealloc"></a>_aligned_realloc
Altera o tamanho de um bloco de memória que foi alocado com [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) ou [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
void * _aligned_realloc(  
   void *memblock,   
   size_t size,   
   size_t alignment  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 [in] `memblock`  
 O ponteiro do bloco de memória atual.  
  
 [in] `size`  
 Tamanho da alocação de memória solicitada.  
  
 [in] `alignment`  
 O valor de alinhamento, que deve ser um inteiro elevado à segunda potência.  
  
## <a name="return-value"></a>Valor de retorno  
 `_aligned_realloc` retorna um ponteiro nulo para o bloco de memória realocado (e possivelmente migrado). O valor retornado é `NULL` se o tamanho for zero e o argumento do buffer não for `NULL`, ou se não houver memória suficiente para expandir o bloco para o tamanho determinado. No primeiro caso, o bloco original é liberado. No segundo caso, ele permanece inalterado. O valor retornado indica um espaço de armazenamento que sempre está sutilmente alinhado para armazenamento de qualquer tipo de objeto. Para obter um ponteiro para um tipo que não seja nulo, digite a conversão no valor retornado.  
  
 Realocar a memória e alterar o alinhamento de um bloco é um erro.  
  
## <a name="remarks"></a>Comentários  
 `_aligned_realloc` baseia-se em `malloc`. Para obter mais informações sobre como usar `_aligned_offset_malloc`, consulte [malloc](../../c-runtime-library/reference/malloc.md).  
  
 Essa função define `errno` como `ENOMEM` se a alocação da memória tiver falhado ou se o tamanho solicitado for maior que `_HEAP_MAXREQ`. Para obter mais informações sobre `errno`, consulte [errno, _doserrno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Além disso, `_aligned_realloc` valida seus parâmetros. Se `alignment` não for um número elevado à segunda potência, essa função invocará o manipulador de parâmetro inválido, conforme a descrição em [Validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, essa função retornará `NULL` e definirá `errno` como `EINVAL`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rotina|Cabeçalho necessário|  
|-------------|---------------------|  
|`_aligned_realloc`|\<malloc.h>|  
  
## <a name="example"></a>Exemplo  
 Para obter mais informações, consulte [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md).  
  
## <a name="see-also"></a>Consulte também  
 [Alinhamento de dados](../../c-runtime-library/data-alignment.md)