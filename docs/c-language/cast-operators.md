---
title: Operadores cast
ms.date: 11/04/2016
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
ms.openlocfilehash: e3d892a5aede4cd2d6a980b440875f0ac9837120
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147939"
---
# <a name="cast-operators"></a>Operadores cast

Uma conversão de tipo fornece um método para conversão explícita do tipo de um objeto em uma situação específica.

## <a name="syntax"></a>Sintaxe

*cast-expression*: *unary-expression*

**(**  *type-name*  **)**  *cast-expression*

O compilador trata *cast-expression* como tipo *type-name* depois que uma conversão de tipo é feita. As conversões podem ser usadas para converter objetos de qualquer tipo escalar em ou de qualquer outro tipo escalar. As conversões de tipo explícito são restringidas pelas mesmas regras que determinam os efeitos de conversões implícitas, descritos em [Conversões de atribuição](../c-language/assignment-conversions.md). As restrições adicionais de conversões podem resultar de tamanhos reais ou de representação de tipos específicos. Consulte [Armazenamento de tipos básicos](../c-language/storage-of-basic-types.md) para obter informações sobre tamanhos reais de tipos integrais. Para obter mais informações sobre conversões de tipos, consulte [Conversões Type-Cast](../c-language/type-cast-conversions.md).

## <a name="see-also"></a>Consulte também

[Operador cast: ()](../cpp/cast-operator-parens.md)
