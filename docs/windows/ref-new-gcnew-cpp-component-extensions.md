---
title: gcnew de ref new, (C + + c++ /CLI e c++ /CLI CX) | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
dev_langs:
- C++
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9553ac6bf1d2e8e8d92745456f1f52d1de1c9ba
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057030"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>gcnew de ref new, (C + + c++ /CLI e c++ /CLI CX)

O **ref novos** palavra-chave agregação aloca uma instância de um tipo que é quando o objeto se torna inacessível e que retorna um identificador de coleta de lixo ([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)) para o objeto alocado.

## <a name="all-runtimes"></a>Todos os Tempos de Execução

Memória para uma instância de um tipo que está alocada por **ref novo** é desalocado automaticamente.

Um **ref novos** operação gera `OutOfMemoryException` se não for possível alocar memória.

Para obter mais informações sobre como a memória para tipos nativos do C++ é alocada e desalocada, consulte [novo e excluir operadores](../cpp/new-and-delete-operators.md).

## <a name="windows-runtime"></a>Tempo de Execução do Windows

Use **ref novo** alocar memória para objetos de tempo de execução do Windows cujo tempo de vida que você deseja administrar automaticamente. O objeto automaticamente será desalocado quando sua contagem de referência chega a zero, o que ocorre depois que a última cópia da referência tiver saído do escopo. Para obter mais informações, consulte [classes e estruturas Ref](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Requisitos

Opção do compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Memória de um tipo gerenciado (tipo de valor ou referência) é alocada pelo **gcnew**e desalocada usando a coleta de lixo.

### <a name="requirements"></a>Requisitos

Opção do compilador: `/clr`

### <a name="examples"></a>Exemplos

O exemplo a seguir usa **gcnew** alocar um objeto de mensagem.

```cpp
// mcppv2_gcnew_1.cpp
// compile with: /clr
ref struct Message {
   System::String^ sender;
   System::String^ receiver;
   System::String^ data;
};

int main() {
   Message^ h_Message  = gcnew Message;
  //...
}
```

O exemplo a seguir usa **gcnew** para criar um tipo de valor demarcado para uso como um tipo de referência.

```cpp
// example2.cpp : main project file.
// compile with /clr
using namespace System;
value class Boxed {
    public:
        int i;
};
int main()
{
    Boxed^ y = gcnew Boxed;
    y->i = 32;
    Console::WriteLine(y->i);
    return 0;
}
```

```Output
32
```

## <a name="see-also"></a>Consulte também

[Extensões de componentes para .NET e UWP](../windows/component-extensions-for-runtime-platforms.md)