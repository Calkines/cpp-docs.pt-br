---
title: '&lt;lista&gt; funções | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269018"
---
# <a name="ltlistgt-functions"></a>&lt;lista&gt; funções

## <a name="swap"></a> troca

Troca os elementos das duas listas.

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>Parâmetros

*À esquerda*\
Um objeto do tipo `list`.

*Certo*\
Um objeto do tipo `list`.

### <a name="remarks"></a>Comentários

Esta função de modelo executa `left.swap(right)`.
