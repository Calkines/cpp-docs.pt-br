---
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 97f0100d8a34253f3a1375d34b887d3d31a77f43
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350865"
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =

**Seção específica da Microsoft**

Atribui um novo valor a um objeto `_bstr_t` existente.

## <a name="syntax"></a>Sintaxe

```
_bstr_t& operator=(const _bstr_t& s1) throw ( );
_bstr_t& operator=(const char* s2);
_bstr_t& operator=(const wchar_t* s3);
_bstr_t& operator=(const _variant_t& var);
```

#### <a name="parameters"></a>Parâmetros

*s1*<br/>
Um objeto `_bstr_t` a ser atribuído a um objeto existente `_bstr_t`.

*s2*<br/>
Uma cadeia de caracteres multibyte a ser atribuída a um objeto `_bstr_t` existente.

*s3*<br/>
Uma cadeia de caracteres Unicode a ser atribuída a um objeto `_bstr_t` existente.

*var*<br/>
Um objeto `_variant_t` a ser atribuído a um objeto existente `_bstr_t`.

**Fim da seção específica da Microsoft**

## <a name="example"></a>Exemplo

Ver [_bstr_t::Assign](../cpp/bstr-t-assign.md) para obter um exemplo de como usar **operador =**.

## <a name="see-also"></a>Consulte também

[Classe _bstr_t](../cpp/bstr-t-class.md)