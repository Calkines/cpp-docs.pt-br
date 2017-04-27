---
title: "Usando mapeamentos de texto genérico | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _UNICODE
dev_langs:
- C++
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- _UNICODE constant
- TXCHAR type
- generic-text mappings
- _TSCHAR type
- T type
- mappings, generic-text
- _TUCHAR type
- MBCS data type
- _MBCS data type
- _TEXT type
- UNICODE constant
- _T type
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
caps.latest.revision: 8
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 5520dd95196cfbcac9eb84659aa444b8fad55c36
ms.lasthandoff: 02/25/2017

---
# <a name="using-generic-text-mappings"></a>Usando mapeamentos de texto genérico
**Seção específica da Microsoft**  
  
 Para simplificar o desenvolvimento de código para vários mercados internacionais, a biblioteca de tempo de execução da Microsoft fornece mapeamentos de "texto genérico" específico da Microsoft para vários tipos de dados, rotinas e outros objetos. Esses mapeamentos são definidos em TCHAR. H. Você pode usar esses mapeamentos de nome para escrever código genérico que pode ser compilado para qualquer um dos três tipos de conjuntos de caracteres: ASCII (SBCS), MBCS ou Unicode, dependendo de uma constante de manifesto que você define usando uma instrução `#define`. Mapeamentos de texto genérico são extensões da Microsoft não compatíveis com ANSI.  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>Diretivas de pré-processador para mapeamentos de texto genérico  
  
|#define|Versão compilada|Exemplo|  
|--------------|----------------------|-------------|  
|`_UNICODE`|Unicode (caracteres largos)|`_tcsrev` mapeia para `_wcsrev`|  
|`_MBCS`|Caracteres multibyte|`_tcsrev` mapeia para `_mbsrev`|  
|Nenhum (padrão: não há definição de `_UNICODE` ou `_MBCS`)|SBCS (ASCII)|`_tcsrev` mapeia para `strrev`|  
  
 Por exemplo, a função de texto genérico `_tcsrev`, definida em TCHAR.H, é mapeada para `mbsrev`, caso `MBCS` tenha sido definida em seu programa, ou para `_wcsrev`, caso `_UNICODE` tenha sido definida. Caso contrário, `_tcsrev` é mapeada para `strrev`.  
  
 O tipo de dados de texto genérico `_TCHAR`, também definido em TCHAR. H, é mapeado para o tipo `char`, se `_MBCS` estiver definida, para o tipo `wchar_t`, se `_UNICODE` estiver definida, e para o tipo `char`, se nenhuma constante estiver definida. Outros mapeamentos de tipo de dados são fornecidos em TCHAR. H para conveniência de programação, mas o tipo `_TCHAR` é o mais útil.  
  
### <a name="generic-text-data-type-mappings"></a>Mapeamentos de tipo de dados de texto genérico  
  
|Nome do tipo de dados de texto genérico|SBCS (_UNICODE, _MBCS não definidos)|_MBCS definido|_UNICODE definido|  
|----------------------------------|--------------------------------------------|--------------------|-----------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` ou `_TEXT`|Nenhum efeito (removido pelo pré-processador)|Nenhum efeito (removido pelo pré-processador)|`L` (converte o próximo caractere ou a próxima cadeia de caracteres no equivalente em Unicode)|  
  
 Para obter uma lista completa de mapeamentos de texto genérico de rotinas, variáveis e outros objetos, consulte [Mapeamentos de texto genérico](../c-runtime-library/generic-text-mappings.md).  
  
 Os fragmentos de código a seguir ilustram o uso de `_TCHAR` e `_tcsrev` para mapear os modelos MBCS, Unicode e SBCS.  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 Se `MBCS` tiver sido definido, o pré-processador mapeia o fragmento anterior para o código a seguir:  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 Se `_UNICODE` tiver sido definido, o pré-processador mapeia o mesmo fragmento para o código a seguir:  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 Se `_MBCS` ou `_UNICODE` não tiver sido definido, o pré-processador mapeará o fragmento para o código ASCII de byte único, da seguinte maneira:  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 Portanto, você pode escrever, manter e compilar um arquivo de código fonte único para execução com rotinas que sejam específicas para qualquer um dos três tipos de conjuntos de caracteres.  
  
 **Fim da seção específica da Microsoft**  
  
## <a name="see-also"></a>Consulte também  
 [Mapeamentos de texto genérico](../c-runtime-library/generic-text-mappings.md)   
 [Mapeamentos de tipo de dados](../c-runtime-library/data-type-mappings.md)   
 [Mapeamentos de constante e variável global](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [Mapeamentos de rotina](../c-runtime-library/routine-mappings.md)   
 [Um programa de texto genérico de amostra](../c-runtime-library/a-sample-generic-text-program.md)