---
title: Namespaces plataforma, padrão e cli (C++/CLI e C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- lang
- cli
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
ms.openlocfilehash: db6c73d6c52bf97aea5d0fbeeeebdeef87f692cc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311953"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>Namespaces plataforma, padrão e cli (C++/CLI e C++/CX)

Um namespace qualifica os nomes dos elementos da linguagem para que os nomes não entrem em conflito com nomes idênticos em outras áreas do código-fonte. Por exemplo, uma colisão de nomes pode impedir que o compilador reconheça [Palavras-chave contextuais](context-sensitive-keywords-cpp-component-extensions.md). Os namespaces são usados pelo compilador, mas não preservados no assembly compilado.

## <a name="all-runtimes"></a>Todos os Tempos de Execução

O Visual Studio fornece um namespace padrão para seu projeto quando o projeto é criado. Você pode renomear manualmente o namespace, ainda que no C++/CX o nome do arquivo .winmd deva corresponder ao nome do namespace raiz.

## <a name="windows-runtime"></a>Tempo de Execução do Windows

Saiba mais em [Namespaces e visibilidade do tipo (C++/CX)](../cppcx/namespaces-and-type-visibility-c-cx.md).

### <a name="requirements"></a>Requisitos

Opção do compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Sintaxe

```cpp
using namespace cli;
```

### <a name="remarks"></a>Comentários

O C++/CLI é compatível com o namespace **cli**. Para compilar com `/clr`, a instrução **using** na seção Syntax é implícita.

Os seguintes recursos de linguagem estão no namespace **cli**:

- [Matrizes](arrays-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)

- [pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)

- [safe_cast](safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>Requisitos

Opção do compilador: `/clr`

### <a name="examples"></a>Exemplos

O exemplo de código a seguir demonstra que é possível usar um símbolo no namespace **cli** como um símbolo definido pelo usuário em seu código.  No entanto, assim que tiver feito isso, você terá que qualificar explícita ou implicitamente suas referências para o elemento de linguagem **cli** de mesmo nome.

```cpp
// cli_namespace.cpp
// compile with: /clr
using namespace cli;
int main() {
   array<int> ^ MyArray = gcnew array<int>(100);
   int array = 0;

   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062

   // OK
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);
}
```

## <a name="see-also"></a>Consulte também

[Extensões de componentes para .NET e UWP](component-extensions-for-runtime-platforms.md)