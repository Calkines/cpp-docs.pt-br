---
title: Classe enable_shared_from_this
ms.date: 11/04/2016
f1_keywords:
- memory/std::enable_shared_from_this
helpviewer_keywords:
- enable_shared_from_this class
- enable_shared_from_this
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
ms.openlocfilehash: 152a5e0433f2eab5160fbdedde8f18f42f2303e6
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245859"
---
# <a name="enablesharedfromthis-class"></a>Classe enable_shared_from_this

Ajuda a gerar um `shared_ptr`.

## <a name="syntax"></a>Sintaxe

```cpp
class enable_shared_from_this {
public:
    shared_ptr<Ty>
        shared_from_this();
    shared_ptr<const Ty> shared_from_this() const;
    weak_ptr<T> weak_from_this() noexcept;
    weak_ptr<T const> weak_from_this() const noexcept;
protected:
    enable_shared_from_this();
    enable_shared_from_this(const enable_shared_from_this&);
    enable_shared_from_this& operator=(const enable_shared_from_this&);
    ~enable_shared_from_this();
};
```

### <a name="parameters"></a>Parâmetros

*Ty*\
O tipo controlado pelo ponteiro compartilhado.

## <a name="remarks"></a>Comentários

Os objetos derivados de `enable_shared_from_this` podem usar os métodos `shared_from_this` nas funções de membro para criar proprietários de instância [shared_ptr](../standard-library/shared-ptr-class.md) que compartilham a propriedade com proprietários `shared_ptr` existentes. Caso contrário, se você criar um novo `shared_ptr` por meio **isso**, ele é diferente do existente `shared_ptr` proprietários, que podem levar a referências inválidas ou fazer com que o objeto seja excluído mais de uma vez.

Os construtores, o destruidor e o operador de atribuição são protegidos para evitar o uso indevido acidental. O tipo de argumento de modelo *Ty* deve ser do tipo da classe derivada.

Para obter um exemplo de uso, consulte [enable_shared_from_this::shared_from_this](#shared_from_this).

## <a name="shared_from_this"></a> shared_from_this

Gera um `shared_ptr` que compartilha a propriedade da instância com proprietários `shared_ptr` existentes.

```cpp
shared_ptr<T> shared_from_this();
shared_ptr<const T> shared_from_this() const;
```

### <a name="remarks"></a>Comentários

Quando você deriva objetos da classe base `enable_shared_from_this`, as funções de membro de modelo `shared_from_this` retornam um objeto de [Classe shared_ptr](../standard-library/shared-ptr-class.md) que compartilha a propriedade dessa instância com os proprietários `shared_ptr` existentes. Caso contrário, se você criar um novo `shared_ptr` partir **isso**, ele é diferente do existente `shared_ptr` proprietários, que podem levar a referências inválidas ou fazer com que o objeto seja excluído mais de uma vez. O comportamento será indefinido se você chamar `shared_from_this` em uma instância que já não pertence a um objeto `shared_ptr`.

### <a name="example"></a>Exemplo

```cpp
// std_memory_shared_from_this.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

struct base : public std::enable_shared_from_this<base>
{
    int val;
    shared_ptr<base> share_more()
    {
        return shared_from_this();
    }
};

int main()
{
    auto sp1 = make_shared<base>();
    auto sp2 = sp1->share_more();

    sp1->val = 3;
    cout << "sp2->val == " << sp2->val << endl;
    return 0;
}
```

```Output
sp2->val == 3
```

## <a name="weak_from_this"></a> weak_from_this

```cpp
weak_ptr<T> weak_from_this() noexcept;
weak_ptr<T const> weak_from_this() const noexcept;
```
