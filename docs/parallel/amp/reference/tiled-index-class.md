---
title: Classe tiled_index | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tiled_index
- AMP/tiled_index
- AMP/Concurrency::tiled_index::tiled_index
- AMP/Concurrency::tiled_index::get_tile_extent
- AMP/Concurrency::tiled_index::barrier
- AMP/Concurrency::tiled_index::global
- AMP/Concurrency::tiled_index::local
- AMP/Concurrency::tiled_index::rank
- AMP/Concurrency::tiled_index::tile
- AMP/Concurrency::tiled_index::tile_dim0
- AMP/Concurrency::tiled_index::tile_dim1
- AMP/Concurrency::tiled_index::tile_dim2
- AMP/Concurrency::tiled_index::tile_origin
- AMP/Concurrency::tiled_index::tile_extent
dev_langs:
- C++
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 3a436635b456bd196a863ac5e9e8a5c10b679644
ms.openlocfilehash: ed5c024e47eb8a822115822ae83e0e02fd8cf111
ms.lasthandoff: 04/21/2017

---
# <a name="tiledindex-class"></a>Classe tiled_index
Fornece um índice em uma [tiled_extent](tiled-extent-class.md) objeto. Essa classe tem propriedades para acessar elementos relativo à origem do bloco local e relativo à origem global. Para obter mais informações sobre os espaços de lado a lado, consulte [usando blocos](../../../parallel/amp/using-tiles.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
template <
    int _Dim0,  
    int _Dim1 = 0,  
    int _Dim2 = 0  
>  
class tiled_index : public _Tiled_index_base<3>;  
 
template <
    int _Dim0,  
    int _Dim1  
>  
class tiled_index<_Dim0, _Dim1, 0> : public _Tiled_index_base<2>;  
 
template <
    int _Dim0  
>  
class tiled_index<_Dim0, 0, 0> : public _Tiled_index_base<1>;  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `_Dim0`  
 O comprimento da dimensão mais significativo.  
  
 `_Dim1`  
 O comprimento da dimensão próximo ao mais significativo.  
  
 `_Dim2`  
 O comprimento da dimensão menos significativo.  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Construtor de tiled_index](#ctor)|Inicializa uma nova instância da classe `tile_index`.|  

  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[get_tile_extent](#tiled_index__get_tile_extent)|Retorna um [extensão](extent-class.md) objeto que tem os valores de `tiled_index` argumentos de modelo `_Dim0`, `_Dim1`, e `_Dim2`.|  


  
### <a name="public-constants"></a>Constantes públicas  
  
|Nome|Descrição|  
|----------|-----------------|  
|[barreira constante](#tiled_index__barrier)|Armazena um [tile_barrier](tile-barrier-class.md) objeto que representa uma barreira no bloco atual de threads.|  
|||  
|[Constante global](#tiled_index__global)|Armazena um [índice](index-class.md) objeto do índice de classificação 1, 2 ou 3 que representa global em um [grade](http://msdn.microsoft.com/en-us/f7d1b6a6-586c-4345-b09a-bfc26c492cb0) objeto.|  
|[Constante local](#tiled_index__local)|Armazena um `index` o objeto de índice de classificação 1, 2 ou 3 que representa o relativo no bloco atual de um [tiled_extent](tiled-extent-class.md) objeto.|  
|[Constante de classificação](#tiled_index__rank)|Armazena a classificação do `tiled_index` objeto.|  
|[Constante Tile](#tiled_index__tile)|Armazena um `index` objeto de classificação 1, 2 ou 3 que representa as coordenadas do bloco atual de um `tiled_extent` objeto.|  
|[Constante tile_dim0](#tiled_index__tile_dim0)|Armazena o comprimento da dimensão mais significativo.|  
|[Constante tile_dim1](#tiled_index__tile_dim1)|Armazena o comprimento da dimensão próximo ao mais significativo.|  
|[Constante tile_dim2](#tiled_index__tile_dim2)|Armazena o comprimento da dimensão menos significativo.|  
|[Constante de tile_origin](#tiled_index__tile_origin)|Armazena um `index` objeto de coordenadas de classificação 1, 2 ou 3 que representa global da origem do bloco atual em um `tiled_extent` objeto.|  

  
### <a name="public-data-members"></a>Membros de Dados Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[tile_extent](#tile_extent)|Obtém um [extensão](extent-class.md) objeto que tem os valores a `tiled_index` argumentos de template `tiled_index` argumentos de template `_Dim0`, `_Dim1`, e `_Dim2`.|  

  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 `_Tiled_index_base`  
  
 `tiled_index`  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** amp.h  
  
 **Namespace:** Simultaneidade  


## <a name="tiled_index__ctor"></a>Construtor de tiled_index  
Inicializa uma nova instância da classe `tiled_index`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
tiled_index(  
    const index<rank>& _Global,  
    const index<rank>& _Local,  
    const index<rank>& _Tile,  
    const index<rank>& _Tile_origin,  
    const tile_barrier& _Barrier ) restrict(amp,cpu);  
  
tiled_index(  
    const tiled_index& _Other ) restrict(amp,cpu);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `_Global`  
 Global [índice](index-class.md) da construído `tiled_index`.  
  
 `_Local`  
 Local [índice](index-class.md) do construído`tiled_index`  
  
 `_Tile`  
 O bloco [índice](index-class.md) do construído`tiled_index`  
  
 `_Tile_origin`  
 A origem de bloco [índice](index-class.md) do construído`tiled_index`  
  
 `_Barrier`  
 O [tile_barrier](tile-barrier-class.md) objeto o construído `tiled_index`.  
  
 `_Other`  
 O `tile_index` objeto a ser copiado para o construído `tiled_index`.  
  
## <a name="overloads"></a>Sobrecargas  
  
|||  
|-|-|  
|Nome|Descrição|  
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Inicializa uma nova instância do `tile_index` classe do índice de bloco em coordenadas global e a posição relativa em bloco em coordenadas de locais. O `_Global` e `_Tile_origin` parâmetros são computados.|  
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Inicializa uma nova instância do `tile_index` classe copiando especificado `tiled_index` objeto.|  


## <a name="tiled_index__get_tile_extent"></a>get_tile_extent
Retorna um [extensão](extent-class.md) objeto que tem os valores de `tiled_index` argumentos de modelo `_Dim0`, `_Dim1`, e `_Dim2`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
extent<rank> get_tile_extent()restrict(amp,cpu);  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Um `extent` objeto que tem os valores de `tiled_index` argumentos de template `_Dim0`, `_Dim1`, e `_Dim2`.  

## <a name="tiled_index__barrier"></a>barreira   
Armazena um [tile_barrier](tile-barrier-class.md) objeto que representa uma barreira no bloco atual de threads.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
const tile_barrier barrier;  
```  

## <a name="tiled_index__global"></a>global   
Armazena um [índice](index-class.md) objeto de classificação 1, 2 ou 3, que representa o índice global de um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
const index<rank> global;  
```  
  
## <a name="tiled_index__local"></a>local   
Armazena um [índice](index-class.md) o objeto de índice de classificação 1, 2 ou 3 que representa o relativo no bloco atual de um [tiled_extent](tiled-extent-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
const index<rank> local;  
```  
  
## <a name="tiled_index__rank"></a>classificação   
Armazena a classificação do `tiled_index` objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
static const int rank = _Rank;  
```  

## <a name="tiled_index__tile"></a>lado a lado   
Armazena um [índice](index-class.md) objeto de classificação 1, 2 ou 3 que representa as coordenadas do bloco atual de um [tiled_extent](tiled-extent-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
const index<rank> tile;  
```  
  
## <a name="tiled_index__tile_dim0"></a>tile_dim0  
Armazena o comprimento da dimensão mais significativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
static const int tile_dim0 = _Dim0;  
```  
   
## <a name="tiled_index__tile_dim1"></a>tile_dim1   
Armazena o comprimento da dimensão próximo ao mais significativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="tiled_index__tile_dim2"></a>tile_dim2   
Armazena o comprimento da dimensão menos significativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="tiled_index__tile_origin"></a>tile_origin   
Armazena um [índice](index-class.md) objeto de coordenadas de classificação 1, 2 ou 3 que representa global da origem do bloco atual dentro de um [tiled_extent](tiled-extent-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
const index<rank> tile_origin  
```  
## <a name="tile_extent"></a>tile_extent
  Obtém um [extensão](extent-class.md) objeto que tem os valores a `tiled_index` argumentos de template `tiled_index` argumentos de template `_Dim0`, `_Dim1`, e `_Dim2`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;  
```  
  
## <a name="see-also"></a>Consulte também  
 [Namespace de simultaneidade (C++ AMP)](concurrency-namespace-cpp-amp.md)
