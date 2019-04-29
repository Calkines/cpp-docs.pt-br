---
title: noexcept (C++)
ms.date: 01/12/2018
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: c314b554abb6c10e62b143f554777af50267e4e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245355"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C++11:** Especifica se uma função pode gerar exceções.

## <a name="syntax"></a>Sintaxe

> *noexcept-expression*: &nbsp;&nbsp;&nbsp;&nbsp;**noexcept** &nbsp;&nbsp;&nbsp;&nbsp;**noexcept(** *constant-expression* **)**

### <a name="parameters"></a>Parâmetros

*constant-expression*<br/>
Uma expressão constante do tipo **bool** que representa se o conjunto de possíveis tipos de exceção está vazio. A versão incondicional é equivalente a `noexcept(true)`.

## <a name="remarks"></a>Comentários

Um *expressão noexcept* é um tipo de *especificação de exceção*, um sufixo para uma declaração de função que representa um conjunto de tipos que podem ser correspondidos por um manipulador de exceção para qualquer exceção que sai de um função. Operador condicional unário `noexcept(` *constant_expression* `)` onde *constant_expression* yeilds **true**e seu sinônimo incondicional **noexcept**, especificar que o conjunto de possíveis tipos de exceção que pode sair de uma função está vazio. Ou seja, a função nunca gera uma exceção e nunca permite que uma exceção ser propagado fora de seu escopo. O operador `noexcept(` *constant_expression* `)` onde *constant_expression* yeilds **false**, ou a ausência de uma especificação de exceção (além de uma função de destruidor ou desalocação), indica que o conjunto de exceções possíveis que podem sair a função é o conjunto de todos os tipos.

Marca uma função como **noexcept** somente se todas as funções que ele chama, direta ou indiretamente, também são **noexcept** ou **const**. O compilador não verifica cada caminho de código para exceções que podem ser emergem até necessariamente uma **noexcept** função. Se uma exceção sair do escopo externo de uma função marcada `noexcept`, [std:: Terminate](../standard-library/exception-functions.md#terminate) é invocada imediatamente, e não há nenhuma garantia de que os destruidores de todos os objetos no escopo serão invocados. Use **noexcept** em vez do especificador de exceção dinâmica `throw()`, que agora está obsoleto no padrão. É recomendável que você aplique `noexcept` para qualquer função que nunca permite que uma exceção propagar a pilha de chamadas. Quando uma função é declarada **noexcept**, ele permite que o compilador gere um código mais eficiente em vários contextos diferentes. Para obter mais informações, consulte [especificações de exceção](exception-specifications-throw-cpp.md).

## <a name="example"></a>Exemplo

Pode ser declarado como uma função de modelo que copia seu argumento **noexcept** a condição de que o objeto que está sendo copiado é um tipo de dados antigo simples (POD). Tal função pode ser declarada como este:

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>Consulte também

[Tratamento de exceções em C++](cpp-exception-handling.md)<br/>
[Especificações de exceção (lançar, noexcept)](exception-specifications-throw-cpp.md)