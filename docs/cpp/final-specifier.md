---
title: especificador final
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: c6400c8060664713fdd004a5aa9536e0617bc0c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588078"
---
# <a name="final-specifier"></a>especificador final

Você pode usar o **final** palavra-chave para designar funções virtuais que não podem ser substituídas em uma classe derivada. Também é possível usá-la para designar classes que não podem ser herdadas.

## <a name="syntax"></a>Sintaxe

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>Comentários

**final** é contextual e tem um significado especial somente quando ele é usado após uma declaração de função ou nome de classe; caso contrário, ele não é uma palavra-chave reservada.

Quando **final** é usado em declarações de classe, `base-classes` é uma parte opcional da declaração.

## <a name="example"></a>Exemplo

O exemplo a seguir usa o **final** palavra-chave para especificar que uma função virtual não pode ser substituída.

```cpp
class BaseClass
{
    virtual void func() final;
};

class DerivedClass: public BaseClass
{
    virtual void func(); // compiler error: attempting to
                         // override a final function
};
```

Para obter informações sobre como especificar que as funções de membro podem ser substituídas, consulte [especificador de substituição](../cpp/override-specifier.md).

O próximo exemplo usa o **final** palavra-chave para especificar que uma classe não pode ser herdada.

```cpp
class BaseClass final
{
};

class DerivedClass: public BaseClass // compiler error: BaseClass is
                                     // marked as non-inheritable
{
};
```

## <a name="see-also"></a>Consulte também

[Palavras-chave](../cpp/keywords-cpp.md)<br/>
[Especificador override](../cpp/override-specifier.md)