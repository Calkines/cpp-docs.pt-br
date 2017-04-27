---
title: _lsearch_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _lsearch_s
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _lsearch_s
- lsearch_s
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 6f89899e5fe2c00cf17a7a18c9de2eac2ba8462f
ms.lasthandoff: 02/25/2017

---
# <a name="lsearchs"></a>_lsearch_s
Executa uma pesquisa linear para um valor. Uma versão de [_lsearch](../../c-runtime-library/reference/lsearch.md) com melhorias de segurança, conforme descrito em [Recursos de Segurança no CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
void *_lsearch_s(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `key`  
 O objeto a ser pesquisado.  
  
 `base`  
 Ponteiro para a base da matriz a ser pesquisada.  
  
 `num`  
 Número de elementos.  
  
 `size`  
 Tamanho de cada elemento da matriz em bytes.  
  
 `compare`  
 Ponteiro para a rotina de comparação. O segundo parâmetro é um ponteiro para a chave de pesquisa. O terceiro parâmetro é um ponteiro para um elemento de matriz a ser comparado com a chave.  
  
 `context`  
 Um ponteiro para um objeto que pode ser acessado na função de comparação.  
  
## <a name="return-value"></a>Valor de retorno  
 Se `key` for encontrado, `_lsearch_s` retornará um ponteiro para o elemento da matriz em `base` que corresponde a `key`. Se `key` não for encontrado, `_lsearch_s` retornará um ponteiro para o novo item adicionado ao final da matriz.  
  
 Se parâmetros inválidos forem passados para a função, o manipulador de parâmetro inválido será invocado, conforme descrito em [Validação de Parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução tiver permissão para continuar, `errno` será definido como `EINVAL` e a função retornará `NULL`. Para obter mais informações, consulte [errno, _doserrno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### <a name="error-conditions"></a>Condições de Erro  
  
|`key`|`base`|`compare`|`num`|`size`|`errno`|  
|-----------|------------|---------------|-----------|------------|-------------|  
|`NULL`|qualquer|qualquer|qualquer|qualquer|`EINVAL`|  
|qualquer|`NULL`|qualquer|!= 0|qualquer|`EINVAL`|  
|qualquer|qualquer|qualquer|qualquer|zero|`EINVAL`|  
|qualquer|qualquer|`NULL`|an|qualquer|`EINVAL`|  
  
## <a name="remarks"></a>Comentários  
 A função `_lsearch_s` executa uma pesquisa linear para o valor `key` em uma matriz de `num` elementos, cada uma de `width` bytes. Ao contrário de `bsearch_s`, `_lsearch_s` não exige que a matriz seja classificada. Se `key` não for encontrado, `_lsearch_s` o adicionará ao final da matriz e incrementará `num`.  
  
 A função `compare` é um ponteiro para uma rotina fornecida pelo usuário que compara dois elementos de matriz e retorna um valor que especifica seu relacionamento. A função `compare` também usa o ponteiro para o contexto como o primeiro argumento. `_lsearch_s` chama `compare` uma ou mais vezes durante a pesquisa, passando ponteiros para dois elementos de matriz em cada chamada. `compare` deve comparar os elementos e retornar um valor diferente de zero (ou seja, os elementos são diferentes) ou 0 (isto é, os elementos são idênticos).  
  
 O ponteiro `context` poderá ser útil se a estrutura de dados pesquisada for parte de um objeto e a função `compare` precisar acessar membros do objeto. Por exemplo, o código na função `compare` pode converter o ponteiro void para o tipo de objeto apropriado e acessar membros de tal objeto. A adição do ponteiro `context` torna `_lsearch_s` mais seguro, pois o contexto adicional pode ser usado para evitar bugs de reentrância associados ao uso de variáveis estáticas para disponibilizar dados para a função `compare`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rotina|Cabeçalho necessário|  
|-------------|---------------------|  
|`_lsearch_s`|\<search.h>|  
  
 Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md) na Introdução.  
  
## <a name="net-framework-equivalent"></a>Equivalente ao .NET Framework  
 Não aplicável. Para chamar a função C padrão, use `PInvoke`. Para obter mais informações, consulte [Exemplos de invocação de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Consulte também  
 [Pesquisando e classificando](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch_s](../../c-runtime-library/reference/bsearch-s.md)   
 [_lfind_s](../../c-runtime-library/reference/lfind-s.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)