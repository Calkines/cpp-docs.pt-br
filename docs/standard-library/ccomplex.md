---
title: '&lt;ccomplex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ccomplex>
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
ms.openlocfilehash: e0f8c31afac0608b4de66bd10602264666d39426
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667929"
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

Inclui o cabeçalho da Biblioteca Padrão C++ [\<complex>](../standard-library/complex.md), que inclui efetivamente o cabeçalho da biblioteca C Padrão \<complex.h> e adiciona os nomes associados ao namespace `std`.

## <a name="syntax"></a>Sintaxe

```cpp
#include <ccomplex>

```

## <a name="remarks"></a>Comentários

A inclusão desse cabeçalho garante que os nomes declarados usando vinculação externa no cabeçalho da biblioteca C Padrão sejam declarados no namespace `std`.

O nome `clog`, declarado em \<complex.h>, não é definido no namespace `std` devido a conflitos em potencial com o `clog` declarado em [\<iostream>](../standard-library/iostream.md).

## <a name="see-also"></a>Consulte também

[Referência de Arquivos de Cabeçalho](../standard-library/cpp-standard-library-header-files.md)<br/>
[Visão geral da biblioteca padrão C++](../standard-library/cpp-standard-library-overview.md)<br/>
