---
title: Classe Platform::Collections::MapView | Microsoft Docs
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
dev_langs:
- C++
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f55a980f0d4fcb6982adb4d40353a47ee2f4d120
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="platformcollectionsmapview-class"></a>Classe Platform::Collections::MapView
Representa uma exibição somente leitura em um *mapa*, que é uma coleção de pares chave-valor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = ::std::less<K>>  
ref class MapView sealed;  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `K`  
 O tipo de chave em pares chave-valor.  
  
 `V`  
 O tipo de valor em pares chave-valor.  
  
 `C`  
 Um tipo que fornece um objeto de função que pode comparar dois valores de elemento como chaves de classificação para determinar sua ordem relativa em MapView. Por padrão, [STD\<K >](../standard-library/less-struct.md).  
  
### <a name="remarks"></a>Comentários  
 MapView é uma implementação concreta de C++ do [Windows::Foundation::Collections::IMapView \<K, V >](http://go.microsoft.com/fwlink/p/?LinkId=262409) interface que é transmitida pela interface binária de aplicativo (ABI). Para obter mais informações, consulte [Coleções (C++/CX)](../cppcx/collections-c-cx.md).  
  
### <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[MapView::MapView](#ctor)|Inicializa uma nova instância da classe MapView.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[MapView::First](#first)|Retorna um iterador que é inicializado para o primeiro elemento na exibição do mapa.|  
|[MapView::HasKey](#haskey)|Determina se o MapView atual contém a chave especificada.|  
|[MapView::Lookup](#lookup)|Recupera o elemento na chave especificada no objeto MapView atual.|  
|[MapView::Size](#size)|Retorna o número de elementos no objeto MapView atual.|  
|[MapView::Split](#split)|Divide um objeto MapView original em dois objetos MapView.|  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 `MapView`  
  
### <a name="requirements"></a>Requisitos  
 **Cabeçalho:** collection.h  
  
 **Namespace:** Platform::Collections  


## <a name="first"></a> Método Mapview:
Retorna um iterador que especifica o primeiro elemento na exibição de mapa.  
  
### <a name="syntax"></a>Sintaxe  
  
```    
virtual Windows::Foundation::Collections::IIterator<  
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um iterador que especifica o primeiro elemento na exibição do mapa.  
  
### <a name="remarks"></a>Comentários  
 Uma maneira conveniente de manter o iterador retornado por First () é atribuir o valor de retorno a uma variável que é declarada com o **automática** palavra-chave de dedução de tipo. Por exemplo, `auto x = myMapView->First();`.  
  


## <a name="haskey"></a>  Método: Haskey
Determina se o MapView atual contém a chave especificada.  
  
### <a name="syntax"></a>Sintaxe  
  
```  
  
bool HasKey(K key);  
```  
  
### <a name="parameters"></a>Parâmetros  
 `key`  
 A chave usada para localizar o elemento MapView. O tipo de `key` é o typename *K*.  
  
### <a name="return-value"></a>Valor de retorno  
 `true` se a chave for encontrada; caso contrário, `false`.  
  


##  <a name="lookup"></a> Método Mapview:
Recupera o valor do tipo V que está associado à chave especificada do tipo K.  
  
### <a name="syntax"></a>Sintaxe  
  
```  
V Lookup(K key);  
```  
  
### <a name="parameters"></a>Parâmetros  
 `key`  
 A chave usada para localizar um elemento em MapView. O tipo de `key` é o typename *K*.  
  
### <a name="return-value"></a>Valor de retorno  
 O valor que é emparelhado com `key`. O tipo do valor de retorno é typename *V*.  
  


##  <a name="ctor"></a> Construtor mapview:: Mapview
Inicializa uma nova instância da classe MapView.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp  
explicit MapView(const C& comp = C());  
  
explicit MapView(const ::std::map<K, V, C>& m);  
  
explicit MapView(std::map<K, V, C>&& m);  
  
template <typename InIt> MapView(  
    InIt first,  
    InIt last,  
    const C& comp = C());  
  
MapView(
    ::std::initializer_list<std::pair<const K, V>> il,  
    const C& comp = C());  
```  
  
### <a name="parameters"></a>Parâmetros  
 `InIt`  
 O typename de MapView atual.  
  
 `comp`  
 Um objeto de função que pode comparar dois valores de elemento como chaves de classificação para determinar sua ordem relativa em MapView.  
  
 `m`  
 Uma referência ou [Lvalues e Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) para um `map Class` que é usado para inicializar o MapView atual.  
  
 `first`  
 O iterador de entrada do primeiro elemento em um intervalo de elementos usados para inicializar o MapView atual.  
  
 `last`  
 O iterador de entrada do primeiro elemento após um intervalo de elementos usados para inicializar o MapView atual.  
  
 il  
 Um [std:: initializer_list < STD\<K, V >>](../standard-library/initializer-list-class.md) cujos elementos serão inseridos em MapView.  



##  <a name="size"></a> Método Mapview:
Retorna o número de elementos no objeto MapView atual.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp  
  
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 O número de elementos no MapView atual.  
  


##  <a name="split"></a> Método Mapview:
Divide o objeto MapView atual em dois objetos MapView. Este método é não operacional.  
  
### <a name="syntax"></a>Sintaxe  
  
```  
void Split(  
   Windows::Foundation::Collections::IMapView<  
                         K, V>^ * firstPartition,  
   Windows::Foundation::Collections::IMapView<  
                         K, V>^ * secondPartition);  
```  
  
### <a name="parameters"></a>Parâmetros  
 `firstPartition`  
 A primeira parte do objeto MapView original.  
  
 `secondPartition`  
 A segunda parte do objeto MapView original.  
  
### <a name="remarks"></a>Comentários  
 Este método não está operacional; ele não faz nada.  
    
## <a name="see-also"></a>Consulte também  
 [Namespace de plataforma](platform-namespace-c-cx.md)