---
title: Classe filesystem_error
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: 7bd6b2d3d716ba25999388d44e7bd5a8d0750eb5
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127209"
---
# <a name="filesystem_error-class"></a>Classe filesystem_error

Uma classe base para todas as exceções geradas para relatar um estouro de baixo nível no sistema.

## <a name="syntax"></a>Sintaxe

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Comentários

A classe serve como a classe base para todas as exceções geradas para relatar um erro em funções \<filesystem >. Ele armazena um objeto do tipo `string`, chamado `mymesg` aqui para fins de exposição. Ele também armazena dois objetos do tipo `path`, chamados `mypval1` e `mypval2`.

## <a name="members"></a>Membros

### <a name="constructors"></a>Construtores

|||
|-|-|
|[filesystem_error](#filesystem_error)|Constrói uma `filesystem_error` mensagem.|

### <a name="functions"></a>Funções

|||
|-|-|
|[path1](#path1)|Retorna `mypval1`|
|[path2](#path2)|Retorna `mypval2`|
|[what](#what)|Retorna um ponteiro para um `NTBS`.|

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<> do sistema de arquivos

**Namespace:** std::experimental::filesystem

## <a name="filesystem_error"></a>filesystem_error

O primeiro construtor constrói sua mensagem do *what_arg* e do *EC*. O segundo construtor também constrói sua mensagem de *pval1*, que é armazenada no `mypval1`. O terceiro construtor também constrói sua mensagem de *pval1*, que armazena em `mypval1`e de *pval2*, que armazena no `mypval2`.

```cpp
filesystem_error(const string& what_arg,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    const path& pval2,
    error_code ec);
```

### <a name="parameters"></a>Parâmetros

*what_arg*\
Mensagem especificada.

*Comunidade*\
Código de erro especificado.

*mypval1*\
Outro parâmetro de mensagem especificado.

*mypval2*\
Outro parâmetro de mensagem especificado.

## <a name="path1"></a>path1

A função membro retorna `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a>caminho

A função membro retorna `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a>acontece

A função member retorna um ponteiro para um `NTBS`, preferencialmente composto `runtime_error::what()`de `system_error::what()`, `mymesg`, `mypval1.native_string()`, e `mypval2.native_string()`.

```cpp
const char *what() const noexcept;
```
