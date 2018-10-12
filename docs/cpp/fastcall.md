---
title: fastcall | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __fastcall_cpp
- __fastcall
- _fastcall
dev_langs:
- C++
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa181349ab01ea2a375bacbb5e23d073a99f3f11
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161236"
---
# <a name="fastcall"></a>__fastcall

**Seção específica da Microsoft**

O **fastcall** convenção de chamada especifica que os argumentos para funções devem ser passados em registros, quando possível. Esta convenção de chamada se aplica somente à arquitetura x86. A lista a seguir mostra a implementação dessa convenção de chamada.

|Elemento|Implementação|
|-------------|--------------------|
|Ordem de passagem de argumentos|Os dois primeiros argumentos de DWORD ou menores encontrados na lista de argumentos da esquerda para a direita são passados em registros de ECX e de EDX; todos os outros argumentos são passados na pilha da direita para a esquerda.|
|Responsabilidade de manutenção de pilha|A função de chamada retira os argumentos da pilha.|
|Convenção de decoração de nome|Sinal de arroba (\@) é prefixado para nomes; um sinal de arroba seguido pelo número de bytes (em decimais) no parâmetro de lista é como sufixo aos nomes.|
|Convenção de conversão de maiúsculas/minúsculas|Nenhuma conversão de maiúsculas/minúsculas é realizada.|

> [!NOTE]
>  As versões futuras do compilador podem usar registros diferentes para armazenar parâmetros.

Usando o [/Gr](../build/reference/gd-gr-gv-gz-calling-convention.md) opção de compilador faz com que cada função no módulo seja compilada como **fastcall** , a menos que a função é declarada usando um atributo conflitante ou o nome da função é `main` .

O **fastcall** palavra-chave é aceita e ignorada pelos compiladores que direcionam o ARM e x64 arquiteturas; em x64 de chip, por convenção, os primeiros quatro argumentos são passados em registros quando possível e argumentos adicionais são passados na pilha. Para obter mais informações, consulte [visão geral do x64 convenções de chamada](../build/overview-of-x64-calling-conventions.md). Em um chip ARM, até quatro argumentos inteiros e oito argumentos de ponto flutuante podem ser passados em registros, e os argumentos adicionais são passados na pilha.

Para funções de classe não estáticas, se a função for definida como fora da linha, o modificador da convenção de chamada não precisará ser especificado na definição fora da linha. Ou seja, para métodos de membro de classe não estática, a convenção de chamada especificada durante a declaração é assumida no ponto de definição. Dada esta definição de classe:

```cpp
struct CMyClass {
   void __fastcall mymethod();
};
```

isto:

```cpp
void CMyClass::mymethod() { return; }
```

equivale a isto:

```cpp
void __fastcall CMyClass::mymethod() { return; }
```

Para compatibilidade com versões anteriores, **fastcall** é um sinônimo de **fastcall** , a menos que a opção de compilador [/Za \(desabilitar extensões de linguagem)](../build/reference/za-ze-disable-language-extensions.md) é especificado.

## <a name="example"></a>Exemplo

No exemplo a seguir, a função `DeleteAggrWrapper` recebe argumentos passados em registros:

```cpp
// Example of the __fastcall keyword
#define FASTCALL    __fastcall

void FASTCALL DeleteAggrWrapper(void* pWrapper);
// Example of the __ fastcall keyword on function pointer
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[Convenções de passagem e nomenclatura de argumentos](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Palavras-chave](../cpp/keywords-cpp.md)