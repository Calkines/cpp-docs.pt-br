---
title: Classe _com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 8ed1521cbf768e5b473281e5f9b7c6597cdc4692
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519549"
---
# <a name="comerror-class"></a>Classe _com_error

**Seção específica da Microsoft**

Um **com_error** objeto representa uma condição de exceção detectada pelas funções de wrapper de tratamento de erros nos arquivos de cabeçalho gerados a partir da biblioteca de tipos ou por uma das classes de suporte COM. O **com_error** classe encapsula o código de erro HRESULT e associados `IErrorInfo Interface` objeto.

### <a name="construction"></a>Construção

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|Constrói uma **com_error** objeto.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](../cpp/com-error-operator-equal.md)|Atribui um existente **com_error** objeto para outro.|

### <a name="extractor-functions"></a>Funções de extrator

|||
|-|-|
|[Erro](../cpp/com-error-error.md)|Recupera o HRESULT transmitido ao construtor.|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Recupera o objeto `IErrorInfo` passado para o construtor.|
|[WCode](../cpp/com-error-wcode.md)|Recupera o código de erro de 16 bits mapeado para o HRESULT encapsulado.|

### <a name="ierrorinfo-functions"></a>Funções IErrorInfo

|||
|-|-|
|[Descrição](../cpp/com-error-description.md)|Chama a função `IErrorInfo::GetDescription`.|
|[HelpContext](../cpp/com-error-helpcontext.md)|Chama a função `IErrorInfo::GetHelpContext`.|
|[Arquivo de ajuda](../cpp/com-error-helpfile.md)|Chama a função `IErrorInfo::GetHelpFile`.|
|[Source](../cpp/com-error-source.md)|Chama a função `IErrorInfo::GetSource`.|
|[GUID](../cpp/com-error-guid.md)|Chama a função `IErrorInfo::GetGUID`.|

### <a name="format-message-extractor"></a>Extrator de mensagem de formato

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|Recupera a mensagem de cadeia de caracteres para o HRESULT armazenado na **com_error** objeto.|

### <a name="exepinfowcode-to-hresult-mappers"></a>Mapeadores de ExepInfo.wCode para HRESULT

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Mapeia o HRESULT de 32 bits para 16 bits `wCode`.|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapas de 16 bits `wCode` para HRESULT de 32 bits.|

**Fim da seção específica da Microsoft**

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<comdef >

`Lib:` comsuppw. lib ou comsuppwd (consulte [/ZC: wchar_t (wchar_t Is Native Type)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obter mais informações)

## <a name="see-also"></a>Consulte também

[Classes de suporte COM do compilador](../cpp/compiler-com-support-classes.md)<br/>
[Interface IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)