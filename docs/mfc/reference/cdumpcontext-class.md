---
title: Classe CDumpContext
ms.date: 11/04/2016
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
ms.openlocfilehash: a5b53ced4e20c920aab8e7ebcda3e3f6f8798ba5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164092"
---
# <a name="cdumpcontext-class"></a>Classe CDumpContext

Dá suporte a orientada por fluxo de saída de diagnóstico na forma de texto legível.

## <a name="syntax"></a>Sintaxe

```
class CDumpContext
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CDumpContext::CDumpContext](#cdumpcontext)|Constrói um objeto `CDumpContext`.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CDumpContext::DumpAsHex](#dumpashex)|Despeja o item indicado em formato hexadecimal.|
|[CDumpContext::Flush](#flush)|Libera todos os dados no buffer de contexto de despejo.|
|[CDumpContext::GetDepth](#getdepth)|Obtém um inteiro correspondente a profundidade do despejo.|
|[CDumpContext::HexDump](#hexdump)|Despejos de bytes contidos em uma matriz no formato hexadecimal.|
|[CDumpContext::SetDepth](#setdepth)|Define a profundidade do despejo.|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|[CDumpContext::operator &lt;&lt;](#operator_lt_lt)|Insere o contexto de despejo variáveis e objetos.|

## <a name="remarks"></a>Comentários

`CDumpContext` não tem uma classe base.

Você pode usar [afxDump](diagnostic-services.md#afxdump), um pré-declarados `CDumpContext` objeto para a maioria dos seus despejar. O `afxDump` objeto está disponível somente na versão de depuração da biblioteca de classes Microsoft Foundation.

Vários da memória [serviços de diagnóstico](../../mfc/reference/diagnostic-services.md) usar `afxDump` para sua saída.

No ambiente do Windows, a saída do predefinida `afxDump` objeto, conceitualmente semelhante ao `cerr` stream, será roteado para o depurador por meio da função Windows `OutputDebugString`.

O `CDumpContext` classe tem uma inserção sobrecarregada ( **<<**) operador para `CObject` ponteiros que despeja os dados do objeto. Se você precisar de um formato de despejo de memória personalizado para um objeto derivado, substitua [CObject::Dump](../../mfc/reference/cobject-class.md#dump). A maioria das classes Microsoft Foundation implementar um substituído `Dump` função de membro.

Classes que não são derivadas de `CObject`, como `CString`, `CTime`, e `CTimeSpan`, têm seus próprios sobrecarregado `CDumpContext` operadores de inserção, como estruturas geralmente usado como `CFileStatus`, `CPoint`, e `CRect`.

Se você usar o [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) ou [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) macro na implementação de sua classe, em seguida, `CObject::Dump` imprimirá o nome do seu `CObject`-classe derivada. Caso contrário, ele imprimirá `CObject`.

O `CDumpContext` classe está disponível com versões de depuração e versão da biblioteca, mas o `Dump` função de membro é definida somente na versão de depuração. Use **#ifdef DEBUG**  /  `#endif` instruções para seu código de diagnóstico, incluindo o personalizado de colchete `Dump` funções de membro.

Antes de criar seu próprio `CDumpContext` do objeto, você deve criar um `CFile` objeto que serve como o destino de despejo.

Para obter mais informações sobre `CDumpContext`, consulte [Depurando aplicativos do MFC](/visualstudio/debugger/mfc-debugging-techniques).

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`CDumpContext`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** AFX. h

##  <a name="cdumpcontext"></a>  CDumpContext::CDumpContext

Constrói um objeto da classe `CDumpContext`.

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>Parâmetros

*pFile*<br/>
Um ponteiro para o `CFile` objeto que é o destino de despejo.

### <a name="remarks"></a>Comentários

O `afxDump` objeto é criado automaticamente.

Não gravar subjacente `CFile` enquanto o contexto de despejo estiver ativa; caso contrário, você irá interferir com o despejo. No ambiente do Windows, a saída é roteada para o depurador por meio da função Windows `OutputDebugString`.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

##  <a name="dumpashex"></a>  CDumpContext::DumpAsHex

O tipo especificado, formatado como números hexadecimais de despejos de memória.

```
CDumpContext& DumpAsHex(BYTE b);
CDumpContext& DumpAsHex(DWORD dw);
CDumpContext& DumpAsHex(int n);
CDumpContext& DumpAsHex(LONG l);
CDumpContext& DumpAsHex(LONGLONG n);
CDumpContext& DumpAsHex(UINT u);
CDumpContext& DumpAsHex(ULONGLONG n);
CDumpContext& DumpAsHex(WORD w);
```

### <a name="return-value"></a>Valor de retorno

Uma referência a um objeto `CDumpContext`.

### <a name="remarks"></a>Comentários

Chame essa função de membro para o item do tipo especificado como um número hexadecimal de despejo. Para uma matriz de despejo, chame [CDumpContext::HexDump](#hexdump).

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

##  <a name="flush"></a>  CDumpContext::Flush

Força os dados restantes em buffers a serem gravados no arquivo anexado ao contexto de despejo.

```
void Flush();
```

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

##  <a name="getdepth"></a>  CDumpContext::GetDepth

Determina se um despejo deep ou shallow está no processo.

```
int GetDepth() const;
```

### <a name="return-value"></a>Valor de retorno

A profundidade do despejo conforme definido pela `SetDepth`.

### <a name="example"></a>Exemplo

  Veja o exemplo de [SetDepth](#setdepth).

##  <a name="hexdump"></a>  CDumpContext::HexDump

Uma matriz de bytes formatados como números hexadecimais de despejos de memória.

```
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>Parâmetros

*lpszLine*<br/>
Uma cadeia de caracteres de saída no início de uma nova linha.

*pby*<br/>
Um ponteiro para um buffer que contém os bytes a ser despejado.

*nBytes*<br/>
O número de bytes a ser despejado.

*nWidth*<br/>
Número máximo de bytes despejados por linha (não a largura da linha de saída).

### <a name="remarks"></a>Comentários

Para um tipo de item único e específico como um número hexadecimal de despejo, chame [CDumpContext::DumpAsHex](#dumpashex).

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

##  <a name="operator_lt_lt"></a>  CDumpContext::operator &lt;&lt;

Gera os dados especificados para o contexto de despejo.

```
CDumpContext& operator<<(const CObject* pOb);
CDumpContext& operator<<(const CObject& ob);
CDumpContext& operator<<(LPCTSTR lpsz);
CDumpContext& operator<<(const void* lp);
CDumpContext& operator<<(BYTE by);
CDumpContext& operator<<(WORD w);
CDumpContext& operator<<(DWORD dw);
CDumpContext& operator<<(int n);
CDumpContext& operator<<(double d);
CDumpContext& operator<<(float f);
CDumpContext& operator<<(LONG l);
CDumpContext& operator<<(UINT u);
CDumpContext& operator<<(LPCWSTR lpsz);
CDumpContext& operator<<(LPCSTR lpsz);
CDumpContext& operator<<(LONGLONG n);
CDumpContext& operator<<(ULONGLONG n);
CDumpContext& operator<<(HWND h);
CDumpContext& operator<<(HDC h);
CDumpContext& operator<<(HMENU h);
CDumpContext& operator<<(HACCEL h);
CDumpContext& operator<<(HFONT h);
```

### <a name="return-value"></a>Valor de retorno

Uma referência a `CDumpContext`. Usando o valor de retorno, você pode escrever várias inserções em uma única linha de código-fonte.

### <a name="remarks"></a>Comentários

O operador de inserção está sobrecarregado para `CObject` ponteiros, bem como para tipos mais primitivos. Um ponteiro para caractere resulta em um despejo do conteúdo da cadeia de caracteres. um ponteiro para **void** resulta em um despejo hexadecimal do endereço apenas. Um LONGLONG resulta em um despejo de um inteiro com sinal de 64 bits; Um ULONGLONG resulta em um despejo de um inteiro sem sinal de 64 bits.

Se você usar a macro IMPLEMENT_DYNAMIC ou IMPLEMENT_SERIAL na implementação de sua classe e, em seguida, o operador de inserção, por meio `CObject::Dump`, imprimirá o nome do seu `CObject`-classe derivada. Caso contrário, ele imprimirá `CObject`. Se você substituir o `Dump` função da classe, você pode fornecer uma saída mais significativa do conteúdo do objeto, em vez de um despejo hexadecimal.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

##  <a name="setdepth"></a>  CDumpContext::SetDepth

Define a profundidade de despejo.

```
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>Parâmetros

*nNewDepth*<br/>
O novo valor de profundidade.

### <a name="remarks"></a>Comentários

Se você estiver despejar um tipo primitivo ou simples `CObject` que não contém nenhum ponteiros para outros objetos e, em seguida, um valor de 0 é suficiente. Um valor maior que 0 especifica um despejo profundo em que todos os objetos são despejados recursivamente. Por exemplo, um despejo de profundidade de uma coleção despejará todos os elementos da coleção. Você pode usar outros valores específicos de profundidade em suas classes derivadas.

> [!NOTE]
>  Referências circulares não são detectadas nos despejos de profundidade e podem resultar em loops infinitos.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classe CFile](../../mfc/reference/cfile-class.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)
