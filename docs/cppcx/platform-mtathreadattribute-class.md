---
title: Classe Platform::MTAThreadAttribute
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
ms.openlocfilehash: 4564def412834ae0586292e8aa533d3b2bd0d679
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152664"
---
# <a name="platformmtathreadattribute-class"></a>Classe Platform::MTAThreadAttribute

Indica que o modelo de threading COM para um aplicativo é MTA (Multi-Threaded Apartment).

## <a name="syntax"></a>Sintaxe

```
public ref class MTAThreadAttribute sealed : Attribute
```

### <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[1 de construtor MTAThreadAttribute](#ctor) construtor|Inicializa uma nova instância da classe.|

### <a name="public-methods"></a>Métodos públicos

O atributo MTAThreadAttribute herda [classe Platform:: Object](../cppcx/platform-object-class.md). O MTAThreadAttribute também sobrecarrega ou tem os seguintes membros:

|Nome|Descrição|
|----------|-----------------|
|[MTAThreadAttribute::Equals](#equals)|Determina se o objeto especificado é igual ao objeto atual.|
|[MTAThreadAttribute::GetHashCode](#gethashcode)|Retorna o código hash para essa instância.|
|[MTAThreadAttribute::ToString](#tostring)|Retorna uma cadeia de caracteres que representa o objeto atual.|

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`Platform`

### <a name="requirements"></a>Requisitos

**Metadados:** platform.winmd

**Namespace:** Plataforma

## <a name="ctor"></a> Construtor MTAThreadAttribute

Inicializa uma nova instância da classe MTAThreadAttribute.

### <a name="syntax"></a>Sintaxe

```cpp
public:MTAThreadAttribute();
```

## <a name="equals"></a> MTAThreadAttribute::Equals

Determina se o objeto especificado é igual ao objeto atual.

### <a name="syntax"></a>Sintaxe

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>Parâmetros

*obj*<br/>
O objeto a ser comparado.

### <a name="return-value"></a>Valor de retorno

**Verdadeiro** se os objetos forem iguais; caso contrário, **falso**.

## <a name="gethashcode"></a> MTAThreadAttribute::GetHashCode

Retorna o código hash para essa instância.

### <a name="syntax"></a>Sintaxe

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Valor de retorno

O código hash para essa instância.

## <a name="tostring"></a> MTAThreadAttribute::ToString

Retorna uma cadeia de caracteres que representa o objeto atual.

### <a name="syntax"></a>Sintaxe

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Valor de retorno

Uma cadeia de caracteres que representa o objeto atual.

## <a name="see-also"></a>Consulte também

[Namespace de plataforma](platform-namespace-c-cx.md)
