---
title: '&lt;string&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::<string>
- string/std::<string>
- std.<string>
- <string>
dev_langs:
- C++
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
caps.latest.revision: 23
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: f352a9efb06dc0267abcf1d4174c48dcbaae78a2
ms.lasthandoff: 02/25/2017

---
# <a name="ltstringgt"></a>&lt;string&gt;
Define a classe de modelo do contêiner `basic_string` e diversos modelos de suporte.  
  
 Para obter mais informações sobre `basic_string`, consulte [basic_string Class](../standard-library/basic-string-class.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
#include <string>  
```  
  
## <a name="remarks"></a>Comentários  
 A linguagem C++ e a biblioteca C++ padrão dão suporte a dois tipos de cadeias de caracteres:  
  
-   Matrizes de caracteres com terminação nula geralmente conhecidas como cadeias de caracteres C.  
  
-   Objetos de classe de modelo, do tipo `basic_string`, que lidam com todos os argumentos de modelo do tipo `char`.  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[string](../standard-library/string-typedefs.md#string)|Um tipo que descreve uma especialização da classe modelo `basic_string` com elementos do tipo `char` como uma `string`.|  
|[wstring](../standard-library/string-typedefs.md#wstring)|Um tipo que descreve uma especialização da classe modelo `basic_string` com elementos do tipo `wchar_t` como uma `wstring`.|  
|[u16string](../standard-library/string-typedefs.md#u16string)|Um tipo que descreve uma especialização da classe modelo `basic_string` com base em elementos do tipo `char16_t`.|  
|[u32string](../standard-library/string-typedefs.md#u32string)|Um tipo que descreve uma especialização da classe modelo `basic_string` com base em elementos do tipo `char32_t`.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator+](../standard-library/string-operators.md#operator_add)|Concatena dois objetos de cadeia de caracteres.|  
|[operator!=](../standard-library/string-operators.md#operator_neq)|Testa se o objeto da cadeia de caracteres à esquerda do operador é diferente do objeto da cadeia de caracteres à direita.|  
|[operator==](../standard-library/string-operators.md#operator_eq_eq)|Testa se o objeto da cadeia de caracteres à esquerda do operador é igual ao objeto da cadeia de caracteres à direita.|  
|[operator<](../standard-library/string-operators.md#operator_lt_)|Testa se o objeto da cadeia de caracteres à esquerda do operador é menor que o objeto da cadeia de caracteres à direita.|  
|[operator<=](../standard-library/string-operators.md#operator_lt__eq)|Testa se o objeto da cadeia de caracteres à esquerda do operador é menor que ou igual ao objeto da cadeia de caracteres à direita.|  
|[operator<\<](../standard-library/string-operators.md#operator_lt__lt_)|Uma função de modelo que insere uma cadeia de caracteres no fluxo de saída.|  
|[operator>](../standard-library/string-operators.md#operator_gt_)|Testa se o objeto da cadeia de caracteres à esquerda do operador é maior que o objeto da cadeia de caracteres à direita.|  
|[operator>=](../standard-library/string-operators.md#operator_gt__eq)|Testa se o objeto da cadeia de caracteres à esquerda do operador é maior que ou igual ao objeto da cadeia de caracteres à direita.|  
|[operator>>](../standard-library/string-operators.md#operator_gt__gt_)|Uma função de modelo que extrai uma cadeia de caracteres do fluxo de entrada.|  
  
### <a name="specialized-template-functions"></a>Funções de Modelo Especializadas  
  
|||  
|-|-|  
|[swap](../standard-library/string-functions.md#swap)|Troca as matrizes de caracteres de duas cadeias de caracteres.|  
|[stod](../standard-library/string-functions.md#stod)|Converte uma sequência de caracteres em um `double.`|  
|[stof](../standard-library/string-functions.md#stof)|Converte uma sequência de caracteres em um `float`.|  
|[stoi](../standard-library/string-functions.md#stoi)|Converte uma sequência de caracteres em um número inteiro.|  
|[stold](../standard-library/string-functions.md#stold)|Converte uma sequência de caracteres em um `long double`.|  
|[stoll](../standard-library/string-functions.md#stoll)|Converte uma sequência de caracteres em um `long long`.|  
|[stoul](../standard-library/string-functions.md#stoul)|Converte uma sequência de caracteres em um `unsigned long`.|  
|[stoull](../standard-library/string-functions.md#stoull)|Converte uma sequência de caracteres em um `unsigned long long`.|  
|[to_string](../standard-library/string-functions.md#to_string)|Converte um valor em uma `string`.|  
|[to_wstring](../standard-library/string-functions.md#to_wstring)|Converte um valor em uma `string` larga.|  
  
### <a name="functions"></a>Funções  
  
|||  
|-|-|  
|[getline Função de Modelo](../standard-library/string-functions.md#getline)|Extrai cadeias de caracteres do fluxo de entrada linha por linha.|  
  
### <a name="classes"></a>Classes  
  
|||  
|-|-|  
|[Classe basic_string](../standard-library/basic-string-class.md)|Uma classe de modelo que descreve os objetos que pode armazenar uma sequência de objetos arbitrários do tipo caractere.|  
|[Struct char_traits](../standard-library/char-traits-struct.md)|Uma classe de modelo que descreve os atributos associados a um caractere do tipo CharType|  
  
### <a name="specializations"></a>Especializações  
  
|||  
|-|-|  
|[char_traits\<char> Struct](../standard-library/char-traits-char-struct.md)|Um struct é uma especialização de struct modelo `char_traits`\<CharType> para um elemento do tipo `char`.|  
|[Struct char_traits<wchar_t>](../standard-library/char-traits-wchar-t-struct.md)|Um struct é uma especialização de struct modelo `char_traits`\<CharType> para um elemento do tipo `wchar_t`.|  
|[Struct char_traits<char16_t>](../standard-library/char-traits-char16-t-struct.md)|Um struct é uma especialização de struct modelo `char_traits`\<CharType> para um elemento do tipo `char16_t`.|  
|[Struct char_traits<char32_t>](../standard-library/char-traits-char32-t-struct.md)|Um struct é uma especialização de struct modelo `char_traits`\<CharType> para um elemento do tipo `char32_t`.|  
  
## <a name="requirements"></a>Requisitos  
  
- **Cabeçalho:** \<string>  
  
- **Namespace:** std  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Arquivos de Cabeçalho](../standard-library/cpp-standard-library-header-files.md)   
 [Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



