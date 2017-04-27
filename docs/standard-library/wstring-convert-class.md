---
title: Classe wstring_convert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- wstring_convert
- stdext::cvt::wstring_convert
- cvt::wstring_convert
- wstring/stdext::cvt::wstring_convert
- locale/std::wstring_convert::byte_string
- locale/std::wstring_convert::wide_string
- locale/std::wstring_convert::state_type
- locale/std::wstring_convert::int_type
- locale/std::wstring_convert::from_bytes
- locale/std::wstring_convert::to_bytes
- locale/std::wstring_convert::converted
- locale/std::wstring_convert::state
dev_langs:
- C++
helpviewer_keywords:
- wstring_convert class
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: bbe0589b9f0b02a738e8367002986c1669935605
ms.lasthandoff: 02/25/2017

---
# <a name="wstringconvert-class"></a>Classe wstring_convert
A classe de modelo `wstring_convert` executa conversões entre uma cadeia de caracteres largos e uma cadeia de caracteres de bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```  
  
#### <a name="parameters"></a>Parâmetros  
 Codecvt  
 A faceta de [locale](../standard-library/locale-class.md) que representa o objeto de conversão.  
  
 Elem  
 O tipo de elemento de caractere largo.  
  
## <a name="remarks"></a>Comentários  
 A classe de modelo descreve um objeto que controla conversões entre objetos de cadeia de caracteres largos da classe `std::basic_string<Elem>` e objetos de cadeia de caracteres de bytes da classe `std::basic_string<char>` (também conhecida como `std::string`). A classe de modelo define os tipos `wide_string` e `byte_string` como sinônimos desses dois tipos. A conversão entre uma sequência de valores `Elem` (armazenada em um objeto `wide_string`) e as sequências multibyte (armazenadas em um objeto `byte_string`) é executada por um objeto da classe `Codecvt<Elem, char, std::mbstate_t>`, que atende aos requisitos da faceta de conversão de código padrão `std::codecvt<Elem, char, std::mbstate_t>`.  
  
 Um objeto desta classe de modelo armazena:  
  
-   Uma cadeia de caracteres de bytes para ser exibida em caso de erros  
  
-   Uma cadeia de caracteres largos para ser exibida em caso de erros  
  
-   Um ponteiro para o objeto de conversão alocado (que é liberado quando o objeto wbuffer_convert é destruído)  
  
-   Um objeto do estado da conversão do tipo [state_type](#wstring_convert__state_type)  
  
-   Uma contagem de conversões  
  
### <a name="constructors"></a>Construtores  
  
|||  
|-|-|  
|[wstring_convert](#wstring_convert__wstring_convert)|Constrói um objeto do tipo `wstring_convert`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[byte_string](#wstring_convert__byte_string)|Um tipo que representa uma cadeia de caracteres de bytes.|  
|[wide_string](#wstring_convert__wide_string)|Um tipo que representa uma cadeia de caracteres largos.|  
|[state_type](#wstring_convert__state_type)|Um tipo que representa o estado da conversão.|  
|[int_type](#wstring_convert__int_type)|Um tipo que representa um número inteiro.|  
  
### <a name="member-functions"></a>Funções membro  
  
|||  
|-|-|  
|[from_bytes](#wstring_convert__from_bytes)|Converte uma cadeia de caracteres de bytes em uma cadeia de caracteres largos.|  
|[to_bytes](#wstring_convert__to_bytes)|Converte uma cadeia de caracteres largos em uma cadeia de caracteres de bytes.|  
|[converted](#wstring_convert__converted)|Retorna o número de conversões bem-sucedidas.|  
|[state](#wstring_convert__state)|Retorna um objeto que representa o estado da conversão.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<locale>  
  
 **Namespace:** std  
  
##  <a name="wstring_convert__byte_string"></a> wstring_convert::byte_string  
 Um tipo que representa uma cadeia de caracteres de bytes.  
  
```
typedef std::basic_string<char> byte_string;
```  
  
### <a name="remarks"></a>Comentários  
 O tipo é um sinônimo de `std::basic_string<char>`.  
  
##  <a name="wstring_convert__converted"></a> wstring_convert::converted  
 Retorna o número de conversões bem-sucedidas.  
  
```
size_t converted() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O número de conversões bem-sucedidas.  
  
### <a name="remarks"></a>Comentários  
 O número de conversões bem-sucedidas é armazenado no objeto de contagem de conversões.  
  
##  <a name="wstring_convert__from_bytes"></a> wstring_convert::from_bytes  
 Converte uma cadeia de caracteres de bytes em uma cadeia de caracteres largos.  
  
```
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Byte`|A sequência de bytes de elemento único a ser convertida.|  
|`ptr`|A sequência de caracteres terminada em nulo de estilo C a ser convertida.|  
|`Bstr`|A [byte_string](#wstring_convert__byte_string) a ser convertida.|  
|`first`|O primeiro caractere em um intervalo de caracteres a ser convertido.|  
|`last`|O último caractere em um intervalo de caracteres a ser convertido.|  
  
### <a name="return-value"></a>Valor de retorno  
 Um objeto de cadeia de caracteres largos resultante da conversão.  
  
### <a name="remarks"></a>Comentários  
 Se o objeto do [estado da conversão](../standard-library/wstring-convert-class.md) for `not` construído com um valor explícito, ele será definido como seu valor padrão (o estado inicial da conversão) antes do início da conversão. Caso contrário, ele permanecerá inalterado.  
  
 O número de elementos de entrada convertidos com êxito é armazenado no objeto de contagem de conversões. Se não houver erro de conversão, a função membro retornará a cadeia de caracteres largos convertida. Caso contrário, se o objeto for construído com um inicializador para a mensagem de erro de cadeia de caracteres largos, a função membro retornará o objeto da mensagem de erro de cadeia de caracteres largos. Caso contrário, a função membro gerará um objeto da classe [range_error](../standard-library/range-error-class.md).  
  
##  <a name="wstring_convert__int_type"></a> wstring_convert::int_type  
 Um tipo que representa um número inteiro.  
  
```
typedef typename wide_string::traits_type::int_type int_type;
```  
  
### <a name="remarks"></a>Comentários  
 O tipo é um sinônimo de `wide_string::traits_type::int_type`.  
  
##  <a name="wstring_convert__state"></a> wstring_convert::state  
 Retorna um objeto que representa o estado da conversão.  
  
```
state_type state() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O objeto do [estado da conversão](../standard-library/wstring-convert-class.md) que representa o estado da conversão.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="wstring_convert__state_type"></a> wstring_convert::state_type  
 Um tipo que representa o estado da conversão.  
  
```
typedef typename Codecvt::state_type state_type;
```  
  
### <a name="remarks"></a>Comentários  
 O tipo descreve um objeto que pode representar o estado da conversão. O tipo é um sinônimo de `Codecvt::state_type`.  
  
##  <a name="wstring_convert__to_bytes"></a> wstring_convert::to_bytes  
 Converte uma cadeia de caracteres largos em uma cadeia de caracteres de bytes.  
  
```
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Char`|O caractere largo a ser convertido.|  
|`Wptr`|A sequência de caracteres terminada em nulo de estilo C, começando em `wptr`, a ser convertida.|  
|`Wstr`|A [wide_string](#wstring_convert__wide_string) a ser convertida.|  
|`first`|O primeiro elemento em um intervalo de elementos a ser convertido.|  
|`last`|O último elemento em um intervalo de elementos a ser convertido.|  
  
### <a name="remarks"></a>Comentários  
 Se o objeto do [estado da conversão](../standard-library/wstring-convert-class.md) for `not` construído com um valor explícito, ele será definido como seu valor padrão (o estado inicial da conversão) antes do início da conversão. Caso contrário, ele permanecerá inalterado.  
  
 O número de elementos de entrada convertidos com êxito é armazenado no objeto de contagem de conversões. Se não houver erro de conversão, a função membro retornará a cadeia de caracteres de bytes convertida. Caso contrário, se o objeto for construído com um inicializador para a mensagem de erro de cadeia de caracteres de bytes, a função membro retornará o objeto da mensagem de erro de cadeia de caracteres de bytes. Caso contrário, a função membro gerará um objeto da classe [range_error](../standard-library/range-error-class.md).  
  
##  <a name="wstring_convert__wide_string"></a> wstring_convert::wide_string  
 Um tipo que representa uma cadeia de caracteres largos.  
  
```
typedef std::basic_string<Elem> wide_string;
```  
  
### <a name="remarks"></a>Comentários  
 O tipo é um sinônimo de `std::basic_string<Elem>`.  
  
##  <a name="wstring_convert__wstring_convert"></a> wstring_convert::wstring_convert  
 Constrói um objeto do tipo `wstring_convert`.  
  
```
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`*Pcvt`|O objeto do tipo `Codecvt` para executar a conversão.|  
|`_State`|O objeto do tipo [state_type](#wstring_convert__state_type) que representa o estado da conversão.|  
|`_Berr`|Uma [byte_string](#wstring_convert__byte_string) para ser exibida em caso de erros.|  
|`Werr`|Uma [wide_string](#wstring_convert__wide_string) para ser exibida em caso de erros.|  
  
### <a name="remarks"></a>Comentários  
 O primeiro construtor armazena *Pcvt_arg* no [objeto de conversão](../standard-library/wstring-convert-class.md)
