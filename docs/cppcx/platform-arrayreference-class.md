---
title: Classe MTAThreadAttribute | Microsoft Docs
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
dev_langs:
- C++
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0987511b6653bee85b6cc5c4c680331d12519450
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="platformarrayreference-class"></a>Classe Platform::ArrayReference
`ArrayReference` é um tipo de otimização que você pode substituir por [Platform::Array^](../cppcx/platform-array-class.md) em parâmetros de entrada quando você deseja preencher uma matriz de estilo C com os dados de entrada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
class ArrayReference  
```
  
### <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[ArrayReference::ArrayReference](#ctor)|Inicializa uma nova instância da classe `ArrayReference`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Operador ArrayReference::operator()](#operator-call)|Converte essa `ArrayReference` em uma `Platform::Array<T>^*`.|  
|[Operador ArrayReference::operator=](#operator-assign)|Atribui o conteúdo de outra `ArrayReference` a essa instância.|  
  
## <a name="exceptions"></a>Exceções  
  
### <a name="remarks"></a>Comentários  
 Usando `ArrayReference` para preencher uma matriz de estilo C, você evita a operação de cópia adicional que estaria envolvida ao copiar primeiramente em uma variável `Platform::Array` e, em seguida, na matriz de estilo C. Quando você usa `ArrayReference`, há apenas uma operação de cópia. Para obter um exemplo de código, consulte [matriz e WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
### <a name="requirements"></a>Requisitos  
 **Suporte mínimo de cliente:** Windows 8  
  
 **Suporte mínimo de servidor:** Windows Server 2012  
  
 **Namespace:** Platform  
  
 **Cabeçalho:** vccorlib.h  
  
## <a name="ctor"></a>  Construtor arrayreference:: Arrayreference
Inicializa uma nova instância do [arrayreference](../cppcx/platform-arrayreference-class.md) classe.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp  
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);  
ArrayReference(ArrayReference&& otherArg)  
  
```  
  
### <a name="parameters"></a>Parâmetros  
 `dataArg`  
 Ponteiro para os dados de matriz.  
  
 `sizeArg`  
 O número de elementos na matriz de origem.  
  
 `otherArg`  
 Objeto `ArrayReference` cujos dados serão movidos para inicializar a nova instância.  
  
### <a name="remarks"></a>Comentários  
  


## <a name="operator-assign"></a>  Arrayreference:: Operator operador =
Atribui o objeto especificado ao atual [arrayreference](../cppcx/platform-arrayreference-class.md) objeto usando a semântica de animação.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp  
  
ArrayReference& operator=(ArrayReference&& otherArg);  
  
```  
  
### <a name="parameters"></a>Parâmetros  
 `otherArg`  
 O objeto que é movido para o objeto `ArrayReference` atual.  
  
### <a name="return-value"></a>Valor de retorno  
 Referência a um objeto do tipo `ArrayReference`.  
  
### <a name="remarks"></a>Comentários  
 `Platform::ArrayReference` é um modelo de classe C++ padrão, não uma classe de referência.  
  


## <a name="operator-call"></a>  Operador Arrayreference
Converte atual [arrayreference](../cppcx/platform-arrayreference-class.md) do objeto para um [Platform:: array](../cppcx/platform-array-class.md) classe.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp  
  
Array<TArg>^ operator ();  
  
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um identificador para um objeto do tipo `Array<TArg>^`  
  
### <a name="remarks"></a>Comentários  
 [Arrayreference](../cppcx/platform-arrayreference-class.md) e [Platform:: array](../cppcx/platform-array-class.md) são modelos de classe C++ padrão, não ref classes.  
  


  
  
## <a name="see-also"></a>Consulte também  
 [Namespace de plataforma](../cppcx/platform-namespace-c-cx.md)