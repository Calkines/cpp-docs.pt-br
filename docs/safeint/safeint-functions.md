---
title: Funções (SafeInt)
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt functions
- SafeAdd
- SafeCast
- SafeDivide
- SafeEquals
- SafeGreaterThan
- SafeGreaterThanEquals
- SafeLessThan
- SafeLessThanEquals
- SafeModulus
- SafeMultiply
- SafeNotEquals
- SafeSubtract
helpviewer_keywords:
- functions, SafeInt
- SafeAdd function
- SafeCast function
- SafeDivide function
- SafeEquals function
- SafeGreaterThan function
- SafeGreaterThanEquals function
- SafeLessThan function
- SafeLessThanEquals function
- SafeModulus function
- SafeMultiply function
- SafeNotEquals function
- SafeSubtract function
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
ms.openlocfilehash: e31cf35c903a0e7572ce7d47ada21c4603119cb2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515571"
---
# <a name="safeint-functions"></a>Funções (SafeInt)

A biblioteca SafeInt fornece várias funções que você pode usar sem criar uma instância da classe [SafeInt](../safeint/safeint-class.md). Se quiser proteger uma única operação matemática contra estouros de inteiro, você pode usar essas funções. Se quiser proteger várias operações matemáticas, você deve criar objetos `SafeInt`. É mais eficiente criar objetos `SafeInt` do que usar essas funções várias vezes.

Essas funções permitem comparar ou realizar operações matemáticas em dois tipos diferentes de parâmetros sem antes precisar convertê-los no mesmo tipo.

Cada uma dessas funções tem dois tipos de modelo: `T` e `U`. Cada um desses tipos pode ser um tipo booliano, caractere ou integral. Tipos integrais podem ser assinados ou não assinados e ter qualquer tamanho de 8 a 64 bits.

> [!NOTE]
> A última versão dessa biblioteca está localizada em [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt).

## <a name="in-this-section"></a>Nesta seção

Função                      | Descrição
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | Adiciona dois números e protege contra estouros.
[SafeCast](#safecast)         | Converte um tipo de parâmetro em outro tipo.
[SafeDivide](#safedivide)     | Divide dois números e protege contra a divisão por zero.
[SafeEquals](#safeequals), [SafeGreaterThan](#safegreaterthan), [SafeGreaterThanEquals](#safegreaterthanequals), [SafeLessThan](#safelessthan), [SafeLessThanEquals](#safelessthanequals), [SafeNotEquals](#safenotequals) | Compara dois números. Essas funções permitem comparar dois tipos diferentes de números sem alterar seus tipos.
[SafeModulus](#safemodulus)   | Realiza a operação de módulo em dois números.
[SafeMultiply](#safemultiply) | Multiplica dois números juntos e protege contra estouros.
[SafeSubtract](#safesubtract) | Subtrai dois números e protege contra estouros.

## <a name="related-sections"></a>Seções relacionadas

Seção                                                  | Descrição
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](../safeint/safeint-class.md)                   | A classe `SafeInt`.
[SafeIntException](../safeint/safeintexception-class.md) | A classe de exceção específica da biblioteca SafeInt.

## <a name="safeadd"></a>SafeAdd

Adiciona dois números de uma maneira que protege contra estouros.

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parâmetros

*t*<br/>
[in] O primeiro número a adicionar. Deve ser do tipo T.

*u*<br/>
[in] O segundo número a adicionar. Deve ser do tipo U.

*resultado*<br/>
[out] O parâmetro em que `SafeAdd` armazena o resultado.

### <a name="return-value"></a>Valor de retorno

**true** se nenhum erro ocorrer; **false** se ocorrer um erro.

## <a name="safecast"></a>SafeCast

Converte um tipo de número em outro tipo.

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Parâmetros

*From*<br/>
[in] O número de origem para converter. Deve ser do tipo `T`.

*To*<br/>
[out] Uma referência ao novo tipo de número. Deve ser do tipo `U`.

### <a name="return-value"></a>Valor de retorno

**true** se nenhum erro ocorrer; **false** se ocorrer um erro.

## <a name="safedivide"></a>SafeDivide

Divide dois números de uma maneira que protege contra a divisão por zero.

```cpp
template<typename T, typename U>
inline bool SafeDivide (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parâmetros

*t*<br/>
[in] O divisor. Deve ser do tipo T.

*u*<br/>
[in] O dividendo. Deve ser do tipo U.

*resultado*<br/>
[out] O parâmetro em que `SafeDivide` armazena o resultado.

### <a name="return-value"></a>Valor de retorno

**true** se nenhum erro ocorrer; **false** se ocorrer um erro.

## <a name="safeequals"></a>SafeEquals

Compara dois números para determinar se eles são iguais.

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parâmetros

*t*<br/>
[in] O primeiro número para comparar. Deve ser do tipo T.

*u*<br/>
[in] O segundo número para comparar. Deve ser do tipo U.

### <a name="return-value"></a>Valor de retorno

**true** se *t* e *u* forem iguais, caso contrário, **false**.

### <a name="remarks"></a>Comentários

O método aprimora `==` porque `SafeEquals` permite comparar dois tipos diferentes de números.

## <a name="safegreaterthan"></a>SafeGreaterThan

Compara dois números.

```cpp
template<typename T, typename U>
inline bool SafeGreaterThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parâmetros

*t*<br/>
[in] O primeiro número para comparar. Deve ser do tipo `T`.

*u*<br/>
[in] O segundo número para comparar. Deve ser do tipo `U`.

### <a name="return-value"></a>Valor de retorno

**true** se *t* for maior que *u*; caso contrário, **false**.

### <a name="remarks"></a>Comentários

`SafeGreaterThan` estende o operador de comparação regular, permitindo que você compare dois tipos diferentes de números.

## <a name="safegreaterthanequals"></a>SafeGreaterThanEquals

Compara dois números.

```cpp
template <typename T, typename U>
inline bool SafeGreaterThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parâmetros

*t*<br/>
[in] O primeiro número para comparar. Deve ser do tipo `T`.

*u*<br/>
[in] O segundo número para comparar. Deve ser do tipo `U`.

### <a name="return-value"></a>Valor de retorno

**true** se *t* for maior que ou igual a *u*; caso contrário, **false**.

### <a name="remarks"></a>Comentários

`SafeGreaterThanEquals` aprimora o operador de comparação padrão porque permite comparar dois tipos diferentes de números.

## <a name="safelessthan"></a>SafeLessThan

Determina se um número é menor que outro.

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parâmetros

*t*<br/>
[in] O primeiro número. Deve ser do tipo `T`.

*u*<br/>
[in] O segundo número. Deve ser do tipo `U`.

### <a name="return-value"></a>Valor de retorno

**true** se *t* for menor que *u*; caso contrário, **false**.

### <a name="remarks"></a>Comentários

Esse método aprimora o operador de comparação padrão porque `SafeLessThan` permite comparar dois tipos diferentes de números.

## <a name="safelessthanequals"></a>SafeLessThanEquals

Compara dois números.

```cpp
template <typename T, typename U>
inline bool SafeLessThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parâmetros

*t*<br/>
[in] O primeiro número para comparar. Deve ser do tipo `T`.

*u*<br/>
[in] O segundo número para comparar. Deve ser do tipo `U`.

### <a name="return-value"></a>Valor de retorno

**true** se *t* for menor que ou igual a *u*; caso contrário, **false**.

### <a name="remarks"></a>Comentários

`SafeLessThanEquals` estende o operador de comparação regular, permitindo que você compare dois tipos diferentes de números.

## <a name="safemodulus"></a>SafeModulus

Realiza a operação de módulo em dois números.

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parâmetros

*t*<br/>
[in] O divisor. Deve ser do tipo `T`.

*u*<br/>
[in] O dividendo. Deve ser do tipo `U`.

*resultado*<br/>
[out] O parâmetro em que `SafeModulus` armazena o resultado.

### <a name="return-value"></a>Valor de retorno

**true** se nenhum erro ocorrer; **false** se ocorrer um erro.

## <a name="safemultiply"></a>SafeMultiply

Multiplica dois números juntos de uma forma que protege contra estouros.

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parâmetros

*t*<br/>
[in] O primeiro número para multiplicar. Deve ser do tipo `T`.

*u*<br/>
[in] O segundo número para multiplicar. Deve ser do tipo `U`.

*resultado*<br/>
[out] O parâmetro em que `SafeMultiply` armazena o resultado.

### <a name="return-value"></a>Valor de retorno

`true` se não ocorrer erro; `false` se ocorrer um erro.

## <a name="safenotequals"></a>SafeNotEquals

Determina se dois números não são iguais.

```cpp
template<typename T, typename U>
inline bool SafeNotEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parâmetros

*t*<br/>
[in] O primeiro número para comparar. Deve ser do tipo `T`.

*u*<br/>
[in] O segundo número para comparar. Deve ser do tipo `U`.

### <a name="return-value"></a>Valor de retorno

**true** se *t* e *u* não forem iguais, caso contrário, **false**.

### <a name="remarks"></a>Comentários

O método aprimora `!=` porque `SafeNotEquals` permite comparar dois tipos diferentes de números.

## <a name="safesubtract"></a>SafeSubtract

Subtrai dois números de uma maneira que protege contra estouros.

```cpp
template<typename T, typename U>
inline bool SafeSubtract (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parâmetros

*t*<br/>
[in] O primeiro número na subtração. Deve ser do tipo `T`.

*u*<br/>
[in] O número para subtrair de *t*. Deve ser do tipo `U`.

*resultado*<br/>
[out] O parâmetro em que `SafeSubtract` armazena o resultado.

### <a name="return-value"></a>Valor de retorno

**true** se nenhum erro ocorrer; **false** se ocorrer um erro.
