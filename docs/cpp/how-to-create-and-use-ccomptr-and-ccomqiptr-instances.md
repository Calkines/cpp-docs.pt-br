---
title: 'Como: Criar e usar instâncias CComPtr e CComQIPtr'
ms.custom: how-to
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: 2bcabfe80185939b899c84fc44f71b98608fc3c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154055"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Como: Criar e usar instâncias CComPtr e CComQIPtr

Na programação clássica do Windows, bibliotecas geralmente são implementadas como objetos COM (ou mais precisamente, como servidores COM). Muitos componentes do sistema operacional Windows são implementados como servidores COM e muitos colaboradores fornecem bibliotecas neste formulário. Para obter informações sobre os conceitos básicos de COM, consulte [(COM Component Object Model)](/windows/desktop/com/component-object-model--com--portal).

Quando você instancia um objeto de modelo de objeto de componente (COM), armazenar o ponteiro de interface em um ponteiro inteligente COM, que executa a referência de contagem usando chamadas para `AddRef` e `Release` no destruidor. Se você estiver usando a biblioteca ATL (Active Template) ou o Microsoft Foundation Class Library (MFC), em seguida, use o `CComPtr` ponteiro inteligente. Se você não estiver usando o MFC ou ATL, em seguida, use `_com_ptr_t`. Porque não há nenhuma COM equivalente a `std::unique_ptr`, use esses ponteiros inteligentes para o único proprietário e o proprietário de vários cenários. Ambos `CComPtr` e `ComQIPtr` suporte mover as operações que têm referências de rvalue.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar `CComPtr` para instanciar um objeto COM e obter ponteiros para suas interfaces. Observe que o `CComPtr::CoCreateInstance` função de membro é usada para criar o objeto COM, em vez da função do Win32 que tem o mesmo nome.

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` e seus parentes fazem parte da ATL e são definidos em \<atlcomcli. h >. `_com_ptr_t` é declarada em \<comip. h >. O compilador cria especializações `_com_ptr_t` quando ele gera classes de wrapper para as bibliotecas de tipos.

## <a name="example"></a>Exemplo

A ATL também fornece `CComQIPtr`, que tem uma sintaxe mais simples para consultar um objeto COM para recuperar uma interface adicional. No entanto, recomendamos `CComPtr` porque ele faz tudo isso `CComQIPtr` pode fazer e é semanticamente mais consistente com ponteiros de interface brutos COM. Se você usar um `CComPtr` para consultar uma interface, o novo ponteiro de interface é colocado em um parâmetro de saída. Se a chamada falhar, será retornado um HRESULT que é o padrão típico de COM. Com `CComQIPtr`, o valor retornado é o ponteiro em si, e se a chamada falhar, o valor de retorno HRESULT interno não pode ser acessado. Estas duas linhas mostram como mecanismos de manipulação de erros `CComPtr` e `CComQIPtr` são diferentes.

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example"></a>Exemplo

`CComPtr` Fornece uma especialização de IDispatch que permite que ele armazenar ponteiros para os componentes de automação COM e chamar os métodos na interface por meio de associação tardia. `CComDispatchDriver` é um typedef para `CComQIPtr<IDispatch, &IIDIDispatch>`, que é implicitamente conversível para `CComPtr<IDispatch>`. Portanto, quando qualquer um destes três nomes aparece no código, é equivalente a `CComPtr<IDispatch>`. O exemplo a seguir mostra como obter um ponteiro para o modelo de objeto do Microsoft Word usando um `CComPtr<IDispatch>`.

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>Consulte também

[Ponteiros inteligentes (C++ moderno)](../cpp/smart-pointers-modern-cpp.md)
