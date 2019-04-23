---
title: '#Importar atributos (C++)'
ms.date: 11/04/2016
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
ms.openlocfilehash: 954dfec50db75c0e3d11f0924b0ee398cd211fe1
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036134"
---
# <a name="import-attributes-c"></a>Atributos #import (C++)
Fornece links para atributos usados com o `#import` diretiva.

**Seção específica da Microsoft**

Os seguintes atributos estão disponíveis para o `#import` diretiva.

|Atributo|Descrição|
|---------------|-----------------|
|[auto_rename](../preprocessor/auto-rename.md)|Renomeia palavras reservadas C++ com dois sublinhados (__) para o nome da variável para resolver possíveis conflitos de nome.|
|[auto_search](../preprocessor/auto-search.md)|Especifica que, quando uma biblioteca de tipos é referenciada com #import e ela mesma referencia outra biblioteca de tipos, o compilador pode fazer um #import implícito para a outra biblioteca de tipos.|
|[embedded_idl](../preprocessor/embedded-idl.md)|Especifica que a biblioteca de tipos é gravada no arquivo .tlh com o código gerado pelo atributo preservado.|
|[exclude](../preprocessor/exclude-hash-import.md)|Exclui itens dos arquivos de cabeçalho da biblioteca de tipos que estão sendo gerados.|
|[high_method_prefix](../preprocessor/high-method-prefix.md)|Especifica um prefixo a ser usado na nomeação de propriedades e métodos de alto nível.|
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|Especifica prefixos alternativos para três métodos da propriedade.|
|[implementation_only](../preprocessor/implementation-only.md)|Suprime geração do arquivo de cabeçalho .tlh (o arquivo de cabeçalho primário).|
|[include()](../preprocessor/include-parens.md)|Desabilita a exclusão automática.|
|[inject_statement](../preprocessor/inject-statement.md)|Insere seu argumento como texto de origem no cabeçalho da biblioteca de tipos.|
|[named_guids](../preprocessor/named-guids.md)|Informa ao compilador para definir e inicializar variáveis GUID no estilo antigo, do formulário `LIBID_MyLib`, `CLSID_MyCoClass`, `IID_MyInterface`, e `DIID_MyDispInterface`.|
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|Desabilita a exclusão automática.|
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|Altera o modo como o compilador gerenciar funções wrapper para métodos da interface dupla.|
|[no_implementation](../preprocessor/no-implementation.md)|Suprime geração do cabeçalho .tli, que contém as implementações das funções de membro do wrapper.|
|[no_namespace](../preprocessor/no-namespace.md)|Especifica que o nome do namespace não é gerado pelo compilador.|
|[no_registry](../preprocessor/no-registry.md)|Diz para o compilador não procurar no Registro por bibliotecas de tipos.|
|[no_search_namespace](../preprocessor/no-search-namespace.md)|Tem a mesma funcionalidade que o [no_namespace](../preprocessor/no-namespace.md) do atributo, mas é usado em bibliotecas de tipos que você usar a diretiva #import com o [auto_search](../preprocessor/auto-search.md) atributo.|
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|Suprime a criação de ponteiros inteligentes para todas as interfaces na biblioteca de tipos.|
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|Instrui o compilador a gerar funções wrapper de nível baixo para dispinterface métodos e propriedades que chamam `IDispatch::Invoke` e retornar o código de erro HRESULT.|
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|Suprime a geração de funções de wrapper de tratamento de erros e [propriedade](../cpp/property-cpp.md) declarações que usam essas funções wrapper.|
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|Especifica um prefixo diferente para evitar colisões de nome.|
|[raw_native_types](../preprocessor/raw-native-types.md)|Desabilita o uso de classes de suporte COM nas funções wrapper de alto nível e força o uso de tipos de dados de nível baixo.|
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|Especifica prefixos alternativos para três métodos da propriedade.|
|[rename](../preprocessor/rename-hash-import.md)|Soluciona os problemas de colisão de nome.|
|[rename_namespace](../preprocessor/rename-namespace.md)|Renomeia o namespace que contém o conteúdo da biblioteca de tipos.|
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|Tem a mesma funcionalidade que o [rename_namespace](../preprocessor/rename-namespace.md) do atributo, mas é usado em bibliotecas de tipos que você usar a diretiva #import com o [auto_search](../preprocessor/auto-search.md) atributo.|
|[tlbid](../preprocessor/tlbid.md)|Permite carregar bibliotecas diferentes de biblioteca de tipos primárias.|

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[#import diretiva](../preprocessor/hash-import-directive-cpp.md)