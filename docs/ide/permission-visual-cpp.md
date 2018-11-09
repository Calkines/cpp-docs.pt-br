---
title: '&lt;permission&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
ms.openlocfilehash: 5cbcfd6bee97c3ca937ddfac363cd70276ee4d1e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529110"
---
# <a name="ltpermissiongt-visual-c"></a>&lt;permission&gt; (Visual C++)

A marca \<permissão > permite documentar o acesso de um membro. <xref:System.Security.PermissionSet> permite que você especifique o acesso a um membro.

## <a name="syntax"></a>Sintaxe

```
<permission cref="member">description</permission>
```

#### <a name="parameters"></a>Parâmetros

*member*<br/>
Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e converte `member` no nome de elemento canônico no XML de saída.  Coloque o nome entre aspas simples ou duplas.

O compilador emite um aviso se não encontra `member`.

Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [ \<consulte>](../ide/see-visual-cpp.md).

*description*<br/>
Uma descrição do acesso ao membro.

## <a name="remarks"></a>Comentários

Compile com [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para processar comentários de documentação em um arquivo.

O compilador do Visual C++ tentará resolver as referências cref em uma passagem pelos comentários da documentação.  Portanto, se você estiver usando as regras de pesquisa do C++ e um símbolo não for encontrado pelo compilador, a referência será marcada como não resolvida. Confira [\<seealso>](../ide/seealso-visual-cpp.md) para obter mais informações.

## <a name="example"></a>Exemplo

```
// xml_permission_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_permission_tag.dll
using namespace System;
/// Text for class TestClass.
public ref class TestClass {
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>
   void Test() {}
};
```

## <a name="see-also"></a>Consulte também

[Documentação XML](../ide/xml-documentation-visual-cpp.md)