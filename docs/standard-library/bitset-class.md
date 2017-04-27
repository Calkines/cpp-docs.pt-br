---
title: Classe bitset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- bitset/std::bitset
- bitset
- bitset/std::bitset::element_type
- bitset/std::bitset::all
- bitset/std::bitset::any
- bitset/std::bitset::count
- bitset/std::bitset::flip
- bitset/std::bitset::none
- bitset/std::bitset::reset
- bitset/std::bitset::set
- bitset/std::bitset::size
- bitset/std::bitset::test
- bitset/std::bitset::to_string
- bitset/std::bitset::to_ullong
- bitset/std::bitset::to_ulong
- bitset/std::bitset::reference
dev_langs:
- C++
helpviewer_keywords:
- bitset class
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
caps.latest.revision: 21
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
ms.sourcegitcommit: 441f493d8ada3ef232f60d917dc3f95812ba9114
ms.openlocfilehash: 2e78e22c04bac149694a4c4f860074296c7b37fc
ms.lasthandoff: 02/25/2017

---
# <a name="bitset-class"></a>Classe bitset
Descreve um tipo de objeto que armazena uma sequência que consiste em um número fixo de bits que fornecem uma maneira compacta de manter sinalizadores para um conjunto de itens ou condições. A classe bitset dá suporte a operações em objetos do tipo bitset que contêm uma coleção de bits e fornecem acesso constante a cada bit.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
template <size_t N>  
class bitset  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *N*  
 Especifica o número de bits no objeto bitset com um inteiro diferente de zero do tipo **size_t** que deve ser conhecido no tempo de compilação.  
  
## <a name="remarks"></a>Comentários  
 Ao contrário da [Classe vector\<bool>](../standard-library/vector-bool-class.md) semelhante, a classe bitset não tem iteradores e não é um contêiner da Biblioteca Padrão C++. Ela também é diferente do vetor \<bool> por ser de um tamanho específico que é fixado no tempo de compilação de acordo com o tamanho especificado pelo parâmetro de modelo **N** quando o **bitset\<N\>** é declarado.  
  
 Um bit será definido se seu valor for 1 e redefinido se seu valor for 0. Virar ou inverter um bit é alterar seu valor de 1 para 0 ou de 0 para 1. Os **N** bits em um bitset são indexados por valores inteiros de 0 a **N** - 1, em que 0 indexa a posição do primeiro bit e **N** - 1 a posição do bit final.  
  
### <a name="constructors"></a>Construtores  
  
|||  
|-|-|  
|[bitset](#bitset__bitset)|Constrói um objeto da classe `bitset\<N>` e inicializa os bits como zero, para algum valor especificado ou para valores obtidos dos caracteres em uma cadeia de caracteres.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[element_type](#bitset__element_type)|Um tipo que é um sinônimo do tipo de dados `bool` e pode ser usado para referenciar os bits de elemento em um `bitset`.|  
  
### <a name="member-functions"></a>Funções membro  
  
|||  
|-|-|  
|[all](#bitset__all)|Testa todos os bits nesse `bitset` para determinar se eles estão todos definidos como `true`.|  
|[any](#bitset__any)|A função membro testa se qualquer bit na sequência está definido como 1.|  
|[count](#bitset__count)|A função membro retorna o número de bits definido na sequência de bits.|  
|[flip](#bitset__flip)|Inverte o valor de todos os bits em um `bitset` ou inverte um único bit em uma posição especificada.|  
|[none](#bitset__none)|Testa se nenhum bit foi definido como 1 em um objeto `bitset`.|  
|[reset](#bitset__reset)|Redefine todos os bits em um `bitset` como 0 ou redefine um bit em uma posição especificada como 0.|  
|[set](#bitset__set)|Define todos os bits em um `bitset` como 1 ou define um bit em uma posição especificada como 1.|  
|[size](#bitset__size)|Retorna o número de bits em um objeto `bitset`.|  
|[test](#bitset__test)|Testa se o bit em uma posição especificada em um `bitset` está definido como 1.|  
|[to_string](#bitset__to_string)|Converte um objeto `bitset` em uma representação de cadeia de caracteres.|  
|[to_ullong](#bitset__to_ullong)|Retorna a soma dos valores de no `bitset` como um `unsigned long long`.|  
|[to_ulong](#bitset__to_ulong)|Converte um objeto `bitset` no `unsigned long` que geraria a sequência de bits contidos se fosse usado para inicializar o `bitset`.|  
  
### <a name="member-classes"></a>Classes de membro  
  
|||  
|-|-|  
|[reference](#bitset__reference)|Uma classe de proxy que fornece referências aos bits contidos em um `bitset` que é usado para acessar e manipular os bits individuais como uma classe auxiliar do `operator[]` da classe `bitset`.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator!=](#bitset__operator_neq)|Testa um `bitset` de destino quanto à desigualdade em relação a um `bitset` especificado.|  
|[operator&=](#bitset__operator_and_eq)|Executa uma combinação bit a bit de bitsets com a operação lógica `AND`.|  
|[operator<<](#bitset__operator_lshift)|Desloca os bits em um `bitset` um número especificado de posições à esquerda e retorna o resultado para um novo `bitset`.|  
|[operator<<=](#bitset__operator_lshift_eq)|Desloca os bits em um `bitset` um número especificado de posições à esquerda e retorna o resultado para o `bitset` de destino.|  
|[operator==](#bitset__operator_eq_eq)|Testa um `bitset` de destino quanto à igualdade em relação a um `bitset` especificado.|  
|[operator>>](#bitset__operator_rshift)|Desloca os bits em um `bitset` um número especificado de posições à direita e retorna o resultado para um novo `bitset`.|  
|[operator>>=](#bitset__operator_rshift_eq)|Desloca os bits em um `bitset` um número especificado de posições à direita e retorna o resultado para o `bitset` de destino.|  
|[operator&#91;&#93;](#bitset__operator_at)|Retornará uma referência a um bit em uma posição especificada em um `bitset` se o `bitset` for modificável, caso contrário, retornará o valor do bit nessa posição.|  
|[operator^=](#bitset__operator_xor_eq)|Executa uma combinação bit a bit de bitsets com a operação `OR` exclusiva.|  
|[operator&#124;=](#bitset__operator_or_eq')|Executa uma combinação bit a bit de bitsets com a operação `OR` inclusiva.|  
|[operator~](#bitset__operator_dtor)|Inverte todos os bits em um `bitset` de destino e retorna o resultado.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<bitset>  
  
 **Namespace:** std  
  
##  <a name="bitset__all"></a>  bitset::all  
 Testa todos os bits nesse bitset para determinar se todos estão definidos como true.  
  
```  
bool all() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retornará true se todos os bits nesse conjunto forem true. Retornará **false** se um ou mais bits forem false.  
  
##  <a name="bitset__any"></a>  bitset::any  
 Testa se algum bit na sequência está definido como 1.  
  
```  
bool any() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se algum bit no bitset estiver definido como 1, **false** se todos os bits forem 0.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_any.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 6 );  
   bool b, rb;  
  
   cout << "The original bitset b1( 6 ) is: ( "<< b1 << " )"  
        << endl;  
  
   b = b1.any ( );  
  
   if ( b )  
      cout << "At least one of the bits in bitset is set to 1."  
           << endl;  
   else  
      cout << "None of the bits in bitset are set to 1."  
           << endl;  
  
   bitset<5> rb1;  
   rb1 = b1.reset ( );  
  
   cout << "The reset bitset is: ( "<< b1 << " )"  
        << endl;  
  
   rb = rb1.any ( );  
  
   if ( rb )  
      cout << "At least one of the bits in the reset bitset "  
           << "are set to 1." << endl;  
   else  
      cout << "None of the bits in bitset b1 are set to 1."  
           << endl;  
}  
```  
  
```Output  
The original bitset b1( 6 ) is: ( 00110 )  
At least one of the bits in bitset is set to 1.  
The reset bitset is: ( 00000 )  
None of the bits in bitset b1 are set to 1.  
```  
  
##  <a name="bitset__bitset"></a>  bitset::bitset  
 Constrói um objeto da classe `bitset\<N>` e inicializa os bits como zero, como algum valor especificado ou como os valores obtidos dos caracteres em uma cadeia de caracteres.  
  
```  
bitset();

bitset(
    unsigned long long val);

explicit bitset(
    const char* _CStr);

template <class CharType,   
    class Traits,   
    class Allocator>  
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,  
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos = 0);

template <class CharType,  
    class Traits,  
    class Allocator>  
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,  
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos,  
    typename basic_string<CharType, Traits, Allocator>::size_type count,  
    CharType _Zero = CharType ('0'),   
    CharType _One = CharType ('1'));
```  
  
### <a name="parameters"></a>Parâmetros  
 `val`  
 O inteiro sem sinal cuja representação de base dois é usada para inicializar os bits no bitset que está sendo construído.  
  
 `str`  
 A cadeia de caracteres de zeros e uns usada para inicializar os valores de bits do bitset.  
  
 `_CStr`  
 Uma cadeia de caracteres do estilo C de zeros e uns usada para inicializar os valores de bit do bitset.  
  
 `_Pos`  
 A posição do caractere na cadeia de caracteres, contando da esquerda para a direita e começando com zero, usada para inicializar o primeiro bit no bitset.  
  
 `count`  
 O número de caracteres na cadeia de caracteres que é usado para fornecer os valores iniciais dos bits no bitset.  
  
 `_Zero`  
 O caractere que é usado para representar um zero. O padrão é '0'.  
  
 `_One`  
 O caractere que é usado para representar um. O padrão é '1'.  
  
### <a name="remarks"></a>Comentários  
 Três construtores podem ser usados para construir objetos da classe `bitset\<N>`:  
  
-   O primeiro construtor não aceita parâmetros, constrói um objeto da classe `bitset\<N>` e inicializa todos os N bits com um valor padrão igual a zero.  
  
-   O segundo construtor constrói um objeto da classe `bitset\<N>` e inicializa os bits usando o único parâmetro `unsigned long long`.  
  
-   O terceiro construtor constrói um objeto da classe `bitset\<N>`, inicializando os N bits com os valores que correspondem aos caracteres fornecidos em uma cadeia de caracteres do estilo c de zeros e uns. Chame o construtor sem converter a cadeia de caracteres em um tipo de cadeia de caracteres: `bitset<5> b5("01011");`  
  
 Também há dois modelos de construtor fornecidos:  
  
-   O primeiro modelo de construtor constrói um objeto da classe `bitset\<N>` e inicializa os bits dos caracteres fornecidos em uma cadeia de caracteres de zeros e uns. Se algum caractere da cadeia de caracteres for diferente de 0 ou 1, o construtor gerará um objeto da classe [invalid argument](../standard-library/invalid-argument-class.md). Se a posição especificada (`_Pos`) estiver além do comprimento da cadeia de caracteres, o construtor gerará um objeto da classe [out_of_range](../standard-library/out-of-range-class.md). O construtor apenas define os bits na posição *j* no bitset cujo caractere na cadeia de caracteres na posição `_Pos + j` é 1. Por padrão, `_Pos` é 0.  
  
-   O segundo modelo de construtor é semelhante ao primeiro, mas inclui um parâmetro adicional (`count`) que é usado para especificar o número de bits a serem inicializados. Ele também tem dois parâmetros opcionais, `_Zero` e `_One`, que indica qual caractere em `str` deve ser interpretado como um bit 0 e um bit 1, respectivamente.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_bitset.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   // Using the default constructor  
   using namespace std;  
   bitset<2> b0;  
   cout << "The set of bits in bitset<2> b0 is: ( "  
        << b0 << " )." << endl;  
  
   // Using the second member function  
   bitset<5> b1 ( 6 );  
   cout << "The set of bits in bitset<5> b1( 6 ) is: ( "  
        << b1 << " )." << endl;  
  
   // The template parameter N can be an expresssion  
   bitset< 2 * sizeof ( int ) > b2;  
   cout << "The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( "  
        << b2 << " )." << endl;  
  
   // The base two representation will be truncated  
   // if its length exceeds the size of the bitset  
   bitset<3> b3 ( 6 );  
   cout << "The set of bits in bitset<3> b3( 6 ) is ( "  
        << b3 << " )." << endl;  
  
   // Using a c-style string to initialize the bitset  
    bitset<7> b3andahalf ( "1001001" );  
    cout << "The set of bits in bitset<7> b3andahalf ( \"1001001\" )"  
         << " is ( " << b3andahalf << " )." << endl;   
  
   // Using the fifth member function with the first parameter  
   string bitval4 ( "10011" );  
   bitset<5> b4 ( bitval4 );  
   cout << "The set of bits in bitset<5> b4( bitval4 ) is ( "  
        << b4 << " )." << endl;  
  
   // Only part of the string may be used for initialization  
  
   // Starting at position 3 for a length of 6 (100110)  
   string bitval5 ("11110011011");  
   bitset<6> b5 ( bitval5, 3, 6 );  
   cout << "The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( "  
        << b5 << " )." << endl;  
  
   // The bits not initialized with part of the string  
   // will default to zero  
   bitset<11> b6 ( bitval5, 3, 5 );  
   cout << "The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( "  
        << b6 << " )." << endl;  
  
   // Starting at position 2 and continue to the end of the string  
   bitset<9> b7 ( bitval5, 2 );  
   cout << "The set of bits in bitset<9> b7( bitval, 2 ) is ( "  
        << b7 << " )." << endl;  
}  
```  
  
```Output  
The set of bits in bitset<2> b0 is: ( 00 ).  
The set of bits in bitset<5> b1( 6 ) is: ( 00110 ).  
The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( 00000000 ).  
The set of bits in bitset<3> b3( 6 ) is ( 110 ).  
The set of bits in bitset<5> b4( bitval4 ) is ( 10011 ).  
The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( 100110 ).  
The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( 00000010011 ).  
The set of bits in bitset<9> b7( bitval, 2 ) is ( 110011011 ).  
```  
  
##  <a name="bitset__count"></a>  bitset::count  
 Retorna o número de bits definidos na sequência de bits.  
  
```  
size_t count() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
  
O número de bits definidos na sequência de bits.  
  
### <a name="example"></a>Exemplo  
  
O exemplo a seguir demonstra o uso da função membro bitset::count.  
  
```cpp  
// bitset_count.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
  
    bitset<5> b1(4);  
  
    cout << "The collection of bits in the original bitset is: ( "  
         << b1 << " )" << endl;  
  
    size_t i;  
    i = b1.count();  
    cout << "The number of bits in the bitset set to 1 is: "  
         << i << "." << endl;  
  
    bitset<5> fb1;  
    fb1 = b1.flip();  
  
    cout << "The collection of flipped bits in the modified bitset "  
         << "is: ( " << b1 << " )" << endl;  
  
    size_t ii;  
    ii = fb1.count();  
    cout << "The number of bits in the bitset set to 1 is: "  
         << ii << "." << endl;  
}  
```  
  
```Output  
The collection of bits in the original bitset is: ( 00100 )  
The number of bits in the bitset set to 1 is: 1.  
The collection of flipped bits in the modified bitset is: ( 11011 )  
The number of bits in the bitset set to 1 is: 4.  
```  
  
##  <a name="bitset__element_type"></a>  bitset::element_type  
 Um tipo que é sinônimo do tipo de dados `bool` e pode ser usado para referenciar os bits de elemento em um bitset.  
  
```  
typedef bool element_type;  
```  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_elem_type.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<3> b1 ( 2 );  
   cout << "Original bitset b1(6) is: ( "<< b1 << " )"  
        << endl;  
  
   //Compare two ways to reference bits in a bitset  
   bool b;  
   bitset<5>::element_type e;  
  
   b = b1.test ( 2 );  
   if ( b )  
      cout << "The bit at position 2 of bitset b1"  
           << "has a value of 1." << endl;  
   else  
      cout << "The bit at position 2 of bitset b1"  
           << "has a value of 0." << endl;  
   b1[2] = 1;  
   cout << "Bitset b1 modified by b1[2] = 1 is: ( "<< b1 << " )"  
        << endl;  
  
   e = b1.test ( 2 );  
   if ( e )  
      cout << "The bit at position 2 of bitset b1"  
           << "has a value of 1." << endl;  
   else  
      cout << "The bit at position 2 of bitset b1"  
           << "has a value of 0." << endl;  
}  
```  
  
```Output  
Original bitset b1(6) is: ( 010 )  
The bit at position 2 of bitset b1has a value of 0.  
Bitset b1 modified by b1[2] = 1 is: ( 110 )  
The bit at position 2 of bitset b1has a value of 1.  
```  
  
##  <a name="bitset__flip"></a>  bitset::flip  
 Inverte o valor de todos os bits em um bitset ou inverte um único bit em uma posição especificada.  
  
```  
bitset\<N>& flip();  
bitset\<N>& flip(size_t _Pos);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Pos`  
 A posição do bit cujo valor deve ser invertido.  
  
### <a name="return-value"></a>Valor de retorno  
 Uma cópia do bitset modificado para o qual a função membro foi invocada.  
  
### <a name="remarks"></a>Comentários  
 A segunda função membro gera uma exceção [out_of_range](../standard-library/out-of-range-class.md) quando a posição especificada como um parâmetro é maior que o tamanho *N* do **bitset\<***N***>** cujo bit foi invertido.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_flip.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 6 );  
  
   cout << "The collection of bits in the original bitset is: ( "  
        << b1 << " )" << endl;  
  
   bitset<5> fb1;  
   fb1 = b1.flip ( );  
  
   cout << "After flipping all the bits, the bitset becomes: ( "  
        << fb1 << " )" << endl;  
  
   bitset<5> f3b1;  
   f3b1 = b1.flip ( 3 );  
  
   cout << "After flipping the fourth bit, the bitset becomes: ( "  
        << f3b1 << " )" << endl << endl;  
  
   bitset<5> b2;  
   int i;  
   for ( i = 0 ; i <= 4 ; i++ )  
   {  
      b2.flip(i);  
      cout << b2 << "  The bit flipped is in position "  
           << i << ".\n";  
   }  
}  
```  
  
```Output  
The collection of bits in the original bitset is: ( 00110 )  
After flipping all the bits, the bitset becomes: ( 11001 )  
After flipping the fourth bit, the bitset becomes: ( 10001 )  
  
00001  The bit flipped is in position 0.  
00011  The bit flipped is in position 1.  
00111  The bit flipped is in position 2.  
01111  The bit flipped is in position 3.  
11111  The bit flipped is in position 4.  
```  
  
##  <a name="bitset__none"></a>  bitset::none  
 Testa se nenhum bit foi definido como 1 em um objeto bitset.  
  
```  
bool none() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se nenhum bit no bitset tiver sido definido como 1, **false** se pelo menos um bit foi definido como 1.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_none.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 6 );  
   bool b, rb;  
  
   cout << "Original bitset b1(6) is: ( " << b1 << " )"  
        << endl;  
  
   b = b1.none ( );  
  
   if ( b )  
      cout << "None of the bits in bitset b1 are set to 1."  
           << endl;  
   else  
      cout << "At least one of the bits in bitset b1 is set to 1."  
           << endl;  
  
   bitset<5> rb1;  
   rb1 = b1.reset ( );  
   rb = rb1.none ( );  
   if ( rb )  
      cout << "None of the bits in bitset b1 are set to 1."  
           << endl;  
   else  
      cout << "At least one of the bits in bitset b1 is set to 1."  
           << endl;  
}  
```  
  
```Output  
Original bitset b1(6) is: ( 00110 )  
At least one of the bits in bitset b1 is set to 1.  
None of the bits in bitset b1 are set to 1.  
```  
  
##  <a name="bitset__operator_neq"></a>  bitset::operator!=  
 Testa um conjunto de bits de destino quanto à desigualdade em relação a um bitset especificado.  
  
```  
bool operator!=(const bitset\<N>& right) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `right`  
 O bitset a ser comparado com o bitset de destino quanto à desigualdade.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se os bitsets forem diferentes, **false** se eles forem iguais.  
  
### <a name="remarks"></a>Comentários  
 Os bitsets deve ser do mesmo tamanho para serem testados quanto à desigualdade pela função de operador de membro.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_op_NE.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 7 );  
   bitset<5> b3 ( 2 );  
   bitset<4> b4 ( 7 );  
  
   if ( b1 != b2 )  
      cout << "Bitset b1 is different from bitset b2." << endl;  
   else  
      cout << "Bitset b1 is the same as bitset b2." << endl;  
  
   if ( b1 != b3 )  
      cout << "Bitset b1 is different from bitset b3." << endl;  
   else  
      cout << "Bitset b1 is the same as bitset b3." << endl;  
  
   // This would cause an error because bitsets must have the  
   // same size to be tested  
   // if ( b1 != b4 )  
   //   cout << "Bitset b1 is different from bitset b4." << endl;  
   // else  
   //   cout << "Bitset b1 is the same as bitset b4." << endl;  
}  
```  
  
```Output  
Bitset b1 is the same as bitset b2.  
Bitset b1 is different from bitset b3.  
```  
  
##  <a name="bitset__operator_and_eq"></a>  bitset::operator&amp;=  
 Executa uma combinação bit a bit de bitsets com a operação lógica **AND**.  
  
```  
bitset\<N>& operator&=(const bitset\<N>& right);
```  
  
### <a name="parameters"></a>Parâmetros  
 `right`  
 O bitset que deve ser combinado bit a bit com o bitset de destino.  
  
### <a name="return-value"></a>Valor de retorno  
 O bitset de destino modificado que resulta da operação **AND** bit a bit com o bitset especificado como um parâmetro.  
  
### <a name="remarks"></a>Comentários  
 Dois bits combinados pelo operador **AND** retornarão **true** se cada bit for true, caso contrário, a combinação retornará **false**.  
  
 Os bitsets deve ser do mesmo tamanho para serem combinados bit a bit com o operador **AND** pela função de operador de membro.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_op_bitwise.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 11 );  
   bitset<4> b3 ( 7 );  
  
   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;  
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;  
   cout << endl;  
  
   b1 &= b2;  
   cout << "After bitwise AND combination,\n"  
        << " the target bitset b1 becomes:   ( "<< b1 << " )."   
        << endl;  
  
   // Note that the parameter-specified bitset is unchanged  
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."   
        << endl;  
  
   // The following would cause an error because the bisets   
   // must be of the same size to be combined  
   // b1 &= b3;  
}  
```  
  
```Output  
The target bitset b1 is:    ( 00111 ).  
The parameter bitset b2 is: ( 01011 ).  
  
After bitwise AND combination,  
 the target bitset b1 becomes:   ( 00011 ).  
The parameter bitset b2 remains: ( 01011 ).  
```  

##  <a name="bitset__operator_lshift"></a> bitset::operator\<\<    
  
Desloca os bits em um bitset um número especificado de posições à esquerda e retorna o resultado para um novo bitset.  
  
```  
bitset\<N> operator<<(size_t _Pos) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Pos`  
 O número de posições à esquerda que os bits no bitset devem ser deslocados.  
  
### <a name="return-value"></a>Valor de retorno  
 O bitset modificado com os bits deslocados o número necessário de posições à esquerda.  
  
### <a name="remarks"></a>Comentários  
 A função de operador de membro retorna **bitset**(**\*this**) **<<= pos,** em que [<<=](#bitset__operator_lshift_eq) desloca os bits em um bitset um número especificado de posições à esquerda e retorna o resultado ao bitset de destino.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_op_LS.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
  
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;  
  
   bitset<5> b2;  
   b2 = b1 << 2;  
  
   cout << "After shifting the bits 2 positions to the left,\n"  
        << " the bitset b2 is: ( "<< b2 << " )."  
        << endl;  
  
   bitset<5> b3 = b2 >> 1;  
  
   cout << "After shifting the bits 1 position to the right,\n"  
        << " the bitset b3 is: ( " << b3 << " )."  
        << endl;  
}  
```  
  
##  <a name="bitset__operator_lshift_eq"></a>  bitset::operator&lt;&lt;=  
 Desloca os bits em um bitset um número especificado de posições à esquerda e retorna o resultado para um bitset de destino.  
  
```  
bitset\<N>& operator<<=(size_t _Pos);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Pos`  
 O número de posições para a esquerda que os bits no bitset devem ser deslocados.  
  
### <a name="return-value"></a>Valor de retorno  
 O bitset de destino modificado de forma que os bits foram deslocados o número necessário de posições à esquerda.  
  
### <a name="remarks"></a>Comentários  
 Se não existir nenhum elemento na posição, a função limpará o bit para o valor 0.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_op_LSE.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 7 );  
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;  
   b1 <<= 2;  
   cout << "After shifting the bits 2 positions to the left,\n"  
        << " the target bitset b1 becomes: ( "<< b1 << " )."   
        << endl;  
}  
```  
  
```Output  
The target bitset b1 is: ( 00111 ).  
After shifting the bits 2 positions to the left,  
 the target bitset b1 becomes: ( 11100 ).  
```  
  
##  <a name="bitset__operator_eq_eq"></a>  bitset::operator==  
 Testa um bitset de destino quanto à igualdade com um bitset especificado.  
  
```  
bool operator==(const bitset\<N>& right) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `right`  
 O bitset a ser comparado com o bitset de destino quanto à igualdade.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se os bitsets forem iguais, **false** se eles forem diferentes.  
  
### <a name="remarks"></a>Comentários  
 Os bitsets devem ser do mesmo tamanho para serem testados quanto à igualdade pela função de operador de membro.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_op_EQ.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 7 );  
   bitset<5> b3 ( 2 );  
   bitset<4> b4 ( 7 );  
  
   if ( b1 == b2 )  
      cout << "Bitset b1 is the same as bitset b2." << endl;  
   else  
      cout << "Bitset b1 is different from bitset b2." << endl;  
  
   if ( b1 == b3 )  
      cout << "Bitset b1 is the same as bitset b3." << endl;  
   else  
      cout << "Bitset b1 is different from bitset b3." << endl;  
  
   // This would cause an error because bitsets must have the   
   // same size to be tested  
   // if ( b1 == b4 )  
   //   cout << "Bitset b1 is the same as bitset b4." << endl;  
   // else  
   //   cout << "Bitset b1 is different from bitset b4." << endl;  
}  
```  
  
```Output  
Bitset b1 is the same as bitset b2.  
Bitset b1 is different from bitset b3.  
```  
  
##  <a name="bitset__operator_rshift"></a>  bitset::operator&gt;&gt;  
 Desloca os bits em um bitset um número especificado de posições à direita e retorna o resultado para um novo bitset.  
  
```  
bitset\<N> operator>>(size_t _Pos) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Pos`  
 O número de posições à direita que os bits no bitset devem ser deslocados.  
  
### <a name="return-value"></a>Valor de retorno  
 Um novo bitset para o qual os bits foram deslocados à direita um número necessário de posições relativas ao bitset de destino.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_op_RS.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 7 );  
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;  
  
   bitset<5> b2;  
   b2 = b1 << 2;  
  
   cout << "After shifting the bits 2 positions to the left,\n"  
        << " the bitset b2 is: ( "<< b2 << " )."  
        << endl;  
   bitset<5> b3 = b2 >> 1;  
  
   cout << "After shifting the bits 1 position to the right,\n"  
        << " the bitset b3 is: ( " << b3 << " )."  
        << endl;  
}  
```  
  
```Output  
The bitset b1 is: ( 00111 ).  
After shifting the bits 2 positions to the left,  
 the bitset b2 is: ( 11100 ).  
After shifting the bits 1 position to the right,  
 the bitset b3 is: ( 01110 ).  
```  
  
##  <a name="bitset__operator_rshift_eq"></a>  bitset::operator&gt;&gt;=  
 Desloca os bits em um bitset para a direita um número especificado de posições e retorna o resultado ao bitset de destino.  
  
```  
bitset\<N>& operator>>=(size_t _Pos);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Pos`  
 O número de posições à direita que os bits no bitset devem ser deslocados.  
  
### <a name="return-value"></a>Valor de retorno  
 O bitset de destino modificado com os bits deslocados o número necessário de posições à direita.  
  
### <a name="remarks"></a>Comentários  
 Se não existir nenhum elemento na posição, a função limpará o bit para o valor 0.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_op_RSE.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 28 );  
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;  
  
   b1 >>= 2;  
   cout << "After shifting the bits 2 positions to the right,\n"  
        << " the target bitset b1 becomes: ( "<< b1 << " )."   
        << endl;  
}  
```  
  
```Output  
The target bitset b1 is: ( 11100 ).  
After shifting the bits 2 positions to the right,  
 the target bitset b1 becomes: ( 00111 ).  
```  
  
##  <a name="bitset__operator_at"></a>  bitset::operator[]  
 Retornará uma referência a um bit em uma posição especificada em um bitset, se o bitset for modificável, caso contrário, retornará o valor do bit nessa posição.  
  
```  
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Pos`  
 A posição que localiza o bit dentro do bitset.  
  
### <a name="remarks"></a>Comentários  
Quando você definir [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) como 1 ou 2 no build, um erro de tempo de execução ocorrerá em seu executável se você tentar acessar um elemento fora dos limites do bitset. Para obter mais informações, consulte [Iteradores verificados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_op_REF.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bool b;  
   bitset<5> b1 ( 6 );  
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."  
        << endl;  
  
   int i;  
   for ( i = 0 ; i <= 4 ; i++ )  
   {  
      b = b1[ i ];  
      cout << "  The bit in position "  
           << i << " is " << b << ".\n";  
   }  
}  
```  
  
##  <a name="bitset__operator_xor_eq"></a>  bitset::operator^=  
 Executa uma combinação bit a bit de bitsets com a operação `OR` exclusiva.  
  
```  
bitset\<N>& operator^=(const bitset\<N>& right);
```  
  
### <a name="parameters"></a>Parâmetros  
 `right`  
 O bitset que deve ser combinado bit a bit com o bitset de destino.  
  
### <a name="return-value"></a>Valor de retorno  
 O bitset de destino modificado que resulta da operação `OR` exclusiva bit a bit com o bitset especificado como um parâmetro.  
  
### <a name="remarks"></a>Comentários  
 Dois bits combinados pelo operador **OR** exclusivo retornam **true** se pelo menos um, mas não os dois bits são **true**, caso contrário, a combinação retorna **false**.  
  
 Os bitsets devem ser do mesmo tamanho para serem combinados bit a bit com o operador `OR` exclusivo pela função de operador de membro.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_op_bitwiseOR.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 11 );  
   bitset<4> b3 ( 7 );  
  
   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;  
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;  
   cout << endl;  
  
   b1 ^= b2;  
   cout << "After bitwise exclusive OR combination,\n"  
        << " the target bitset b1 becomes:   ( "<< b1 << " )."   
        << endl;  
  
   // Note that the parameter-specified bitset in unchanged  
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."   
        << endl;  
  
   // The following would cause an error because the bisets   
   // must be of the same size to be combined  
   // b1 |= b3;  
}  
```  
  
```Output  
The target bitset b1 is:    ( 00111 ).  
The parameter bitset b2 is: ( 01011 ).  
  
After bitwise exclusive OR combination,  
 the target bitset b1 becomes:   ( 01100 ).  
The parameter bitset b2 remains: ( 01011 ).  
```  
  
##  <a name="bitset__operator_or_eq"></a>  bitset::operator&#124;=  
 Executa uma combinação bit a bit de bitsets com a operação `OR` inclusiva.  
  
```  
bitset\<N>& operator|=(const bitset\<N>& right);
```  
  
### <a name="parameters"></a>Parâmetros  
 `right`  
 O bitset que deve ser combinado bit a bit com o bitset de destino.  
  
### <a name="return-value"></a>Valor de retorno  
 O bitset de destino modificado que resulta da operação `OR` inclusiva bit a bit com o bitset especificado como um parâmetro.  
  
### <a name="remarks"></a>Comentários  
 Dois bits combinados pelo operador `OR` inclusivo retornarão **true** se pelo menos um dos bits for **true**. Se os dois bits forem **false**, a combinação retornará **false**.  
  
 Os bitsets devem ser do mesmo tamanho para serem combinados bit a bit com o operador `OR` inclusivo pela função de operador de membro.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_op_BIO.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 11 );  
   bitset<4> b3 ( 7 );  
  
   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;  
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;  
   cout << endl;  
  
   b1 |= b2;  
   cout << "After bitwise inclusive OR combination,\n"  
        << " the target bitset b1 becomes:   ( "<< b1 << " )."   
        << endl;  
  
   // Note that the parameter-specified bitset in unchanged  
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."   
        << endl;  
  
   // The following would cause an error because the bisets   
   // must be of the same size to be combined  
   // b1 |= b3;  
}  
```  
  
```Output  
The target bitset b1 is:    ( 00111 ).  
The parameter bitset b2 is: ( 01011 ).  
  
After bitwise inclusive OR combination,  
 the target bitset b1 becomes:   ( 01111 ).  
The parameter bitset b2 remains: ( 01011 ).  
```  
  
##  <a name="bitset__operator_dtor"></a>  bitset::operator~  
 Inverte todos os bits em um bitset de destino e retorna o resultado.  
  
```  
bitset\<N> operator~() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O bitset com todos os seus bits invertidos em relação ao bitset de destino.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_op_invert.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
#include <bitset>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
   bitset<5> b2;  
   b2 = ~b1;  
  
   cout << "Bitset b1 is: ( "<< b1 << " )." << endl;  
   cout << "Bitset b2 = ~b1 is: ( "<< b2 << " )." << endl;  
  
   // These bits could also be flipped using the flip member function  
   bitset<5> b3;  
   b3 = b1.flip( );  
   cout << "Bitset b3 = b1.flip( ) is: ( "<< b2 << " )." << endl;  
}  
```  
  
```Output  
Bitset b1 is: ( 00111 ).  
Bitset b2 = ~b1 is: ( 11000 ).  
Bitset b3 = b1.flip( ) is: ( 11000 ).  
```  
  
##  <a name="bitset__reference"></a>  bitset::reference  
 Uma classe de proxy que fornece referências aos bits contidos em um bitset que é usado para acessar e manipular bits individuais como uma classe auxiliar para o `operator[]` da classe bitset.  
  
```  
class reference {  
   friend class bitset\<N>;  
public: 
   reference& operator=(bool val);
   reference& operator=(const reference& _Bitref);
   bool operator~() const;
   operator bool() const;
   reference& flip();
};  
```    
  
### <a name="parameters"></a>Parâmetros  
 `val`  
 O valor do objeto do tipo `bool` a ser atribuído a um bit em um bitset.  
  
 `_Bitref`  
 Uma referência no formato *x [i]* ao bit na posição *i* no bitset *x*.  
  
### <a name="return-value"></a>Valor de retorno  
 Uma referência ao bit no bitset especificado pela posição do argumento da primeira, da segunda e da quinta função membro de referência de classe e **true** ou **false** para refletir o valor do bit modificado no bitset da terceira e da quarta função de membro de referência de classe.  
  
### <a name="remarks"></a>Comentários  
 A classe `reference` existe apenas como uma classe auxiliar para o bitset `operator[]`. A classe de membro descreve um objeto que pode acessar um bit individual em um bitset. Permita que *b* seja um objeto do tipo `bool`, *x* e *y* sejam objetos do tipo **bitset\<***N***>** e *i* e *j* sejam posições válidas dentro desse objeto. A notação *x [i]* referencia o bit na posição *i* no bitset *x*. As funções membro da classe `reference` fornecem, em ordem, as seguintes operações:  
  
|Operação|Definição|  
|---------------|----------------|  
|*x*[*i*] = *b*|Armazena o valor `bool` *b* na posição de bit *i* no bitset *x*.|  
|*x*[*i*] = *y*[*j*]|Armazena o valor do bit *y* [*j*] na posição de bit *i* no bitset *x*.|  
|*b* = ~ *x*[*i*]|Armazena o valor invertido do bit *x* [*i*] em `bool` *b*.|  
|*b* = *x*[*i*]|Armazena o valor do bit *x* [*i*] em `bool` *b*.|  
|*x*[*i*]. `flip`( )|Armazena o valor invertido do bit *x* [*,*] novamente na posição de bit *i* em *x*.|  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_reference.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 2 );  
   bitset<5> b2 ( 6 );  
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."  
        << endl;  
   cout << "The initialized bitset<5> b2( 6 ) is: ( "<< b2 << " )."  
        << endl;  
  
   // Example of x [i] = b storing bool b at bit position i  
   // in bitset x  
   b1[ 0 ] = true;  
   cout << "The bitset<5> b1 with the bit at position 0 set to 1"  
        << " is: ( "<< b1 << " )" << endl;  
  
   // Example of x [i] = y [j] storing the bool value of the  
   // bit at position j in bitset y at bit position i in bitset x  
   b2 [4] = b1 [0];      // b1 [0] = true  
   cout << "The bitset<5> b2 with the bit at position 4 set to the "  
        << "value\n of the bit at position 0 of the bit in "  
        << "bitset<5> b1 is: ( "<<  b2  << " )" << endl;  
  
   // Example of b = ~x [i] flipping the value of the bit at  
   // position i of bitset x and storing the value in an   
   // object b of type bool  
   bool b = ~b2 [4];      // b2 [4] = false  
   if ( b )  
      cout << "The value of the object b = ~b2 [4] "  
           << "of type bool is true." << endl;  
   else  
      cout << "The value of the object b = ~b2 [4] "  
           << "of type bool is false." << endl;  
  
   // Example of b = x [i] storing the value of the bit at  
   // position i of bitset x in the object b of type bool  
   b = b2 [4];  
   if ( b )  
      cout << "The value of the object b = b2 [4] "  
           << "of type bool is true." << endl;  
   else  
      cout << "The value of the object b = b2 [4] "  
           << "of type bool is false." << endl;  
  
   // Example of x [i] . flip ( ) toggling the value of the bit at  
   // position i of bitset x  
   cout << "Before flipping the value of the bit at position 4 in "  
        << "bitset b2,\n it is ( "<<  b2  << " )." << endl;  
   b2 [4].flip( );  
   cout << "After flipping the value of the bit at position 4 in "  
        << "bitset b2,\n it becomes ( "<<  b2  << " )." << endl;  
   bool c;  
   c = b2 [4].flip( );  
   cout << "After a second flip, the value of the position 4"  
        << " bit in b2 is now: " << c << ".";  
}  
```  
  
```Output  
The initialized bitset<5> b1( 2 ) is: ( 00010 ).  
The initialized bitset<5> b2( 6 ) is: ( 00110 ).  
The bitset<5> b1 with the bit at position 0 set to 1 is: ( 00011 )  
The bitset<5> b2 with the bit at position 4 set to the value  
 of the bit at position 0 of the bit in bitset<5> b1 is: ( 10110 )  
The value of the object b = ~b2 [4] of type bool is false.  
The value of the object b = b2 [4] of type bool is true.  
Before flipping the value of the bit at position 4 in bitset b2,  
 it is ( 10110 ).  
After flipping the value of the bit at position 4 in bitset b2,  
 it becomes ( 00110 ).  
After a second flip, the value of the position 4 bit in b2 is now: 1.  
```  
  
##  <a name="bitset__reset"></a>  bitset::reset  
 Redefine todos os bits em um bitset como 0 ou redefine um bit em uma posição especificada como 0.  
  
```  
bitset\<N>& reset();  
bitset\<N>& reset(size_t _Pos);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Pos`  
 A posição do bit no bitset a ser redefinido como 0.  
  
### <a name="return-value"></a>Valor de retorno  
 Uma cópia do bitset para o qual a função membro foi invocada.  
  
### <a name="remarks"></a>Comentários  
 A segunda função membro gera uma exceção [out_of_range](../standard-library/out-of-range-class.md) quando a posição especificada é maior que o tamanho do bitset.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_reset.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 13 );  
   cout << "The set of bits in bitset<5> b1(13) is: ( "<< b1 << " )"  
        << endl;  
  
   bitset<5> b1r3;  
   b1r3 = b1.reset( 2 );  
   cout << "The collecion of bits obtained from resetting the\n"  
        << " third bit of bitset b1 is: ( "<< b1r3 << " )"   
        << endl;  
  
   bitset<5> b1r;  
   b1r = b1.reset( );  
   cout << "The collecion of bits obtained from resetting all\n"  
        << " the elements of the bitset b1 is: ( "<< b1r << " )"  
        << endl;  
}  
```  
  
```Output  
The set of bits in bitset<5> b1(13) is: ( 01101 )  
The collecion of bits obtained from resetting the  
 third bit of bitset b1 is: ( 01001 )  
The collecion of bits obtained from resetting all  
 the elements of the bitset b1 is: ( 00000 )  
```  
  
##  <a name="bitset__set"></a>  bitset::set  
 Define todos os bits em um bitset como 1 ou define um bit em uma posição especificada como 1.  
  
```   
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,   
    bool val = true);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Pos`  
 A posição do bit no bitset a ser definida como um valor atribuído.  
  
 `val`  
 O valor a ser atribuído ao bit na posição especificada.  
  
### <a name="return-value"></a>Valor de retorno  
 Uma cópia do bitset para o qual a função membro foi invocada.  
  
### <a name="remarks"></a>Comentários  
 A segunda função membro gera uma exceção [out_of_range](../standard-library/out-of-range-class.md) quando a posição especificada é maior que o tamanho do bitset.  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// bitset_set.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 6 );  
   cout << "The set of bits in bitset<5> b1(6) is: ( "<< b1 << " )"  
        << endl;  
  
   bitset<5> b1s0;  
   b1s0 = b1.set( 0 );  
   cout << "The collecion of bits obtained from setting the\n"  
        << " zeroth bit of bitset b1 is: ( "<< b1s0 << " )"   
        << endl;  
  
   bitset<5> bs1;  
   bs1 = b1.set( );  
   cout << "The collecion of bits obtained from setting all the\n"  
        << " elements of the bitset b1 is: ( "<< bs1 << " )"  
        << endl;  
}  
```  
  
```Output  
The set of bits in bitset<5> b1(6) is: ( 00110 )  
The collecion of bits obtained from setting the  
 zeroth bit of bitset b1 is: ( 00111 )  
The collecion of bits obtained from setting all the  
 elements of the bitset b1 is: ( 11111 )  
```  
  
##  <a name="bitset__size"></a>  bitset::size  
 Retorna o número de bits em um objeto bitset.  
  
```  
size_t size() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O número de bits, *N*, em um bitset\<N>.  
  
### <a name="example"></a>Exemplo  
  O exemplo a seguir demonstra o uso da função membro bitset::size.  
  
```cpp  
// bitset_size.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    bitset<5> b1(6);  
    size_t i;  
  
    cout << "The set of bits in bitset<5> b1( 6 ) is: ( "<< b1 << " )"  
         << endl;  
  
    i = b1.size();  
  
    cout << "The number of bits in bitset b1 is: " << i << "."  
         << endl;  
}  
```  
  
```Output  
The set of bits in bitset<5> b1( 6 ) is: ( 00110 )  
The number of bits in bitset b1 is: 5.  
```  
  
##  <a name="bitset__test"></a>  bitset::test  
 Testa se o bit em uma posição especificada em um bitset é definido como 1.  
  
```  
bool test(size_t _Pos) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Pos`  
 A posição do bit no bitset a ser testado quanto ao seu valor.  
  
### <a name="return-value"></a>Valor de retorno  
 **true** se o bit especificado pela posição de argumento estiver definido como 1, caso contrário, **false**.  
  
### <a name="remarks"></a>Comentários  
 A função membro gera um [out_of_range](../standard-library/out-of-range-class.md)

