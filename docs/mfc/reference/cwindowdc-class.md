---
title: Classe CWindowDC
ms.date: 11/04/2016
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
ms.openlocfilehash: 55a9ccfc496c95c9e7410cbd5645135ee555ff26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323379"
---
# <a name="cwindowdc-class"></a>Classe CWindowDC

Derivada de `CDC`.

## <a name="syntax"></a>Sintaxe

```
class CWindowDC : public CDC
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|Constrói um objeto `CWindowDC`.|

### <a name="protected-data-members"></a>Membros de dados protegidos

|Nome|Descrição|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|O HWND ao qual este `CWindowDC` está anexado.|

## <a name="remarks"></a>Comentários

Chama a função do Windows [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc)na ocasião da construção e [ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc) no tempo de destruição. Isso significa que um `CWindowDC` objeto acessa a área da tela inteira de um [CWnd](../../mfc/reference/cwnd-class.md) (áreas de cliente e não cliente).

Para obter mais informações sobre como usar `CWindowDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Requisitos

Header: afxwin.h

##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC

Constrói uma `CWindowDC` que acessa a área da tela inteira (cliente e não cliente) do objeto de `CWnd` objeto apontado por *Apropriei*.

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parâmetros

*pWnd*<br/>
A janela cuja área de cliente que acessará o objeto de contexto de dispositivo.

### <a name="remarks"></a>Comentários

O construtor chama a função do Windows [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc).

Uma exceção (do tipo `CResourceException`) será gerada se o Windows `GetWindowDC` chamar falhar. Um contexto de dispositivo pode não estar disponível se o Windows já alocado todos os seus contextos de dispositivo disponíveis. Seu aplicativo compete para os cinco comuns contextos de exibição disponíveis a qualquer momento determinado em Windows.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd

O HWND do `CWnd` ponteiro é usado para construir o `CWindowDC` objeto.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Comentários

`m_hWnd` é uma variável protegida do tipo HWND.

### <a name="example"></a>Exemplo

  Veja o exemplo de [CWindowDC::CWindowDC](#cwindowdc).

## <a name="see-also"></a>Consulte também

[Classe CDC](../../mfc/reference/cdc-class.md)<br/>
[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classe CDC](../../mfc/reference/cdc-class.md)
