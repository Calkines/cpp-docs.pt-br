---
title: Classe cancellation_token_registration | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
caps.latest.revision: 9
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 1dd55aff292926b930271257bda583a2f93aba92
ms.lasthandoff: 03/17/2017

---
# <a name="cancellationtokenregistration-class"></a>Classe cancellation_token_registration
O `cancellation_token_registration` classe representa uma notificação de retorno de chamada de um `cancellation_token`. Quando o `register` método em uma `cancellation_token` é usado para receber notificação quando ocorre o cancelamento, uma `cancellation_token_registration` objeto é retornado como um identificador para o retorno de chamada para que o chamador pode solicitar um retorno de chamada específico não ser feitas por meio do uso do `deregister` método.  
  
## <a name="syntax"></a>Sintaxe  
  
```
class cancellation_token_registration;
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[cancellation_token_registration](#ctor)||  
|[~ cancellation_token_registration destruidor](#dtor)||  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[operator!=](#operator_neq)||  
|[operator=](#operator_eq)||  
|[operator==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 `cancellation_token_registration`  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** pplcancellation_token.h  
  
 **Namespace:** simultaneidade  
  
##  <a name="dtor"></a>~ cancellation_token_registration 

```
~cancellation_token_registration();
```  
  
##  <a name="ctor"></a>cancellation_token_registration 

```
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Src`  
  
##  <a name="operator_neq"></a>operador! = 

```
bool operator!= (const cancellation_token_registration& _Rhs) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Rhs`  
  
### <a name="return-value"></a>Valor de retorno  
  
##  <a name="operator_eq"></a>operador = 

```
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Src`  
  
### <a name="return-value"></a>Valor de retorno  
  
##  <a name="operator_eq_eq"></a>operador = = 

```
bool operator== (const cancellation_token_registration& _Rhs) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Rhs`  
  
### <a name="return-value"></a>Valor de retorno  
  
## <a name="see-also"></a>Consulte também  
 [Namespace de simultaneidade](concurrency-namespace.md)
