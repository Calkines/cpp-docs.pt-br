---
title: /Gh (habilitar função de gancho _penter)
ms.date: 11/04/2016
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: bf7734a7b81c9550c060d43c2eabf5cb05332407
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292573"
---
# <a name="gh-enable-penter-hook-function"></a>/Gh (habilitar função de gancho _penter)

Faz com que uma chamada para o `_penter` função no início de cada método ou função.

## <a name="syntax"></a>Sintaxe

```
/Gh
```

## <a name="remarks"></a>Comentários

O `_penter` função não faz parte de qualquer biblioteca e cabe a você fornecer uma definição para `_penter`.

A menos que você planeja chamar explicitamente `_penter`, você não precisa fornecer um protótipo. A função deve aparecer como se tivesse o protótipo a seguir, e ele deve enviar por push o conteúdo de todos os registros na entrada e pop o conteúdo inalterado na saída:

```
void __declspec(naked) __cdecl _penter( void );
```

Essa declaração não está disponível para projetos de 64 bits.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. Clique o **C/C++** pasta.

1. Clique o **linha de comando** página de propriedades.

1. Digite a opção de compilador na **opções adicionais** caixa.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Exemplo

O código a seguir, quando compilado com **/Gh**, mostra como `_penter` é chamado duas vezes; uma vez ao Inserir função `main` uma vez ao Inserir função `x`.

```cpp
// Gh_compiler_option.cpp
// compile with: /Gh
// processor: x86
#include <stdio.h>
void x() {}

int main() {
   x();
}

extern "C" void __declspec(naked) __cdecl _penter( void ) {
   _asm {
      push eax
      push ebx
      push ecx
      push edx
      push ebp
      push edi
      push esi
    }

   printf_s("\nIn a function!");

   _asm {
      pop esi
      pop edi
      pop ebp
      pop edx
      pop ecx
      pop ebx
      pop eax
      ret
    }
}
```

```Output
In a function!
In a function!
```

## <a name="see-also"></a>Consulte também

[Opções do compilador MSVC](compiler-options.md)<br/>
[Sintaxe da linha de comando do compilador MSVC](compiler-command-line-syntax.md)
