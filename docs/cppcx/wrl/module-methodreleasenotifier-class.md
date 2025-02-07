---
title: Classe Module::MethodReleaseNotifier
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
ms.openlocfilehash: 41b7cfb2601cd2023e895dbcf1a56e85fe65b35d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325059"
---
# <a name="modulemethodreleasenotifier-class"></a>Classe Module::MethodReleaseNotifier

Invoca um manipulador de eventos quando o último objeto no módulo atual é liberado. O manipulador de eventos é especificado por um objeto e seu membro de ponteiro ao método.

## <a name="syntax"></a>Sintaxe

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parâmetros

*T*<br/>
O tipo do objeto cuja função de membro é o manipulador de eventos.

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

Nome                                                                                                 | Descrição
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module::MethodReleaseNotifier::MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | Inicializa uma nova instância da classe `Module::MethodReleaseNotifier`.

### <a name="public-methods"></a>Métodos públicos

Nome                                                                   | Descrição
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier::Invoke](#methodreleasenotifier-invoke) | Chama o manipulador de eventos associado ao atual `Module::MethodReleaseNotifier` objeto.

### <a name="protected-data-members"></a>Membros de dados protegidos

Nome                                                                    | Descrição
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier::method_](#methodreleasenotifier-method) | Contém um ponteiro para o manipulador de eventos para o atual `Module::MethodReleaseNotifier` objeto.
[Module::MethodReleaseNotifier::object_](#methodreleasenotifier-object) | Contém um ponteiro para o objeto cuja função de membro é o manipulador de eventos para o atual `Module::MethodReleaseNotifier` objeto.

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** module.h

**Namespace:** Microsoft::WRL

## <a name="methodreleasenotifier-invoke"></a>Module::MethodReleaseNotifier::Invoke

Chama o manipulador de eventos associado ao atual `Module::MethodReleaseNotifier` objeto.

```cpp
void Invoke();
```

## <a name="methodreleasenotifier-method"></a>Module::MethodReleaseNotifier::method_

Contém um ponteiro para o manipulador de eventos para o atual `Module::MethodReleaseNotifier` objeto.

```cpp
void (T::* method_)();
```

## <a name="methodreleasenotifier-methodreleasenotifier"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier

Inicializa uma nova instância da classe `Module::MethodReleaseNotifier`.

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>Parâmetros

*object*<br/>
Um objeto cuja função de membro é um manipulador de eventos.

*Método*<br/>
A função de membro do parâmetro *objeto* que é o manipulador de eventos.

*release*<br/>
Especificar `true` para habilitar a chamada subjacente [Module:: ReleaseNotifier::Release()](module-releasenotifier-class.md#releasenotifier-release) método; caso contrário, especifique `false`.

## <a name="methodreleasenotifier-object"></a>Module::MethodReleaseNotifier::object_

Contém um ponteiro para o objeto cuja função de membro é o manipulador de eventos para o atual `Module::MethodReleaseNotifier` objeto.

```cpp
T* object_;
```
