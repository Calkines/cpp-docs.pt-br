---
title: Acessando informações da classe runtime
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], and RTTI
- CObject class [MFC], using IsKindOf method [MFC]
- run time [MFC], class information
- RUNTIME_CLASS macro [MFC]
- CObject class [MFC], using RUNTIME_CLASS macro [MFC]
- RTTI compiler option [MFC]
- CObject class [MFC], accessing run-time class information
- run time [MFC]
- IsKindOf method method [MFC]
- run-time class [MFC], accessing information
- classes [MFC], run-time class information
- run-time class [MFC]
- RUNTIME_CLASS macro, using
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
ms.openlocfilehash: 2e4f8685033fc7a8a2f49dafa7ef4e4e019d8989
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392941"
---
# <a name="accessing-run-time-class-information"></a>Acessando informações da classe runtime

Este artigo explica como acessar informações sobre a classe de um objeto em tempo de execução.

> [!NOTE]
>  MFC não usa o [informações de tipo de tempo de execução](../cpp/run-time-type-information.md) suporte (RTTI) introduzido no Visual C++ 4.0.

Se você tiver derivadas de sua classe de [CObject](../mfc/reference/cobject-class.md) e usado a **DECLARE**_**dinâmico** e `IMPLEMENT_DYNAMIC`, a `DECLARE_DYNCREATE` e `IMPLEMENT_DYNCREATE`, ou o `DECLARE_SERIAL` e `IMPLEMENT_SERIAL` macros explicado no artigo [derivando uma classe de CObject](../mfc/deriving-a-class-from-cobject.md), o `CObject` classe tem a capacidade de determinar a classe exata de um objeto em tempo de execução.

Essa capacidade é mais útil quando a verificação dos argumentos da função de tipo adicional é necessária e quando você deve escrever o código de finalidade especial com base na classe de um objeto. No entanto, essa prática não é recomendada geralmente porque ela duplica a funcionalidade de funções virtuais.

O `CObject` função de membro `IsKindOf` pode ser usado para determinar se um determinado objeto pertence a uma classe especificada ou se ele é derivado de uma classe específica. O argumento `IsKindOf` é um `CRuntimeClass` objeto, que você pode obter usando o `RUNTIME_CLASS` macro com o nome da classe.

### <a name="to-use-the-runtimeclass-macro"></a>Para usar a macro RUNTIME_CLASS

1. Use `RUNTIME_CLASS` com o nome da classe, conforme mostrado aqui para a classe `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

Você raramente precisará acessar diretamente o objeto da classe de tempo de execução. Um uso mais comum é para passar o objeto de classe de tempo de execução para o `IsKindOf` de função, conforme mostrado no próximo procedimento. O `IsKindOf` função testa um objeto para ver se ele pertence a uma determinada classe.

#### <a name="to-use-the-iskindof-function"></a>Usar a função IsKindOf

1. Verifique se que a classe tem suporte de classe de tempo de execução. Ou seja, a classe deve ter foi derivada direta ou indiretamente `CObject` e usado a **DECLARE**_**dinâmico** e `IMPLEMENT_DYNAMIC`, o `DECLARE_DYNCREATE` e `IMPLEMENT_DYNCREATE`, ou o `DECLARE_SERIAL` e `IMPLEMENT_SERIAL` macros explicado no artigo [derivando uma classe de CObject](../mfc/deriving-a-class-from-cobject.md).

1. Chame o `IsKindOf` função de membro para objetos dessa classe usando o `RUNTIME_CLASS` macro para gerar o `CRuntimeClass` argumento, como mostrado aqui:

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  Retorna IsKindOf **verdadeira** se o objeto for um membro da classe especificada ou de uma classe derivada da classe especificada. `IsKindOf` não suporta vários herança ou as classes base virtuais, embora você possa usar herança múltipla para seu Microsoft Foundation classes derivadas, se necessário.

Um uso de informações de classe de tempo de execução é na criação dinâmica de objetos. Esse processo é abordado no artigo [criação de objeto dinâmico](../mfc/dynamic-object-creation.md).

Para obter mais informações sobre a serialização e informações de classe de tempo de execução, consulte os artigos [arquivos no MFC](../mfc/files-in-mfc.md) e [serialização](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Consulte também

[Usando CObject](../mfc/using-cobject.md)
