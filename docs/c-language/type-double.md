---
title: Tipo duplo
ms.date: 11/04/2016
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
ms.openlocfilehash: 43e6cc444f4d6a973fc58b5ce550e468066aca1b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151852"
---
# <a name="type-double"></a>Tipo duplo

Os valores de precisão double com tipo double têm 8 bytes. O formato é semelhante ao formato de float, exceto que tem um expoente excess-1023 de 11 bits e uma mantissa de 52 bits, mais 1 bit implícito de ordem alta. Esse formato fornece um intervalo de aproximadamente 1.7E-308 a 1.7E+308 para o tipo double.

**Seção específica da Microsoft**

O tipo duplo contém 64 bits: 1 para o sinal, 11 para o expoente e 52 para a mantissa. O intervalo é +/-1.7E308 com pelo menos 15 dígitos de precisão.

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[Armazenamento de tipos básicos](../c-language/storage-of-basic-types.md)
