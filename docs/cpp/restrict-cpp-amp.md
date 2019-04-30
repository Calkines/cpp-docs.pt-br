---
title: restrita (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: 3609e3f0541cfd8a8af8559d8d49e6a77c00d91c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403380"
---
# <a name="restrict-c-amp"></a>restrita (C++ AMP)

O especificador de restrição pode ser aplicado a declarações de função e lambda. Impõe restrições no código na função e no comportamento da função em aplicativos que usam o tempo de execução do C++ Accelerated Massive Parallelism(AMP C++).

> [!NOTE]
>  Para obter informações sobre o **restringir** palavra-chave que faz parte do **declspec** atributos de classe de armazenamento, consulte [restringir](../cpp/restrict.md).

O **restringir** cláusula usa os seguintes formulários:

|Cláusula|Descrição|
|------------|-----------------|
|`restrict(cpu)`|A função pode usar a linguagem C++ completa. Somente outras funções que são declaradas usando as funções restrict(cpu) podem chamar a função.|
|`restrict(amp)`|A função só pode usar o subconjunto da linguagem C++ que o AMP C++ pode acelerar.|
|Uma sequência de `restrict(cpu)` e `restrict(amp)`.|A função deve atender às limitações de `restrict(cpu)` e `restrict(amp)`. A função pode ser chamada por funções que são declaradas usando `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` ou `restrict(amp, cpu)`.<br /><br /> A forma `restrict(A) restrict(B)` pode ser escrita como `restrict(A,B)`.|

## <a name="remarks"></a>Comentários

O **restringir** palavra-chave é uma palavra-chave contextual. Os especificadores de restrição `cpu` e `amp` não são palavras reservadas. A lista de especificadores não é extensível. Uma função que não tem um **restringir** cláusula é o mesmo que uma função que tem o `restrict(cpu)` cláusula.

Uma função que tem a cláusula `restrict(amp)` tem as seguintes limitações:

- A função só pode chamar funções que tenham a cláusula `restrict(amp)`.

- A função deve ser embutível.

- A função pode declarar somente **int**, **unsigned int**, **float**, e **double** variáveis e as classes e estruturas que contêm apenas Esses tipos. **bool** também é permitido, mas ele deve ser alinhado com 4 bytes se você usá-lo em um tipo composto.

- As funções lambda não podem capturar por referência nem capturar os ponteiros.

- As referências e ponteiros de indireção única só têm suporte como variáveis locais, argumentos de função e tipos de retorno.

- Os seguintes não são permitidos:

   - Recursão.

   - Variáveis declaradas com o [volátil](../cpp/volatile-cpp.md) palavra-chave.

   - Funções virtuais.

   - Ponteiros para funções.

   - Ponteiros para funções de membro.

   - Ponteiros em estruturas.

   - Ponteiros para ponteiros.

   - **GoTo** instruções.

   - Instruções rotuladas.

   - **tente**, **catch**, ou **throw** instruções.

   - Variáveis globais.

   - Variáveis estáticas. Use [palavra-chave tile_static](../cpp/tile-static-keyword.md) em vez disso.

   - **dynamic_cast** conversões.

   - O **typeid** operador.

   - Declarações asm.

   - Varargs.

Para uma discussão sobre limitações da função, consulte [restringir restrições (amp)](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/12/19/restrictamp-restrictions-part-0-of-n-introduction/).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar o `restrict(amp)`cláusula.

```cpp
void functionAmp() restrict(amp) {}
void functionNonAmp() {}

void callFunctions() restrict(amp)
{
    // int is allowed.
    int x;
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.
    // long long int y;

    // Calling an amp-restricted function is allowed.
    functionAmp();

    // Calling a non-amp-restricted function is not allowed.
    // functionNonAmp();
}
```

## <a name="see-also"></a>Consulte também

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)