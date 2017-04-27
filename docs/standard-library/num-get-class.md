---
title: Classe num_get | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- num_get
- std::num_get
- std.num_get
- xlocnum/std::num_get
dev_langs:
- C++
helpviewer_keywords:
- num_get class
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
caps.latest.revision: 18
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
ms.openlocfilehash: 1669ee33324bacd1795b541f99cbef0531956867
ms.lasthandoff: 02/25/2017

---
# <a name="numget-class"></a>Classe num_get
Uma classe de modelo que descreve um objeto que pode servir como uma faceta de localidade para controlar conversões de sequências do tipo `CharType` em valores numéricos.  
  
## <a name="syntax"></a>Sintaxe  
  
```
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>  
class num_get : public locale::facet;
```  
  
#### <a name="parameters"></a>Parâmetros  
 `CharType`  
 O tipo usado em um programa para codificar caracteres em uma localidade.  
  
 `InputIterator`  
 O tipo de iterador do qual as funções get numéricas leem sua entrada.  
  
## <a name="remarks"></a>Comentários  
 Como qualquer faceta de localidade, a ID de objeto estático tem um valor armazenado inicial de zero. A primeira tentativa de acessar seu valor armazenado armazena um valor positivo exclusivo na **id.**  
  
### <a name="constructors"></a>Construtores  
  
|||  
|-|-|  
|[num_get](#num_get__num_get)|O construtor para objetos do tipo `num_get` que são usados para extrair valores numéricos das sequências.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#num_get__char_type)|Um tipo que é usado para descrever um caractere usado por uma localidade.|  
|[iter_type](#num_get__iter_type)|Um tipo que descreve um iterador de entrada.|  
  
### <a name="member-functions"></a>Funções membro  
  
|||  
|-|-|  
|[do_get](#num_get__do_get)|Uma função virtual que é chamada para extrair um valor numérico ou booliano de uma sequência de caracteres.|  
|[get](#num_get__get)|Extrai um valor numérico ou booliano de uma sequência de caracteres.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<locale>  
  
 **Namespace:** std  
  
##  <a name="a-namenumgetchartypea--numgetchartype"></a><a name="num_get__char_type"></a>  num_get::char_type  
 Um tipo que é usado para descrever um caractere usado por uma localidade.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Comentários  
 O tipo é um sinônimo do parâmetro de modelo **CharType**.  
  
##  <a name="a-namenumgetdogeta--numgetdoget"></a><a name="num_get__do_get"></a>  num_get::do_get  
 Uma função virtual que é chamada para extrair um valor numérico ou booliano de uma sequência de caracteres.  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `first`  
 O início do intervalo de caracteres do qual o número será lido.  
  
 `last`  
 O fim do intervalo de caracteres do qual o número será lido.  
  
 `_Iosbase`  
 O [ios_base](../standard-library/ios-base-class.md) cujos sinalizadores são usados pela conversão.  
  
 `_State`  
 O estado para o qual failbit (consulte [ios_base::iostate](../standard-library/ios-base-class.md#ios_base__iostate)) é adicionado após a falha.  
  
 `val`  
 O valor que foi lido.  
  
### <a name="return-value"></a>Valor de retorno  
 O iterador depois que o valor foi lido.  
  
### <a name="remarks"></a>Comentários  
 A primeira função membro virtual protegida,  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `long& val`  
  
 `) const;`  
  
 corresponde a elementos sequenciais começando em `first` na sequência `[``first``,` `last``)` até ter reconhecido um campo de entrada de inteiros completo e não vazio. Se for bem-sucedido, converte esse campo em seu valor equivalente como o tipo `long``,` e armazena o resultado em `val`. Ele retorna um iterador que designa o primeiro elemento além do campo de entrada numérico. Caso contrário, a função não armazena nada em `val` e define `ios_base::failbit` em `state`. Ele retorna um iterador que designa o primeiro elemento além de qualquer prefixo de um campo de entrada de inteiro válido. Em ambos os casos, se o valor retornado for igual a `last`, a função definirá `ios_base::eofbit` em `state`.  
  
 O campo de entrada de inteiro é convertido pelas mesmas regras usadas pelas funções de verificação de correspondência e pela conversão de uma série de elementos `char` de um arquivo. (Cada elemento `char` é considerado mapeado para um elemento equivalente do tipo `Elem` por um mapeamento um para um simples.) A especificação de conversão de verificação equivalente é determinada da seguinte forma:  
  
 Se `iosbase.`[ios_base::flags](../standard-library/ios-base-class.md#ios_base__flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), a especificação de conversão é `lo`.  
  
 Se `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), a especificação de conversão é `lx`.  
  
 Se `iosbase.flags() & ios_base::basefield == 0`, a especificação de conversão é `li`.  
  
 Caso contrário, a especificação de conversão é `ld`.  
  
 O formato de um campo de entrada inteiro é determinado pelo [locale facet](../standard-library/locale-class.md#facet_class)`fac` retornado pela chamada [use_facet](../standard-library/locale-functions.md#use_facet) `<`[numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.` [ios_base::getloc](../standard-library/ios-base-class.md#ios_base__getloc)`())`. Especificamente:  
  
 `fac.`[numpunct::grouping](../standard-library/numpunct-class.md#numpunct__grouping)`()` determina como os dígitos são agrupados à esquerda de qualquer vírgula decimal  
  
 `fac.`[numpunct::thousands_sep](../standard-library/numpunct-class.md#numpunct__thousands_sep)`()` determina a sequência que separa grupos de dígitos à esquerda de qualquer vírgula decimal.  
  
 Se nenhuma instância de `fac.thousands_sep()` ocorrer no campo de entrada numérico, nenhuma restrição de agrupamento é imposta. Caso contrário, qualquer restrição de agrupamento imposta pelo `fac.grouping()` será imposta e os separadores serão removidos antes que a verificação de conversão ocorra.  
  
 A quarta função membro virtual protegida:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `unsigned long& val`  
  
 `) const;`  
  
 comporta-se da mesma maneira que a primeira, exceto que substitui uma especificação de conversão de `ld` por `lu`. Se bem-sucedido, converte o campo de entrada numérico em um valor do tipo `unsigned long` e armazena esse valor em `val`.  
  
 A quinta função membro virtual protegida:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `long long& val`  
  
 `) const;`  
  
 comporta-se da mesma maneira que a primeira, exceto que substitui uma especificação de conversão de `ld` por `lld`. Se bem-sucedido, converte o campo de entrada numérico em um valor do tipo `long long` e armazena esse valor em `val`.  
  
 A sexta função membro virtual protegida:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `unsigned long long& val`  
  
 `) const;`  
  
 comporta-se da mesma maneira que a primeira, exceto que substitui uma especificação de conversão de `ld` por `llu`. Se bem-sucedido, converte o campo de entrada numérico em um valor do tipo `unsigned long long` e armazena esse valor em `val`.  
  
 A sétima função membro virtual protegida:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `float& val`  
  
 `) const;`  
  
 comporta-se da mesma maneira que a primeira, exceto que esforça-se para corresponder a um campo de entrada de ponto flutuante completo e não vazio. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point)`()` determina a sequência que separa os dígitos de inteiro dos dígitos de fração. O especificador de conversão de verificação equivalente é `lf`.  
  
 A oitava função membro virtual protegida:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `double& val`  
  
 `) const;`  
  
 comporta-se da mesma maneira que a primeira, exceto que esforça-se para corresponder a um campo de entrada de ponto flutuante completo e não vazio. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point)`()` determina a sequência que separa os dígitos de inteiro dos dígitos de fração. O especificador de conversão de verificação equivalente é `lf`.  
  
 A nona função membro virtual protegida:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `long double& val`  
  
 `) const;`  
  
 comporta-se da mesma maneira que a oitava, exceto que o especificador de conversão de verificação equivalente é `Lf`.  
  
 A nona função membro virtual protegida:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `void *& val`  
  
 `) const;`  
  
 comporta-se da mesma maneira que a primeira, exceto que o especificador de conversão de verificação equivalente é `p`.  
  
 A última (décima primeira) função membro virtual protegida:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `bool& val`  
  
 `) const;`  
  
 comporta-se da mesma maneira que a primeira, exceto que esforça-se para corresponder a um campo de entrada booliano completo e não vazio. Se bem-sucedido, converte o campo de entrada booliano em um valor do tipo `bool` e armazena esse valor em `val`.  
  
 Um campo de entrada Booliano adota um de dois formatos. Se `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) for false, será o mesmo que um campo de entrada inteiro, exceto que o valor convertido deve ser 0 (para false) ou 1 (para true). Caso contrário, a sequência deve corresponder a `fac.`[numpunct::falsename](../standard-library/numpunct-class.md#numpunct__falsename)`()` (para falso) ou `fac.`[numpunct::truename](../standard-library/numpunct-class.md#numpunct__truename)`()` (para verdadeiro).  
  
### <a name="example"></a>Exemplo  
  Veja o exemplo de [obter](#num_get__get), em que a função membro virtual é chamada por `do_get`.  
  
##  <a name="a-namenumgetgeta--numgetget"></a><a name="num_get__get"></a>  num_get::get  
 Extrai um valor numérico ou booliano de uma sequência de caracteres.  
  
```
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `first`  
 O início do intervalo de caracteres do qual o número será lido.  
  
 `last`  
 O fim do intervalo de caracteres do qual o número será lido.  
  
 `_Iosbase`  
 O [ios_base](../standard-library/ios-base-class.md) cujos sinalizadores são usados pela conversão.  
  
 `_State`  
 O estado para o qual failbit (consulte [ios_base::iostate](../standard-library/ios-base-class.md#ios_base__iostate)) é adicionado após a falha.  
  
 `val`  
 O valor que foi lido.  
  
### <a name="return-value"></a>Valor de retorno  
 O iterador depois que o valor foi lido.  
  
### <a name="remarks"></a>Comentários  
 Todas as funções membro retornam [do_get](#num_get__do_get)( `first`, `last`, `_Iosbase`, `_State`, `val`).  
  
 A primeira função membro virtual protegida virtual tenta corresponder elementos sequenciais, começando pelo primeiro na sequência [ `first`, `last`) até ter reconhecido um campo de entrada inteiro completo e não vazio. Se for bem-sucedido, converte esse campo em seu valor equivalente como o tipo **long** e armazena o resultado em `val`. Ele retorna um iterador que designa o primeiro elemento além do campo de entrada numérico. Caso contrário, a função não armazena nada em `val` e define `ios_base::failbit` em _ *State*. Ele retorna um iterador que designa o primeiro elemento além de qualquer prefixo de um campo de entrada de inteiro válido. Em ambos os casos, se o valor retornado for igual a **last**, a função define `ios_base::eofbit` em `_State`.  
  
 O campo de entrada de inteiro é convertido pelas mesmas regras usadas pelas funções de verificação de correspondência e pela conversão de uma série de elementos `char` de um arquivo. Cada elemento `char` é considerado mapeado para um elemento equivalente do tipo **CharType** por um mapeamento um para um simples. A especificação de conversão de verificação equivalente é determinada da seguinte forma:  
  
-   Se **iosbase**. [flags](../standard-library/ios-base-class.md#ios_base__flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct), a especificação de conversão é **lo**.  
  
-   Se **iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex), a especificação de conversão é **lx**.  
  
-   Se **iosbase.flags** & **ios_base::basefield** == 0, a especificação de conversão é `li`.  
  
-   Caso contrário, a especificação de conversão é **Id**.  
  
 O formato de um campo de entrada inteiro é determinado ainda pelo [locale facet](../standard-library/locale-class.md#facet_class)**fac** retornado pela chamada [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#ios_base__getloc)). Especificamente:  
  
- **fac**. [grouping](../standard-library/numpunct-class.md#numpunct__grouping) determina como os dígitos são agrupados à esquerda da vírgula decimal.  
  
- **fac**. [thousands_sep](../standard-library/numpunct-class.md#numpunct__thousands_sep) determina a sequência que separa grupos de dígitos à esquerda da vírgula decimal.  
  
 Se nenhuma instância de **fac**. `thousands_sep` ocorre no campo de entrada numérico, nenhuma restrição de agrupamento é imposta. Caso contrário, qualquer restrição de agrupamento é imposta por **fac**. **grouping** é imposto e os separadores são removidos antes da conversão de verificação ocorrer.  
  
 A segunda função membro virtual protegida:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```  
  
 comporta-se da mesma maneira que a primeira, exceto que substitui uma especificação de conversão de **Id** por **lu**. Se bem-sucedido, converte o campo de entrada numérico em um valor do tipo `unsigned long` e armazena esse valor em `val`.  
  
 A terceira função membro virtual protegida:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```  
  
 comporta-se da mesma maneira que a primeira, exceto que esforça-se para corresponder a um campo de entrada de ponto flutuante completo e não vazio. **fac**. [decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point) determina a sequência que separa os dígitos de inteiros dos dígitos de fração. O especificador de conversão de verificação equivalente é **If**.  
  
 A quarta função membro virtual protegida:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```  
  
 comporta-se da mesma maneira que a terceira, exceto que o especificador de conversão de verificação equivalente é **Lf**.  
  
 A quinta função membro virtual protegida:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
 comporta-se da mesma maneira que a primeira, exceto que o especificador de conversão de verificação equivalente é **p**.  
  
 A sexta função membro virtual protegida:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
 comporta-se da mesma maneira que a primeira, exceto que tenta corresponder a um campo de entrada booliano completo e não vazio. Se bem-sucedido, converte o campo de entrada booliano em um valor do tipo `bool` e armazena esse valor em `val`.  
  
 Um campo de entrada booliano adota um de dois formatos. Se **iosbase**. Se **flags** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) for **false**, será o mesmo que um campo de entrada inteiro, exceto que o valor convertido deve ser 0 (para **false**) ou 1 (para **true**). Caso contrário, a sequência deve corresponder a **fac**. [falsename](../standard-library/numpunct-class.md#numpunct__falsename) (para **false**) ou **fac**. [truename](../standard-library/numpunct-class.md#numpunct__truename) (para **true**).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// num_get_get.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   basic_stringstream<char> psz, psz2;  
   psz << "-1000,56";  
  
   ios_base::iostate st = 0;  
   long double fVal;  
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;  
  
   psz.imbue( loc );  
   use_facet <num_get <char> >  
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),  
           basic_istream<char>::_Iter(0), psz, st, fVal );  
  
   if ( st & ios_base::failbit )  
      cout << "money_get( ) FAILED" << endl;  
   else  
      cout << "money_get( ) = " << fVal << endl;  
}  
```  
  
##  <a name="a-namenumgetitertypea--numgetitertype"></a><a name="num_get__iter_type"></a>  num_get::iter_type  
 Um tipo que descreve um iterador de entrada.  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>Comentários  
 O tipo é um sinônimo do parâmetro de modelo **InputIterator**.  
  
##  <a name="a-namenumgetnumgeta--numgetnumget"></a><a name="num_get__num_get"></a>  num_get::num_get  
 O construtor para objetos do tipo `num_get` que são usados para extrair valores numéricos das sequências.  
  
```
explicit num_get(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Refs`  
 Valor inteiro usado para especificar o tipo de gerenciamento de memória do objeto.  
  
### <a name="remarks"></a>Comentários  
 Os valores possíveis para o parâmetro `_Refs` e sua significância são:  
  
-   0: o tempo de vida do objeto é gerenciado pelas localidades que o contêm.  
  
-   1: o tempo de vida do objeto deve ser gerenciado manualmente.  
  
-   \> 0: esses valores não estão definidos.  
  
 Nenhum exemplo direto é possível, pois o destruidor está protegido.  
  
 O construtor inicializa seu objeto base com **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`).  
  
## <a name="see-also"></a>Consulte também  
 [\<locale>](../standard-library/locale.md)   
 [Classe facet](../standard-library/locale-class.md#facet_class)   
 [Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



