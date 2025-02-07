---
title: '&lt;exceção > (comentários de documentação do C++)'
ms.date: 11/04/2016
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: 327c1bc27f4ae71aa214e09f375f963dad5b33d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292959"
---
# <a name="ltexceptiongt"></a>&lt;exception&gt;

A marca \<exception> permite que você especifique quais exceções podem ser lançadas. Essa marcação é aplicada a uma definição de método.

## <a name="syntax"></a>Sintaxe

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>Parâmetros

*member*<br/>
Uma referência a uma exceção que está disponível no ambiente de compilação atual. Usando as regras da pesquisa de nome, o compilador verifica se a exceção fornecida existe e converte `member` no nome de elemento canônico no XML de saída.  O compilador emite um aviso se não encontra `member`.

Coloque o nome entre aspas simples ou duplas.

Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [ \<consulte>](see-visual-cpp.md).

*description*<br/>
Uma descrição.

## <a name="remarks"></a>Comentários

Compile com [/doc](doc-process-documentation-comments-c-cpp.md) para processar comentários de documentação em um arquivo.

O compilador MSVC tentará resolver referências cref em uma passagem por meio de comentários de documentação.  Portanto, se você estiver usando as regras de pesquisa do C++ e um símbolo não for encontrado pelo compilador, a referência será marcada como não resolvida. Confira [\<seealso>](seealso-visual-cpp.md) para obter mais informações.

## <a name="example"></a>Exemplo

```
// xml_exception_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_exception_tag.dll
using namespace System;

/// Text for class EClass.
public ref class EClass : public Exception {
   // class definition ...
};

/// <exception cref="System.Exception">Thrown when... .</exception>
public ref class TestClass {
   void Test() {
      try {
      }
      catch(EClass^) {
      }
   }
};
```

## <a name="see-also"></a>Consulte também

[Documentação XML](xml-documentation-visual-cpp.md)
