---
title: _bstr_t::wchar_t *, _bstr_t::char*
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
ms.openlocfilehash: bfc149b0f0688bed567bf202fddb4ab2c3102630
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345149"
---
# <a name="bstrtwchart-bstrtchar"></a>_bstr_t::wchar_t\*, _bstr_t::char\*

**Seção específica da Microsoft**

Retorna os caracteres BSTR como uma matriz de caracteres estreitos ou largos.

## <a name="syntax"></a>Sintaxe

```
operator const wchar_t*( ) const throw( );
operator wchar_t*( ) const throw( );
operator const char*( ) const;
operator char*( ) const;
```

## <a name="remarks"></a>Comentários

Esses operadores podem ser usados para extrair os dados de caractere que são encapsuladas pelo objeto `BSTR`. Atribuir um novo valor para o ponteiro retornado não altera os dados originais de BSTR.

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[Classe _bstr_t](../cpp/bstr-t-class.md)