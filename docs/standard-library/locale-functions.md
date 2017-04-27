---
title: "Funções &lt;locale&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- locale/std::has_facet
- locale/std::isalnum
- locale/std::isalpha
- locale/std::iscntrl
- locale/std::isdigit
- locale/std::isgraph
- locale/std::islower
- locale/std::isprint
- locale/std::ispunct
- locale/std::isspace
- locale/std::isupper
- locale/std::isxdigit
- locale/std::tolower
- locale/std::toupper
- locale/std::use_facet
ms.assetid: b06c1ceb-33a7-48d3-8d4b-2714bbb27f14
caps.latest.revision: 15
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 5ca6c94270b97f8b6e48871699628415e2133778
ms.lasthandoff: 02/25/2017

---
# <a name="ltlocalegt-functions"></a>Funções &lt;locale&gt;
||||  
|-|-|-|  
|[has_facet](#has_facet)|[isalnum](#isalnum)|[isalpha](#isalpha)|  
|[iscntrl](#iscntrl)|[isdigit](#isdigit)|[isgraph](#isgraph)|  
|[islower](#islower)|[isprint](#isprint)|[ispunct](#ispunct)|  
|[isspace](#isspace)|[isupper](#isupper)|[isxdigit](#isxdigit)|  
|[tolower](#tolower)|[toupper](#toupper)|[use_facet](#use_facet)|  
  
##  <a name="has_facet"></a>  has_facet  
 Testa se uma determinada faceta é armazenada em uma localidade especificada.  
  
```  
template <class Facet>  
bool has_facet(const locale& Loc);
```  
  
### <a name="parameters"></a>Parâmetros  
 `Loc`  
 A localidade a ser testada para a presença de uma faceta.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se a localidade tiver a faceta testada; **false** se não.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo é útil para verificar se as facetas não obrigatórias estão listadas em uma localidade antes de `use_facet` ser chamado para evitar a exceção que seria gerada se elas não estiverem presentes.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_has_facet.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   locale loc ( "German_Germany" );  
   bool result = has_facet <ctype<char> > ( loc );  
   cout << result << endl;  
}  
```  
  
```Output  
1  
```  
  
##  <a name="isalnum"></a>  isalnum  
 Testa se um elemento em uma localidade é um caractere alfabético ou numérico.  
  
```  
template <class CharType>  
bool isalnum(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O elemento alfanumérico a ser testado.  
  
 `Loc`  
 A localidade que contém o elemento alfanumérico a ser testado.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se o elemento testado for alfanumérico; **false** se não.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_isalnum.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = isalnum ( 'L', loc);  
   bool result2 = isalnum ( '@', loc);  
   bool result3 = isalnum ( '3', loc);  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "alphanumeric." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not alphanumeric." << endl;  
  
   if ( result2 )  
      cout << "The character '@' in the locale is "  
           << "alphanumeric." << endl;  
   else  
      cout << "The character '@' in the locale is "  
           << " not alphanumeric." << endl;  
  
   if ( result3 )  
      cout << "The character '3' in the locale is "  
           << "alphanumeric." << endl;  
   else  
      cout << "The character '3' in the locale is "  
           << " not alphanumeric." << endl;  
}  
```  
  
```Output  
The character 'L' in the locale is alphanumeric.  
The character '@' in the locale is  not alphanumeric.  
The character '3' in the locale is alphanumeric.  
```  
  
##  <a name="isalpha"></a>  isalpha  
 Testa se um elemento em uma localidade é um caractere alfabético.  
  
```  
template <class CharType>  
bool isalpha(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O elemento a ser testado.  
  
 `Loc`  
 A localidade que contém o elemento alfabético a ser testado.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se o elemento testado for alfabético; **false** se não.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo retorna [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [é](../standard-library/ctype-class.md#ctype__is) (**ctype**\< **CharType**>:: **alpha**, `Ch`).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_isalpha.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = isalpha ( 'L', loc);  
   bool result2 = isalpha ( '@', loc);  
   bool result3 = isalpha ( '3', loc);  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "alphabetic." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not alphabetic." << endl;  
  
   if ( result2 )  
      cout << "The character '@' in the locale is "  
           << "alphabetic." << endl;  
   else  
      cout << "The character '@' in the locale is "  
           << " not alphabetic." << endl;  
  
   if ( result3 )  
      cout << "The character '3' in the locale is "  
           << "alphabetic." << endl;  
   else  
      cout << "The character '3' in the locale is "  
           << " not alphabetic." << endl;  
}  
```  
  
##  <a name="iscntrl"></a>  iscntrl  
 Testa se um elemento em uma localidade é um caractere de controle.  
  
```  
template <class CharType>  
bool iscntrl(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O elemento a ser testado.  
  
 `Loc`  
 A localidade que contém o elemento a ser testado.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se o elemento testado for um caractere de controle; **false** se não.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo retorna [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [é](../standard-library/ctype-class.md#ctype__is) (**ctype**\< **CharType**>:: **cntrl**, `Ch`).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_iscntrl.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = iscntrl ( 'L', loc );  
   bool result2 = iscntrl ( '\n', loc );  
   bool result3 = iscntrl ( '\t', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a control character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a control character." << endl;  
  
   if ( result2 )  
      cout << "The character-set 'backslash-n' in the locale\n is "  
           << "a control character." << endl;  
   else  
      cout << "The character-set 'backslash-n' in the locale\n is "  
           << " not a control character." << endl;  
  
   if ( result3 )  
      cout << "The character-set 'backslash-t' in the locale\n is "  
           << "a control character." << endl;  
   else  
      cout << "The character-set 'backslash-n' in the locale \n is "  
           << " not a control character." << endl;  
}  
```  
  
##  <a name="isdigit"></a>  isdigit  
 Testa se um elemento em uma localidade é um caractere numérico.  
  
```  
template <class CharType>  
bool isdigit(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O elemento a ser testado.  
  
 `Loc`  
 A localidade que contém o elemento a ser testado.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se o elemento testado for um caractere numérico; **false** se não.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo retorna [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [é](../standard-library/ctype-class.md#ctype__is) (**ctype**\< **CharType**>:: **digit**, `Ch`).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_is_digit.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = isdigit ( 'L', loc );  
   bool result2 = isdigit ( '@', loc );  
   bool result3 = isdigit ( '3', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a numeric character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a numeric character." << endl;  
  
   if ( result2 )  
      cout << "The character '@' in the locale is "  
           << "a numeric character." << endl;  
   else  
      cout << "The character '@' in the locale is "  
           << " not a numeric character." << endl;  
  
   if ( result3 )  
      cout << "The character '3' in the locale is "  
           << "a numeric character." << endl;  
   else  
      cout << "The character '3' in the locale is "  
           << " not a numeric character." << endl;  
}  
```  
  
##  <a name="isgraph"></a>  isgraph  
 Testa se um elemento em uma localidade é um caractere alfanumérico ou de pontuação.  
  
```  
template <class CharType>  
bool isgraph(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O elemento a ser testado.  
  
 `Loc`  
 A localidade que contém o elemento a ser testado.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se o elemento testado for um caractere alfanumérico ou de pontuação; **false** se não.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo retorna [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [é](../standard-library/ctype-class.md#ctype__is) (**ctype**\< **CharType**>:: **graph**, `Ch`).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_is_graph.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   locale loc ( "German_Germany" );  
   bool result1 = isgraph ( 'L', loc );  
   bool result2 = isgraph ( '\t', loc );  
   bool result3 = isgraph ( '.', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is\n "  
           << "an alphanumeric or punctuation character." << endl;  
   else  
      cout << "The character 'L' in the locale is\n "  
           << " not an alphanumeric or punctuation character." << endl;  
  
   if ( result2 )  
      cout << "The character 'backslash-t' in the locale is\n "  
           << "an alphanumeric or punctuation character." << endl;  
   else  
      cout << "The character 'backslash-t' in the locale is\n "  
           << "not an alphanumeric or punctuation character." << endl;  
  
   if ( result3 )  
      cout << "The character '.' in the locale is\n "  
           << "an alphanumeric or punctuation character." << endl;  
   else  
      cout << "The character '.' in the locale is\n "  
           << " not an alphanumeric or punctuation character." << endl;  
}  
```  
  
##  <a name="islower"></a>  islower  
 Testa se um elemento em uma localidade está em letras minúsculas.  
  
```  
template <class CharType>  
bool islower(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O elemento a ser testado.  
  
 `Loc`  
 A localidade que contém o elemento a ser testado.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se o elemento testado for um caractere em minúsculas; **false** se não.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo retorna [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [é](../standard-library/ctype-class.md#ctype__is) (**ctype**\< **CharType**>:: **lower**, `Ch`).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_islower.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = islower ( 'L', loc );  
   bool result2 = islower ( 'n', loc );  
   bool result3 = islower ( '3', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a lowercase character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a lowercase character." << endl;  
  
   if ( result2 )  
      cout << "The character 'n' in the locale is "  
           << "a lowercase character." << endl;  
   else  
      cout << "The character 'n' in the locale is "  
           << " not a lowercase character." << endl;  
  
   if ( result3 )  
      cout << "The character '3' in the locale is "  
           << "a lowercase character." << endl;  
   else  
      cout << "The character '3' in the locale is "  
           << " not a lowercase character." << endl;  
}  
```  
  
##  <a name="isprint"></a>  isprint  
 Testa se um elemento em uma localidade é um caractere imprimível.  
  
```  
template <class CharType>  
bool isprint(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O elemento a ser testado.  
  
 `Loc`  
 A localidade que contém o elemento a ser testado.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se o elemento testado for um imprimível; **false** se não.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo retorna [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [é](../standard-library/ctype-class.md#ctype__is) (**ctype**\< **CharType**>:: **print**, `Ch`).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_isprint.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
  
   bool result1 = isprint ( 'L', loc );  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a printable character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a printable character." << endl;  
  
   bool result2 = isprint( '\t', loc );  
   if ( result2 )  
      cout << "The character 'backslash-t' in the locale is "  
           << "a printable character." << endl;  
   else  
      cout << "The character 'backslash-t' in the locale is "  
           << " not a printable character." << endl;  
  
   bool result3 = isprint( '\n', loc );  
   if ( result3 )  
      cout << "The character 'backslash-n' in the locale is "  
           << "a printable character." << endl;  
   else  
      cout << "The character 'backslash-n' in the locale is "  
           << " not a printable character." << endl;  
}  
```  
  
##  <a name="ispunct"></a>  ispunct  
 Testa se um elemento em uma localidade é um caractere de pontuação.  
  
```  
template <class CharType>  
bool ispunct(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O elemento a ser testado.  
  
 `Loc`  
 A localidade que contém o elemento a ser testado.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se o elemento testado for um caractere de pontuação; **false** se não.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo retorna [use_facet](../standard-library/locale-functions.md#use_facet)`<`[ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [é](../standard-library/ctype-class.md#ctype__is) (**ctype**\< **CharType**>:: **punct**, `Ch`).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_ispunct.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = ispunct ( 'L', loc );  
   bool result2 = ispunct ( ';', loc );  
   bool result3 = ispunct ( '*', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a punctuation character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a punctuation character." << endl;  
  
   if ( result2 )  
      cout << "The character ';' in the locale is "  
           << "a punctuation character." << endl;  
   else  
      cout << "The character ';' in the locale is "  
           << " not a punctuation character." << endl;  
  
   if ( result3 )  
      cout << "The character '*' in the locale is "  
           << "a punctuation character." << endl;  
   else  
      cout << "The character '*' in the locale is "  
           << " not a punctuation character." << endl;  
}  
```  
  
##  <a name="isspace"></a>  isspace  
 Testa se um elemento em uma localidade é um caractere de espaço em branco.  
  
```  
template <class CharType>  
bool isspace(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O elemento a ser testado.  
  
 `Loc`  
 A localidade que contém o elemento a ser testado.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se o elemento testado for um caractere de espaço em branco; **false** se não.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo retorna [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [é](../standard-library/ctype-class.md#ctype__is) (**ctype**\< **CharType**>:: **space**, `Ch`).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_isspace.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = isspace ( 'L', loc );  
   bool result2 = isspace ( '\n', loc );  
   bool result3 = isspace ( ' ', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a whitespace character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a whitespace character." << endl;  
  
   if ( result2 )  
      cout << "The character 'backslash-n' in the locale is "  
           << "a whitespace character." << endl;  
   else  
      cout << "The character 'backslash-n' in the locale is "  
           << " not a whitespace character." << endl;  
  
   if ( result3 )  
      cout << "The character ' ' in the locale is "  
           << "a whitespace character." << endl;  
   else  
      cout << "The character ' ' in the locale is "  
           << " not a whitespace character." << endl;  
}  
```  
  
##  <a name="isupper"></a>  isupper  
 Testa se um elemento em uma localidade está em letras maiúsculas.  
  
```  
template <class CharType>  
bool isupper(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O elemento a ser testado.  
  
 `Loc`  
 A localidade que contém o elemento a ser testado.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se o elemento testado for um caractere em maiúsculas; **false** se não.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo retorna [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [é](../standard-library/ctype-class.md#ctype__is) (**ctype**\< **CharType**>:: **upper**, `Ch`).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_isupper.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = isupper ( 'L', loc );  
   bool result2 = isupper ( 'n', loc );  
   bool result3 = isupper ( '3', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a uppercase character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a uppercase character." << endl;  
  
   if ( result2 )  
      cout << "The character 'n' in the locale is "  
           << "a uppercase character." << endl;  
   else  
      cout << "The character 'n' in the locale is "  
           << " not a uppercase character." << endl;  
  
   if ( result3 )  
      cout << "The character '3' in the locale is "  
           << "a uppercase character." << endl;  
   else  
      cout << "The character '3' in the locale is "  
           << " not a uppercase character." << endl;  
}  
```  
  
##  <a name="isxdigit"></a>  isxdigit  
 Testa se um elemento em uma localidade é um caractere usado para representar um número hexadecimal.  
  
```  
template <class CharType>  
bool isxdigit(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O elemento a ser testado.  
  
 `Loc`  
 A localidade que contém o elemento a ser testado.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se o elemento testado for um caractere usado para representar um número hexadecimal; **false** se não.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo retorna [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [é](../standard-library/ctype-class.md#ctype__is) (**ctype**\< **CharType**>:: **xdigit**, `Ch`).  
  
 Dígitos hexadecimais usam base 16 para representar números, usando os números de 0 a 9 e letras de A a F, sem diferenciar maiúsculas e minúsculas, para representar os números decimais de 0 a 15.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_isxdigit.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = isxdigit ( '5', loc );  
   bool result2 = isxdigit ( 'd', loc );  
   bool result3 = isxdigit ( 'q', loc );  
  
   if ( result1 )  
      cout << "The character '5' in the locale is "  
           << "a hexidecimal digit-character." << endl;  
   else  
      cout << "The character '5' in the locale is "  
           << " not a hexidecimal digit-character." << endl;  
  
   if ( result2 )  
      cout << "The character 'd' in the locale is "  
           << "a hexidecimal digit-character." << endl;  
   else  
      cout << "The character 'd' in the locale is "  
           << " not a hexidecimal digit-character." << endl;  
  
   if ( result3 )  
      cout << "The character 'q' in the locale is "  
           << "a hexidecimal digit-character." << endl;  
   else  
      cout << "The character 'q' in the locale is "  
           << " not a hexidecimal digit-character." << endl;  
}  
```  
  
##  <a name="tolower"></a>  tolower  
 Converte um caractere em letra minúscula.  
  
```  
template <class CharType>  
CharType tolower(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O caractere a ser convertido em letras minúsculas.  
  
 `Loc`  
 A localidade que contém o caractere a ser convertido.  
  
### <a name="return-value"></a>Valor de retorno  
 O caractere convertido em letras minúsculas.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo retorna [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [tolower](../standard-library/ctype-class.md#ctype__tolower)( `Ch`).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_tolower.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   char result1 = tolower ( 'H', loc );  
   cout << "The lower case of 'H' in the locale is: "  
        << result1 << "." << endl;  
   char result2 = tolower ( 'h', loc );  
   cout << "The lower case of 'h' in the locale is: "  
        << result2 << "." << endl;  
   char result3 = tolower ( '$', loc );  
   cout << "The lower case of '$' in the locale is: "  
        << result3 << "." << endl;  
}  
```  
  
##  <a name="toupper"></a>  toupper  
 Converte um caractere em letra maiúscula.  
  
```  
template <class CharType>  
CharType toupper(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `Ch`  
 O caractere a ser convertido em maiúsculas.  
  
 `Loc`  
 A localidade que contém o caractere a ser convertido.  
  
### <a name="return-value"></a>Valor de retorno  
 O caractere convertido em maiúsculas.  
  
### <a name="remarks"></a>Comentários  
 A função de modelo retorna [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [toupper](../standard-library/ctype-class.md#ctype__toupper)( `Ch`).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_toupper.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   char result1 = toupper ( 'h', loc );  
   cout << "The upper case of 'h' in the locale is: "  
        << result1 << "." << endl;  
   char result2 = toupper ( 'H', loc );  
   cout << "The upper case of 'H' in the locale is: "  
        << result2 << "." << endl;  
   char result3 = toupper ( '$', loc );  
   cout << "The upper case of '$' in the locale is: "  
        << result3 << "." << endl;  
}  
```  
  
##  <a name="use_facet"></a>  use_facet  
 Retorna uma referência para uma faceta de um tipo especificado armazenada em uma localidade.  
  
```  
template <class Facet>  
const Facet& use_facet(const locale& Loc);
```  
  
### <a name="parameters"></a>Parâmetros  
 `Loc`  
 A localidade const que contém o tipo de faceta que está sendo referenciado.  
  
### <a name="return-value"></a>Valor de retorno  
 Uma referência à faceta da classe `Facet` contida na localidade do argumento.  
  
### <a name="remarks"></a>Comentários  
 A referência à faceta retornada pela função de modelo permanece válida, desde que exista qualquer cópia da localidade que a contém. Se nenhum objeto de faceta da classe `Facet` estiver listado na localidade do argumento, a função gerará uma exceção `bad_cast`.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// locale_use_facet.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );  
   bool result1 = use_facet<ctype<char> > ( loc1 ).is(  
   ctype_base::alpha, 'a'   
);  
   bool result2 = use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!'  
   );  
  
   if ( result1 )  
      cout << "The character 'a' in locale loc1 is alphabetic."   
           << endl;  
   else  
      cout << "The character 'a' in locale loc1 is not alphabetic."   
           << endl;  
  
   if ( result2 )  
      cout << "The character '!' in locale loc2 is alphabetic."   
           << endl;  
   else  
      cout << "The character '!' in locale loc2 is not alphabetic."   
           << endl;  
}  
```  
  
```Output  
The character 'a' in locale loc1 is alphabetic.  
The character '!' in locale loc2 is not alphabetic.  
```  
  
## <a name="see-also"></a>Consulte também  
 [\<locale>](../standard-library/locale.md)

