---
title: '/ZC: referencebinding (Impor regras de associação de referência)'
ms.date: 03/06/2018
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
ms.openlocfilehash: 9dfe8f5b4713d9567f6e98af6685c552fb51160e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316100"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/ZC: referencebinding (Impor regras de associação de referência)

Quando o **/ZC: referencebinding** opção for especificada, o compilador não permite uma referência lvalue non-const associar a um temporário.

## <a name="syntax"></a>Sintaxe

> **/Zc:referenceBinding**[**-**]

## <a name="remarks"></a>Comentários

Se **/ZC: referencebinding** for especificado, o compilador seguirá a seção 8.5.3 de c++11 padrão e não permite expressões que associam um tipo definido pelo usuário temporário a uma referência lvalue non-const. Por padrão, ou se **/Zc:referenceBinding-** for especificado, o compilador permite que tais expressões como uma extensão da Microsoft, mas é emitido um aviso de nível 4. Para segurança de código, portabilidade e conformidade, recomendamos que você use **/ZC: referencebinding**.

O **/ZC: referencebinding** opção está desativada por padrão. O [/permissive--](permissive-standards-conformance.md) opção de compilador define implicitamente essa opção, mas ele pode ser substituído usando **/Zc:referenceBinding-**.

## <a name="example"></a>Exemplo

Este exemplo mostra a extensão da Microsoft que permite que um temporário de um tipo definido pelo usuário a ser associado a uma referência lvalue non-const.

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

void main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

Para obter mais informações sobre problemas de conformidade no Visual C++, consulte [comportamento não padrão](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. Selecione o **propriedades de configuração** > **C/C++** > **linha de comando** página de propriedades.

1. Modificar a **opções adicionais** propriedade incluir **/ZC: referencebinding** e, em seguida, escolha **Okey**.

## <a name="see-also"></a>Consulte também

[Opções do compilador MSVC](compiler-options.md)<br/>
[Sintaxe da linha de comando do compilador MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (conformidade)](zc-conformance.md)<br/>
