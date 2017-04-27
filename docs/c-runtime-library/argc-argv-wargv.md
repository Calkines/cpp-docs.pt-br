---
title: __argc, __argv, __wargv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __wargv
- __argv
- __argc
apilocation:
- msvcrt120.dll
apitype: DLLExport
f1_keywords:
- __argv
- __argc
- __wargv
dev_langs:
- C++
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
caps.latest.revision: 5
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
translationtype: Human Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 93e19bdcae0f10ec48c3a1d9bc875f3208229853
ms.lasthandoff: 02/25/2017

---
# <a name="argc-argv-wargv"></a>__argc, __argv, __wargv
A variável global `__argc` é uma contagem do número de argumentos de linha de comando passados para o programa. `__argv` é um ponteiro para uma matriz de cadeias de caracteres de caractere de byte único ou de caractere multibyte que contêm os argumentos do programa; `__wargv` é um ponteiro para uma matriz de cadeias de caracteres de caractere largo que contêm os argumentos do programa. Essas variáveis globais fornecem os argumentos para `main` ou `wmain`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
extern int __argc;  
extern char ** __argv;  
extern wchar_t ** __wargv;  
```  
  
## <a name="remarks"></a>Comentários  
 Em um programa que usa a função `main`, `__argc` e `__argv` são inicializados na inicialização do programa com a linha de comando usada para iniciar o programa. A linha de comando é analisada em argumentos individuais, e os curingas são expandidos. A contagem de argumentos é atribuída ao `__argc` e as cadeias de caracteres de argumento são alocadas no heap, e um ponteiro para a matriz de argumentos é atribuído ao `__argv`. Em um programa compilado para usar caracteres largos e uma função `wmain`, os argumentos são analisados e os curingas são expandidos como cadeias de caracteres de caractere largo, e um ponteiro para a matriz de cadeias de caracteres de argumento é atribuído ao `__wargv`.  
  
 No caso do código portátil, recomendamos usar os argumentos passados para `main` a fim de obter os argumentos de linha de comando no programa.  
  
### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico  
  
|Rotina Tchar.h|_UNICODE não definido|_UNICODE definido|  
|---------------------|---------------------------|-----------------------|  
|`__targv`|`__argv`|`__wargv`|  
  
## <a name="requirements"></a>Requisitos  
  
|Variável global|Cabeçalho necessário|  
|---------------------|---------------------|  
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>, \<cstdlib> (C++)|  
  
 `__argc`, `__argv` e `__wargv` são extensões da Microsoft. Para obter informações sobre compatibilidade, consulte [Compatibilidade](../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Consulte também  
 [Variáveis globais](../c-runtime-library/global-variables.md)   
 [main: inicialização do programa](../cpp/main-program-startup.md)   
 [Usando wmain em vez main](../cpp/using-wmain-instead-of-main.md)