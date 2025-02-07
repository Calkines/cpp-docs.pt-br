---
title: Exportando funções a partir de uma DLL por ordinal e não por nome
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: d91b516253fc160686e2f1f6ae1ca1704f707f75
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221431"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Exportando funções a partir de uma DLL por ordinal e não por nome

É a maneira mais simples para exportar funções de DLL para exportá-los por nome. Isso é o que acontece quando você usa **dllexport**, por exemplo. Mas, em vez disso, você pode exportar funções por ordinal. Com essa técnica, você deve usar um arquivo. def, em vez de **dllexport**. Para especificar o valor ordinal de uma função, anexe seu ordinal para o nome da função no arquivo. def. Para obter informações sobre como especificar ordinais, consulte [exportando de uma DLL usando arquivos. def](exporting-from-a-dll-using-def-files.md).

> [!TIP]
>  Se você deseja otimizar o tamanho do arquivo da sua DLL, use o **NONAME** atributo em cada função exportada. Com o **NONAME** atributo, os ordinais são armazenados em DLL exporta tabela, em vez dos nomes de função. Se você estiver exportando muitas funções, isso pode ser uma economia considerável.

## <a name="what-do-you-want-to-do"></a>O que você deseja fazer?

- [Usar um arquivo. def, portanto, posso exportar por ordinal](exporting-from-a-dll-using-def-files.md)

- [Use __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Consulte também

[Exportando de uma DLL](exporting-from-a-dll.md)
