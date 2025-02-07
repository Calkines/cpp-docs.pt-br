---
title: Classe CFixedStringT
ms.date: 03/27/2019
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
ms.openlocfilehash: 6c7649b7131e3b1620112acf89867d0731d7265d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235153"
---
# <a name="cfixedstringt-class"></a>Classe CFixedStringT

Essa classe representa um objeto de cadeia de caracteres com um buffer de caracteres fixa.

## <a name="syntax"></a>Sintaxe

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>Parâmetros

*StringType*<br/>
Usado como a classe base para o objeto de cadeia de caracteres fixa e pode ser qualquer `CStringT`-com base em tipo. Alguns exemplos incluem `CString`, `CStringA`, e `CStringW`.

*t_nChars*<br/>
O número de caracteres armazenados em buffer.

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CFixedStringT::CFixedStringT](#cfixedstringt)|O construtor para o objeto de cadeia de caracteres.|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|[CFixedStringT::operator =](#operator_eq)|Atribui um novo valor para um `CFixedStringT` objeto.|

## <a name="remarks"></a>Comentários

Essa classe é um exemplo de uma classe de cadeia de caracteres personalizada com base em `CStringT`. Embora seja semelhante, as duas classes diferem na implementação. As principais diferenças entre `CFixedStringT` e `CStringT` são:

- O buffer de caractere inicial é distribuído como parte do objeto e possui tamanho *t_nChars*. Isso permite que o `CFixedString` objeto para ocupar um bloco de memória contígua para fins de desempenho. No entanto, se o conteúdo de um `CFixedStringT` objeto ultrapassar *t_nChars*, o buffer é alocado dinamicamente.

- O buffer de caracteres para um `CFixedStringT` objeto é sempre o mesmo tamanho ( *t_nChars*). Não há nenhuma limitação no tamanho do buffer para `CStringT` objetos.

- O Gerenciador de memória para `CFixedStringT` personalizada, de modo que o compartilhamento de um [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) objeto entre dois ou mais `CFixedStringT` objetos não é permitido. `CStringT` objetos não têm essa limitação.

Para obter mais informações sobre a personalização da `CFixedStringT` e o gerenciamento de memória para objetos de cadeia de caracteres em geral, consulte [gerenciamento de memória e CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** cstringt. h

##  <a name="cfixedstringt"></a>  CFixedStringT::CFixedStringT

Constrói um objeto `CFixedStringT`.

```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT(const StringType& strSrc);
CFixedStringT(const StringType::XCHAR* pszSrc);
explicit CFixedStringT(const StringType::YCHAR* pszSrc);
explicit CFixedStringT(const unsigned char* pszSrc);
```

### <a name="parameters"></a>Parâmetros

*pszSrc*<br/>
Uma cadeia de caracteres terminada em nulo a ser copiado para isso `CFixedStringT` objeto.

*strSrc*<br/>
Um existente `CFixedStringT` o objeto a ser copiado para isso `CFixedStringT` objeto.

*pStringMgr*<br/>
Um ponteiro para o Gerenciador de memória do `CFixedStringT` objeto. Para obter mais informações sobre `IAtlStringMgr` e o gerenciamento de memória para `CFixedStringT`, consulte [gerenciamento de memória e CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

### <a name="remarks"></a>Comentários

Como os construtores copiam os dados de entrada para o novo armazenamento alocado, você deve estar ciente de que as exceções podem resultar de memória. Alguns desses construtores atuam como funções de conversão.

##  <a name="operator_eq"></a>  CFixedStringT::operator =

Reinicializa um existente `CFixedStringT` objeto com novos dados.

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT<StringType, t_nChars>& operator=(const char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& strSrc);
```

### <a name="parameters"></a>Parâmetros

*pszSrc*<br/>
Uma cadeia de caracteres terminada em nulo a ser copiado para isso `CFixedStringT` objeto.

*strSrc*<br/>
Um existente `CFixedStringT` a ser copiado para isso `CFixedStringT` objeto.

### <a name="remarks"></a>Comentários

Você deve estar ciente que exceções podem ocorrer sempre que você usa o operador de atribuição, porque o novo armazenamento geralmente é alocado para armazenar resultante a memória `CFixedStringT` objeto.

## <a name="see-also"></a>Consulte também

[Classe CStringT](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classes compartilhadas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
