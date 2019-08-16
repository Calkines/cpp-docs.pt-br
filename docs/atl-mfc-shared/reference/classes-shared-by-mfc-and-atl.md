---
title: Classes compartilhadas por MFC e ATL
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: e3e4b35721e84e289aed586c4d010a6986dcc61c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491453"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Classes compartilhadas por MFC e ATL

A tabela a seguir lista as classes compartilhadas entre MFC e ATL.

|Classe|Descrição|Arquivo de cabeçalho|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|Fornece métodos para gerenciar os valores de data e hora associados a um arquivo.|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Fornece métodos para gerenciar valores de data e hora relativos associados a um arquivo.|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Representa um objeto de cadeia de caracteres com um buffer de caracteres fixo.|cstringt.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Fornece suporte a bitmap avançado, incluindo a capacidade de carregar e salvar imagens em formatos JPEG, GIF, BMP e Portable Network Graphics (PNG).|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Encapsula o tipo de dados de data usado na automação OLE.|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Representa uma hora relativa, um período de tempo.|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Uma classe semelhante à estrutura do [ponto](/windows/win32/api/windef/ns-windef-point) do Windows que também inclui funções de membro `CPoint` para `POINT` manipular e estruturar.|atltypes. h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|Uma classe semelhante a uma estrutura de [Rect](/windows/win32/api/windef/ns-windef-rect) do Windows que também inclui funções de `CRect` membro para manipular `RECT` objetos e estruturas do Windows.|atltypes. h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|Representa um `CSimpleStringT` objeto.|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|Uma classe semelhante à estrutura de [tamanho](/windows/win32/api/windef/ns-windef-size) do Windows, que implementa uma coordenada ou posição relativa.|atltypes. h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Fornece limpeza automática de `GetBuffer` recursos e `ReleaseBuffer` chamadas em um objeto existente. `CStringT`|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Representa os dados de um objeto de cadeia de caracteres.|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|Representa um `CStringT` objeto.|CStringT. h (dependente do MFC) atlstr. h (independente do MFC)|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|Representa uma data e hora absoluta.|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Uma quantidade de tempo, que é armazenada internamente como o número de segundos no período de tempo.|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Representa a interface para um `CStringT` Gerenciador de memória.|atlsimpstr.h|

## <a name="see-also"></a>Consulte também

[Classes compartilhadas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
