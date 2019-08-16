---
title: Classe _com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 828a1ec68fef631700d5b64e6aeeec6660acf9a8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498740"
---
# <a name="_com_error-class"></a>Classe _com_error

**Seção específica da Microsoft**

Um objeto **_com_error** representa uma condição de exceção detectada pelas funções de wrapper de tratamento de erros nos arquivos de cabeçalho gerados da biblioteca de tipos ou por uma das classes de suporte com. A classe **_com_error** encapsula o código de erro HRESULT e qualquer objeto `IErrorInfo Interface` associado.

### <a name="construction"></a>Construção

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|Constrói um objeto **_com_error** .|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator =](../cpp/com-error-operator-equal.md)|Atribui um objeto **_com_error** existente a outro.|

### <a name="extractor-functions"></a>Funções de extrator

|||
|-|-|
|[Erro](../cpp/com-error-error.md)|Recupera o HRESULT passado para o construtor.|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Recupera o objeto `IErrorInfo` passado para o construtor.|
|[WCode](../cpp/com-error-wcode.md)|Recupera o código de erro de 16 bits mapeado para o HRESULT encapsulado.|

### <a name="ierrorinfo-functions"></a>Funções IErrorInfo

|||
|-|-|
|[Descrição](../cpp/com-error-description.md)|Chama a função `IErrorInfo::GetDescription`.|
|[HelpContext](../cpp/com-error-helpcontext.md)|Chama a função `IErrorInfo::GetHelpContext`.|
|[HelpFile](../cpp/com-error-helpfile.md)|Chama a função `IErrorInfo::GetHelpFile`.|
|[Source](../cpp/com-error-source.md)|Chama a função `IErrorInfo::GetSource`.|
|[GUID](../cpp/com-error-guid.md)|Chama a função `IErrorInfo::GetGUID`.|

### <a name="format-message-extractor"></a>Extrator de mensagem de formato

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|Recupera a mensagem de cadeia de caracteres para HRESULT armazenado no objeto **_com_error** .|

### <a name="exepinfowcode-to-hresult-mappers"></a>Mapeadores de ExepInfo.wCode para HRESULT

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Mapeia 32 bits HRESULT para 16 bits `wCode`.|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapeia 16 bits `wCode` para HRESULT de 32 bits.|

**Fim da seção específica da Microsoft**

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<> comdef. h

`Lib:`comsuppw. lib ou comsuppwd. lib (consulte [/Zc: wchar_t (Wchar_t é o tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obter mais informações)

## <a name="see-also"></a>Consulte também

[Classes de suporte COM do compilador](../cpp/compiler-com-support-classes.md)<br/>
[Interface IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)