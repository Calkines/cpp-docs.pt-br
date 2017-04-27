---
title: Classe basic_iostream | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::basic_iostream
- std.basic_iostream
- basic_iostream
- std::basic_iostream
dev_langs:
- C++
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
caps.latest.revision: 22
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: a7980efd6709c5004c88b22916865d78511aa017
ms.lasthandoff: 02/25/2017

---
# <a name="basiciostream-class"></a>Classe basic_iostream
Uma classe de fluxo que pode fazer tanto entrada quanto saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_iostream : public basic_istream<Elem, Tr>,  
    public basic_ostream<Elem, Tr>  
{  
public:  
    explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

    virtual ~basic_iostream();

};  
```  
  
## <a name="remarks"></a>Comentários  
 A classe de modelo descreve um objeto que controla inserções, por meio de sua classe base [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`, `Tr`> e extrações, por meio de sua classe base [basic_istream](../standard-library/basic-istream-class.md)< `Elem`, `Tr`>. Os dois objetos compartilham uma classe base virtual comum [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, `Tr`>. Eles também gerenciam um buffer de fluxo comum, com elementos do tipo `Elem`, cujas características de caractere são determinadas pela classe `Tr`. O construtor inicializa suas classes base por meio de `basic_istream`( **strbuf**) e `basic_ostream`( **strbuf**).  
  
### <a name="constructors"></a>Construtores  
  
|||  
|-|-|  
|[basic_iostream](#basic_iostream__basic_iostream)|Crie um objeto `basic_iostream`.|  
  
### <a name="member-functions"></a>Funções membro  
  
|||  
|-|-|  
|[swap](#basic_iostream__swap)|Troca o conteúdo do objeto `basic_iostream` fornecido pelo conteúdo deste objeto.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator=](#basic_iostream__operator_eq)|Atribui o valor de um objeto `basic_iostream` especificado a esse objeto. Essa é uma atribuição de movimentação que envolve um `rvalue` que não deixa uma cópia.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<istream>  
  
 **Namespace:** std  
  
##  <a name="a-namebasiciostreambasiciostreama--basiciostreambasiciostream"></a><a name="basic_iostream__basic_iostream"></a>  basic_iostream::basic_iostream  
 Crie um objeto `basic_iostream`.  
  
```  
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```  
  
### <a name="parameters"></a>Parâmetros  
 ` strbuf`  
 Um objeto `basic_streambuf` existente.  
  
 ` right`  
 Um objeto `basic_iostream` Existente usado para construir um novo `basic_iostream`.  
  
### <a name="remarks"></a>Comentários  
 O primeiro construtor inicializa os objetos base por meio de `basic_istream(`` strbuf``)` e `basic_ostream(`` strbuf``)`.  
  
 O segundo construtor inicializa os objetos base chamando mover `(`` right``)`.  
  
##  <a name="a-namebasiciostreamoperatoreqa--basiciostreamoperator"></a><a name="basic_iostream__operator_eq"></a>  basic_iostream::operator=  
 Atribua o valor do objeto `basic_iostream` especificado a esse objeto. Essa é uma atribuição de movimentação que envolve um `rvalue` que não deixa uma cópia.  
  
```  
basic_iostream& operator=(basic_iostream&& right);
```  
  
### <a name="parameters"></a>Parâmetros  
 ` right`  
 Uma referência `rvalue` a um objeto `basic_iostream` do qual atribuir.  
  
### <a name="remarks"></a>Comentários  
 O operador do membro chama `(`` right``)` de troca.  
  
##  <a name="a-namebasiciostreamswapa--basiciostreamswap"></a><a name="basic_iostream__swap"></a>  basic_iostream::swap  
 Troca o conteúdo do objeto `basic_iostream` fornecido pelo conteúdo deste objeto.  
  
```  
void swap(basic_iostream& right);
```  
  
### <a name="parameters"></a>Parâmetros  
 ` right`  
 O objeto `basic_iostream` a trocar.  
  
### <a name="remarks"></a>Comentários  
 A função membro chama trocar `(`` right``)`  
  
## <a name="see-also"></a>Consulte também  
 [Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programação de iostream](../standard-library/iostream-programming.md)   
 [Convenções de iostreams](../standard-library/iostreams-conventions.md)

