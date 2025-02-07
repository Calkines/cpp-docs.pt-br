---
title: Operadores &lt;ostream&gt;
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: c80abcb08423b4bb269e7d60ac43ef97d197a0e9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453531"
---
# <a name="ltostreamgt-operators"></a>Operadores &lt;ostream&gt;

||
|-|
|[operator&lt;&lt;](#op_lt_lt)|

## <a name="op_lt_lt"></a>  operator&lt;&lt;

Grava vários tipos no fluxo.

```cpp
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```

### <a name="parameters"></a>Parâmetros

*_Ch*\
Um caractere.

*_Elem*\
O tipo de elemento.

*_Ostr*\
Um objeto `basic_ostream`.

*Str*\
Uma cadeia de caracteres.

*_Tr*\
Características de caractere.

*Val*\
O tipo

### <a name="return-value"></a>Valor de retorno

O fluxo.

### <a name="remarks"></a>Comentários

A classe `basic_ostream` também define vários operadores de inserção. Para obter mais informações, consulte [basic_ostream::operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

A função do modelo

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

determina o comprimento N = `traits_type::` [comprimento](../standard-library/char-traits-struct.md#length)(`str`) da sequência que começa em *Str*e insere a sequência. Se N < `_Ostr.`[width](../standard-library/ios-base-class.md#width), a função também insere uma repetição de `_Ostr.width` - N caracteres de preenchimento. A repetição precede a sequência se (`_Ostr`. [flags](../standard-library/ios-base-class.md#flags) & `adjustfield` != [left](../standard-library/ios-functions.md#left). Caso contrário, a repetição segue a sequência. A função retorna *_Ostr*.

A função do modelo

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

insere o elemento `_Ch`. Se 1 < `_Ostr.width`, a função também insere uma repetição de `_Ostr.width` - 1 caracteres de preenchimento. A repetição precede a sequência se `_Ostr.flags & adjustfield != left`. Caso contrário, a repetição segue a sequência. Ele retorna *_Ostr*.

A função do modelo

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```

comporta-se da mesma forma que

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

Exceto que cada elemento *_Ch* da sequência que começa em *Str* é convertido em um objeto do tipo `Elem` chamando `_Ostr.` [Put](../standard-library/basic-ostream-class.md#put)(`_Ostr.`[ampliação](../standard-library/basic-ios-class.md#widen)(`_Ch`)).

A função do modelo

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

comporta-se da mesma forma que

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

Exceto que *_Ch* é convertido em um objeto do tipo `Elem` chamando `_Ostr.put`( `_Ostr.widen`( `_Ch`)).

A função do modelo

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

comporta-se da mesma forma que

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

(Ele não precisa ampliar os elementos antes de inseri-los.)

A função do modelo

```cpp
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```

comporta-se da mesma forma que

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

(Não é necessário ampliar o *_Ch* antes de inseri-lo.)

A função do modelo

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

retorna `_Ostr` < < (`const char *`) `str`.

A função do modelo

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

retorna `_Ostr` < < (`char`) `_Ch`.

A função de modelo:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

retorna `_Ostr` < < (`const char *`) `str`.

A função de modelo:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

retorna `_Ostr` < < (`char`) `_Ch`.

A função de modelo:

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

retorna `_Ostr` `<<` `val` (e converte um [RValue Reference](../cpp/rvalue-reference-declarator-amp-amp.md) para `_Ostr` para um lvalue no processo).

### <a name="example"></a>Exemplo

Consulte [flush](../standard-library/ostream-functions.md#flush) para ver um exemplo usando `operator<<`.

## <a name="see-also"></a>Consulte também

[\<ostream>](../standard-library/ostream.md)
