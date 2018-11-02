---
title: Classe CKeyboardManager
ms.date: 11/04/2016
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
ms.openlocfilehash: 85bda6747c4ef6bed87b7a2ef30a3ef06bdfe29e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517852"
---
# <a name="ckeyboardmanager-class"></a>Classe CKeyboardManager

Gerencia tabelas de chave de atalho para a janela do quadro principal e janelas filho.

## <a name="syntax"></a>Sintaxe

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|||
|-|-|
|Nome|Descrição|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|Constrói um objeto `CKeyboardManager`.|

### <a name="public-methods"></a>Métodos Públicos

|||
|-|-|
|Nome|Descrição|
|[CKeyboardManager::CleanUp](#cleanup)|Limpa as tabelas de teclas de atalho.|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Recupera a tecla de atalho padrão para o comando especificado e a janela.|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Determina se uma chave é tratada pela tabela de acelerador.|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Indica se um caractere imprimível.|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Indica se menus mostram todas as teclas de atalho para um comando ou a tecla de atalho padrão.|
|[CKeyboardManager::LoadState](#loadstate)|Carrega as tabelas de teclas de atalho do registro do Windows.|
|[CKeyboardManager::ResetAll](#resetall)|Recarrega as tabelas de chave de atalho do recurso do aplicativo.|
|[CKeyboardManager::SaveState](#savestate)|Salva o atalho de tabelas de chave no registro do Windows.|
|[Ckeyboardmanager](#showallaccelerators)|Especifica se o framework exibe todas as teclas de atalho para todos os comandos ou uma única tecla de atalho para cada comando. Esse método não afeta os comandos que têm apenas uma tecla de atalho associada.|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Converte um caractere em seu registro superior.|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Atualiza uma tabela de chave de atalho com uma nova tabela de teclas de atalho.|

## <a name="remarks"></a>Comentários

Os membros dessa classe permitem que você salvar e carregar tabelas de chave de atalho para o registro do Windows, use um modelo para atualizar as tabelas de teclas de atalho e localizar a tecla de atalho padrão para um comando em uma janela de quadro. Além disso, o `CKeyboardManager` objeto permite que você controle como as teclas de atalho são exibidas ao usuário.

Você não deve criar um `CKeyboardManager` objeto manualmente. Ele será criado automaticamente pela estrutura do seu aplicativo. No entanto, você deve chamar [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) durante o processo de inicialização do seu aplicativo. Para obter um ponteiro para o Gerenciador de teclado para o seu aplicativo, chame [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra como recuperar um ponteiro para um `CKeyboardManager` do objeto de um `CWinAppEx` classe e como mostrar todas as teclas de atalho associadas aos comandos de menu. Este trecho de código é parte do [exemplo de páginas personalizadas](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxkeyboardmanager.h

##  <a name="ckeyboardmanager"></a>  CKeyboardManager::CKeyboardManager

Constrói um objeto `CKeyboardManager`.

```
CKeyboardManager();
```

### <a name="remarks"></a>Comentários

Na maioria dos casos, você não precisa criar um `CKeyboardManager` diretamente. Por padrão, a estrutura criará um para você. Para obter um ponteiro para o `CKeyboardManager`, chame [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Se você criar um manualmente, você deve inicializá-lo com o método [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).

##  <a name="cleanup"></a>  CKeyboardManager::CleanUp

Libera o `CKeyboardManager` recursos e limpa todos os mapeamentos de teclas de atalho.

```
static void CleanUp();
```

### <a name="remarks"></a>Comentários

Para obter mais informações sobre teclas de atalho, consulte [personalização de teclado e Mouse](../../mfc/keyboard-and-mouse-customization.md).

Você não precisa chamar essa função quando seu aplicativo for encerrado porque o framework chama automaticamente durante a saída do aplicativo.

##  <a name="finddefaultaccelerator"></a>  CKeyboardManager::FindDefaultAccelerator

Recupera a tecla de atalho padrão para o comando especificado e a janela.

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parâmetros

*uiCmd*<br/>
[in] A ID de comando.

*str*<br/>
[out] Uma referência a um `CString` objeto.

*pWndFrame*<br/>
[in] Um ponteiro para uma janela do quadro.

*bIsDefaultFrame*<br/>
[in] Especifica se a janela do quadro é a janela do quadro padrão.

### <a name="return-value"></a>Valor de retorno

Diferente de zero se o atalho for encontrado; Caso contrário, 0.

### <a name="remarks"></a>Comentários

Este método pesquisa o comando especificado por *uiCmd* e recupera a tecla de atalho padrão. Em seguida, o método usa a cadeia de caracteres associada a essa tecla de atalho e grava o valor para o *str* parâmetro.

##  <a name="iskeyhandled"></a>  CKeyboardManager::IsKeyHandled

Determina se a chave especificada é tratada pelos [classe CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md).

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parâmetros

|||
|-|-|
|Parâmetro|Descrição|
|*nKey*|[in] A chave para verificar.|
|*fVirt*|[in] Especifica o comportamento da tecla de atalho. Para obter uma lista de valores possíveis, consulte [estrutura de ACELERAÇÃO](/windows/desktop/api/winuser/ns-winuser-tagaccel).|
|*pWndFrame*|[in] Uma janela do quadro. Este método determina se uma tecla de atalho é tratada neste quadro.|
|*bIsDefaultFrame*|[in] Um parâmetro booliano que indica se *pWndFrame* é a janela de quadro do padrão.|

### <a name="return-value"></a>Valor de retorno

TRUE se a tecla de atalho é manipulada. FALSE se a chave não for tratada ou se *pWndFrame* é NULL.

### <a name="remarks"></a>Comentários

Os parâmetros de entrada devem corresponder à entrada na tabela de aceleradores ambas as para *nKey* e *fVirt* para determinar se uma tecla de atalho é tratada no *pWndFrame*.

##  <a name="iskeyprintable"></a>  CKeyboardManager::IsKeyPrintable

Indica se um caractere imprimível.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Parâmetros

|||
|-|-|
|Parâmetro|Descrição|
|*nChar*|[in] O caractere que esse método verifica.|

### <a name="return-value"></a>Valor de retorno

Diferente de zero se o caractere for imprimível, zero se não for.

### <a name="remarks"></a>Comentários

Esse método falhar se uma chamada para [GetKeyboardState](https://msdn.microsoft.com/library/windows/desktop/ms646299) falhar.

##  <a name="isshowallaccelerators"></a>  CKeyboardManager::IsShowAllAccelerators

Indica se menus mostram todas as teclas de atalho associadas aos comandos de menu ou as teclas de atalho padrão.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Valor de retorno

Diferente de zero se o aplicativo lista todas as teclas de atalho para comandos de menu. 0 se o aplicativo exibe somente as teclas de atalho padrão.

### <a name="remarks"></a>Comentários

O aplicativo lista as teclas de atalho para comandos de menu na barra de menus. Use a função [Ckeyboardmanager](#showallaccelerators) para controlar se o aplicativo lista todas as teclas de atalho ou apenas as teclas de atalho padrão.

##  <a name="loadstate"></a>  CKeyboardManager::LoadState

Carrega as tabelas de teclas de atalho do registro do Windows.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parâmetros

*lpszProfileName*<br/>
[in] O caminho do registro onde `CKeyboardManager` os dados são salvos.

*pDefaultFrame*<br/>
[in] Um ponteiro para uma janela do quadro a ser usado como a janela padrão.

### <a name="return-value"></a>Valor de retorno

Diferente de zero se o estado foi carregado com êxito ou 0, caso contrário.

### <a name="remarks"></a>Comentários

Se o *lpszProfileName* parâmetro for NULL, esse método verifica o local de registro padrão para `CKeyboardManager` dados. O local do registro padrão for especificado o [classe CWinAppEx](../../mfc/reference/cwinappex-class.md). Os dados devem ser gravados anteriormente com o método [CKeyboardManager::SaveState](#savestate).

Se você não especificar uma janela padrão, a janela do quadro principal de seu aplicativo será usada.

##  <a name="resetall"></a>  CKeyboardManager::ResetAll

Recarrega as tabelas de chave de atalho do recurso do aplicativo.

```
void ResetAll();
```

### <a name="remarks"></a>Comentários

Essa função limpa os atalhos armazenados em do `CKeyboardManager` instância. Ele será, em seguida, recarregue o estado do Gerenciador de teclado do recurso do aplicativo.

##  <a name="savestate"></a>  CKeyboardManager::SaveState

Salva o atalho de tabelas de chave no registro do Windows.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parâmetros

*lpszProfileName*<br/>
[in] O caminho do registro para salvar o `CKeyboardManager` estado.

*pDefaultFrame*<br/>
[in] Um ponteiro para uma janela do quadro que se torna a janela padrão.

### <a name="return-value"></a>Valor de retorno

Diferente de zero se o estado do Gerenciador de teclado foi salva com êxito, ou caso contrário, 0.

### <a name="remarks"></a>Comentários

Se o *lpszProfileName* parâmetro for NULL, esse método gravará os `CKeyboardManager` estado para o local padrão especificado pelo [classe CWinAppEx](../../mfc/reference/cwinappex-class.md). Se você especificar um local, você pode carregar os dados posteriormente usando o método [CKeyboardManager::LoadState](#loadstate).

Se você não especificar uma janela padrão, a janela do quadro principal será usada como a janela padrão.

##  <a name="showallaccelerators"></a>  Ckeyboardmanager

Mostra todas as teclas de atalho associadas aos comandos de menu.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Parâmetros

*bShowAll*<br/>
[in] Se for TRUE, todas as teclas de atalho serão exibidas. Se for FALSE, apenas a primeira chave de atalho será exibida.

*lpszDelimiter*<br/>
[in] Uma cadeia de caracteres a ser inserido entre as teclas de atalho. Este delimitador não tem nenhum efeito se apenas uma tecla de atalho é exibida.

### <a name="remarks"></a>Comentários

Por padrão, se um comando tiver mais de uma tecla de atalho associada a ele, apenas a primeira chave de atalho será mostrada. Essa função permite que você lista as teclas de atalho associadas a todos os comandos.

As teclas de atalho serão listadas ao lado de comando na barra de menus. Se todas as teclas de atalho são exibidas, a cadeia de caracteres fornecido pelo *lpszDelimiter* vai separar as teclas de atalho individuais.

##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper

Converte um caractere em seu registro superior.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Parâmetros

*nChar*<br/>
[in] O caractere a ser convertido.

### <a name="return-value"></a>Valor de retorno

O caractere que é o registro superior dos parâmetros de entrada.

##  <a name="updateacceltable"></a>  CKeyboardManager::UpdateAccelTable

Atualiza uma tabela de chave de atalho com uma nova tabela de teclas de atalho.

```
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    LPACCEL lpAccel,
    int nSize,
    CFrameWnd* pDefaultFrame = NULL);

BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    HACCEL hAccelNew,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parâmetros

*pTemplate*<br/>
[in] Um ponteiro para um modelo de documento.

*lpAccel*<br/>
[in] Um ponteiro para a nova chave de atalho.

*nSize*<br/>
[in] O tamanho da nova tabela de atalho.

*pDefaultFrame*<br/>
[in] Um ponteiro para a janela do quadro padrão.

*hAccelNew*<br/>
[in] Um identificador para a nova tabela de atalho.

### <a name="return-value"></a>Valor de retorno

Diferente de zero se o método for bem-sucedido; Caso contrário, 0.

### <a name="remarks"></a>Comentários

Use essa função para substituir a tabela de atalho existente com novas teclas de atalho para vários objetos de janela de quadro. A função recebe um modelo de documento como um parâmetro para obter acesso a todos os objetos de janela de quadro conectado ao modelo de documento determinado.

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Personalização de teclado e mouse](../../mfc/keyboard-and-mouse-customization.md)

