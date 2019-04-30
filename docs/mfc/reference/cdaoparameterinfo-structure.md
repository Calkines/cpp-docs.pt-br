---
title: Estrutura CDaoParameterInfo
ms.date: 11/04/2016
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 62addd44f8aa8fceafef6a27244994a2ec6b766b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399779"
---
# <a name="cdaoparameterinfo-structure"></a>Estrutura CDaoParameterInfo

O `CDaoParameterInfo` estrutura contém informações sobre um objeto de parâmetro definido para objetos de acesso de dados (DAO).

## <a name="syntax"></a>Sintaxe

```
struct CDaoParameterInfo
{
    CString m_strName;       // Primary
    short m_nType;           // Primary
    ColeVariant m_varValue;  // Secondary
};
```

#### <a name="parameters"></a>Parâmetros

*m_strName*<br/>
Exclusivamente nomeia o objeto de parâmetro. Para obter mais informações, consulte o tópico "Propriedade de nome" na Ajuda do DAO.

*m_nType*<br/>
Um valor que indica o tipo de dados de um objeto de parâmetro. Para obter uma lista dos valores possíveis, consulte o *m_nType* membro a [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estrutura. Para obter mais informações, consulte o tópico "Propriedade do tipo" na Ajuda do DAO.

*m_varValue*<br/>
O valor do parâmetro, armazenado em uma [COleVariant](../../mfc/reference/colevariant-class.md) objeto.

## <a name="remarks"></a>Comentários

As referências a primária e secundária acima indicam como as informações são retornadas pela [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) função de membro na classe `CDaoQueryDef`.

MFC não encapsula os objetos de parâmetro DAO em uma classe. DAO querydef objetos MFC subjacente `CDaoQueryDef` objetos armazenam parâmetros em suas coleções de parâmetros. Para acessar os objetos de parâmetro em uma [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) do objeto, chame o objeto de querydef `GetParameterInfo` função de membro para um nome de parâmetro específico ou um índice na coleção de parâmetros. Você pode usar o [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) função de membro em conjunto com `GetParameterInfo` para executar um loop através da coleção de parâmetros.

As informações recuperadas pelo [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) função de membro é armazenada em um `CDaoParameterInfo` estrutura. Chamar `GetParameterInfo` para o objeto querydef cuja coleção de parâmetros, o objeto de parâmetro é armazenado.

> [!NOTE]
>  Se você quiser obter ou definir apenas o valor de um parâmetro, use o [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) e [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) funções membro da classe `CDaoRecordset`.

`CDaoParameterInfo` também define um `Dump` compilações de função de membro na depuração. Você pode usar `Dump` para despejar o conteúdo de um `CDaoParameterInfo` objeto.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxdao.h

## <a name="see-also"></a>Consulte também

[Estruturas, estilos, retornos de chamada e mapas de mensagem](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Classe CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)
