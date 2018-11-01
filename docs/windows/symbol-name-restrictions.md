---
title: Restrições de nome do símbolo
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.restrictions.name
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
ms.assetid: 4ae7f695-ca86-4f4b-989a-fe6f89650ff7
ms.openlocfilehash: 7b6d8804dc7f3c9768dc9e86fde0e708f67c43fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624842"
---
# <a name="symbol-name-restrictions"></a>Restrições de nome do símbolo

As restrições em nomes de símbolos são da seguinte maneira:

- Todos os [símbolos](../windows/symbols-resource-identifiers.md) deve ser exclusivo dentro do escopo do aplicativo. Isso impede que as definições conflitantes do símbolo nos arquivos de cabeçalho.

- Caracteres válidos para um nome de símbolo incluem A-Z, a-z, 0 a 9 e sublinhados (_).

- Nomes de símbolo não podem começar com um número e são limitados a 247 caracteres.

- Nomes de símbolo não podem conter espaços.

- Nomes de símbolos não diferenciam maiusculas de minúsculas, mas no caso da primeira definição de símbolo é preservado. O arquivo de cabeçalho que define os símbolos é usado pelo compilador/editor de recursos e programas do C++ para fazer referência a recursos definidos em um arquivo de recurso. Dois nomes de símbolo que diferem apenas em maiusculas, o programa de C++ verá dois símbolos separados, enquanto o compilador/editor de recurso verá os dois nomes como uma referência a um único símbolo.

   > [!NOTE]
   > Se você não seguir o esquema de nome de símbolo padrão (ID*_[keyword]) descritas abaixo, e seu nome de símbolo, por acaso, é o mesmo como uma palavra-chave conhecida do compilador do script de recurso, tentar criar o arquivo de script de recurso resulta em erro aparentemente aleatório geração que é difícil de diagnosticar. Para evitar isso, seguem o esquema de nomenclatura padrão.

Nomes de símbolos têm prefixos descritivos que indicam o tipo de recurso ou objeto que eles representam. Esses prefixos descritivos começam com a ID da combinação de texto. O Microsoft Foundation Class Library (MFC) usa as convenções de nomenclatura de símbolo mostradas na tabela a seguir.

|Categoria|Prefixo|Use|
|--------------|------------|---------|
|Recursos|IDR IDD _ IDC IDI_ IDB_|Acelerador ou menu (e recursos associados ou personalizados) caixa de diálogo Bitmap do ícone de Cursor|
|Itens de menu|ID _|Item de menu|
|Comandos|ID _|Comando|
|Controles e janelas filho|IDC|Controle|
|Cadeias de caracteres|IDS _|Cadeia de caracteres na tabela de cadeia de caracteres|
|MFC|AFX_|Reservado para símbolos predefinidos do MFC|

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte também

[Alterando um símbolo ou um nome de símbolo (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[Restrições de valor de símbolo](../windows/symbol-value-restrictions.md)<br/>
[IDs de símbolos predefinidos](../windows/predefined-symbol-ids.md)