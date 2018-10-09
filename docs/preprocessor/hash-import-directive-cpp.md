---
title: '#Importar diretiva (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#import'
dev_langs:
- C++
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60397fea85e3fd121469ae4568dac18fa6b9ddb1
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890316"
---
# <a name="import-directive-c"></a>Diretiva #import (C++)
**Específico do C++**  
  
Usada para incorporar informações de uma biblioteca de tipos. O conteúdo da biblioteca de tipos é convertido em classes do C++, a maioria descrevendo as interfaces COM.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
#import "filename" [attributes]  
#import <filename> [attributes]  
```  
  
### <a name="parameters"></a>Parâmetros  
*filename*  
Especifica a biblioteca de tipos a ser importada. *nome de arquivo* pode ser uma das seguintes opções:  
  
- O nome de um arquivo que contém uma biblioteca de tipos, como um arquivo .olb, .tlb ou .dll. A palavra-chave **arquivo:**, pode preceder cada nome de arquivo.  
  
- O progid de um controle na biblioteca de tipos. A palavra-chave **progid:**, pode preceder cada progid. Por exemplo:  
  
    ```  
    #import "progid:my.prog.id.1.5"  
    ```  
  
     Para obter mais informações sobre progids, consulte [especificando a ID de localização e o número de versão](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).  
  
     Observe que, ao compilar com um compilador cruzado em um sistema operacional de 64 bits, o compilador será capaz de ler apenas o hive do Registro de 32 bits. Pode ser conveniente usar o compilador de 64 bits nativo para criar e registrar uma biblioteca de tipos de 64 bits.  
  
- A ID da biblioteca de tipos. A palavra-chave **libid:**, pode preceder cada ID de biblioteca. Por exemplo:  
  
    ```  
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")  
    ```  
  
     Se você não especificar a versão ou o lcid, o [regras](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) que são aplicados à **progid:** também são aplicadas às **libid:**.  
  
- Um arquivo executável (.exe).  
  
- Um arquivo de biblioteca (.dll) que contém um recurso de biblioteca de tipos (como .ocx).  
  
- Um documento composto que contém uma biblioteca de tipos.  
  
- Qualquer outro formato de arquivo que possa ser compreendido pela **LoadTypeLib** API.  
  
*Atributos*  
Um ou mais [#import atributos](#_predir_the_23import_directive_import_attributes). Separe os atributos com espaços ou vírgulas. Por exemplo:  
  
```  
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only  
```  
  
-ou-  
  
```  
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only  
```  
  
## <a name="remarks"></a>Comentários  
  
##  <a name="_predir_the_23import_directive_searchorderforfilename"></a> Ordem de pesquisa de nome de arquivo  

*nome do arquivo* é opcionalmente precedido por uma especificação de diretório. O nome do arquivo deve nomear um arquivo existente. A diferença entre os dois formatos de sintaxe é a ordem em que o pré-processador procura os arquivos de biblioteca de tipos quando o caminho é especificado de forma incompleta.  
  
|Formato de sintaxe|Ação|  
|-----------------|------------|  
|Forma entre aspas|Instrui o pré-processador a procurar por arquivos de biblioteca de tipo primeiramente no diretório do arquivo que contém o **#import** instrução e, em seguida, nos diretórios de quaisquer arquivos que incluem (`#include`) desse arquivo. Em seguida, o pré-processador pesquisa ao longo dos caminhos mostrados abaixo.|  
|Forma de colchete angular|Instrui o pré-processador a procurar arquivos de biblioteca de tipos ao longo dos seguintes caminhos:<br /><br /> 1.  O `PATH` lista de caminhos da variável de ambiente<br />2.  O `LIB` lista de caminhos da variável de ambiente<br />3.  O caminho especificado por /I (adicionais diretórios de inclusão) a opção de compilador, exceto que o compilador está procurando por uma biblioteca de tipos que foi referenciada em outra biblioteca de tipos com o [no_registry](../preprocessor/no-registry.md) atributo.|  
  
##  <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a> Especificando a ID de localização e o número de versão  

Ao especificar um progid, você também pode especificar a ID de localização e o número de versão do progid. Por exemplo:  
  
```  
#import "progid:my.prog.id" lcid("0") version("4.0)  
```  
  
Se você não especificar uma ID de localização, um progid será escolhido de acordo com as seguintes regras:  
  
- Se houver apenas uma ID de localização, essa será usada.  
  
- Se houver mais de uma ID de localização, será usada a primeira delas com número de versão 0, 9 ou 409.  
  
- Se houver mais de uma ID de localização e nenhuma delas for 0, 9 ou 409, será usada a última.  
  
- Se você não especificar um número de versão, será usada a versão mais recente.  
  
##  <a name="_predir_the_23import_directive_header_files_created_by_import"></a> Arquivos de cabeçalho criados por importação  

**#import** cria dois arquivos de cabeçalho que reconstroem o conteúdo da biblioteca de tipo no código-fonte C++. O arquivo de cabeçalho principal é semelhante ao produzido pelo compilador de MIDL (linguagem IDL da Microsoft), mas com código gerado pelo compilador e dados adicionais. O [arquivo de cabeçalho principal](#_predir_the_primary_type_library_header_file) tem o mesmo nome base da biblioteca de tipos, além de um. Extensão TLH. O arquivo de cabeçalho secundário tem o mesmo nome base que a biblioteca de tipos, com a extensão .TLI. Ele contém as implementações para funções de membro geradas pelo compilador e está incluído (`#include`) no arquivo de cabeçalho principal.  
  
Se estiver importando uma propriedade dispinterface que usa parâmetros byref, #import não irá gerar o declspec ([propriedade](../cpp/property-cpp.md)) instrução para a função.  
  
Os dois arquivos de cabeçalho são colocados no diretório de saída especificado pela opção /Fo (nomear arquivo de objeto). Em seguida, eles são lidos e compilados pelo compilador como se o arquivo de cabeçalho principal tivesse sido nomeado por uma política `#include`.  
  
As seguintes otimizações de compilador vêm com o **#import** diretiva:  
  
- O arquivo de cabeçalho, quando é criado, recebe o mesmo carimbo de data/hora que a biblioteca de tipos.  
  
- Quando **#import** é processado, o compilador verifica primeiro se o cabeçalho existe e está atualizado. Em caso positivo, ele não precisará ser recriado.  
  
O **#import** diretiva também participa da recompilação mínima e pode ser colocada em um arquivo de cabeçalho pré-compilado. Ver [criando arquivos de cabeçalho pré-compilado](../build/reference/creating-precompiled-header-files.md) para obter mais informações.  
  
###  <a name="_predir_the_primary_type_library_header_file"></a> Arquivo de cabeçalho de biblioteca de tipo principal  
O arquivo de cabeçalho principal da biblioteca de tipos consiste em sete seções:  
  
- Texto clichê de título: inclui comentários, a instrução `#include` para COMDEF.H (que define algumas macros padrão usadas no cabeçalho) e outras informações de configuração.  
  
- Referências de encaminhamento e typedefs: consiste em declarações de estrutura como `struct IMyInterface` e typedefs.  
  
- Declarações de ponteiro inteligente: A classe de modelo `_com_ptr_t` é uma implementação de ponteiro inteligente que encapsula ponteiros de interface e elimina a necessidade de chamar `AddRef`, `Release`, `QueryInterface` funções. Além disso, ela oculta a chamada `CoCreateInstance` na criação de um novo objeto COM. Esta seção usa a instrução de macro `_COM_SMARTPTR_TYPEDEF` para estabelecer typedefs de interfaces COM como especializações de modelo a [com_ptr_t](../cpp/com-ptr-t-class.md) classe de modelo. Por exemplo, para a interface `IMyInterface`, o. Arquivos TLH contém:  
  
    ```  
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
    ```  
  
     que o compilador expande para:  
  
    ```  
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;  
    ```  
  
     O tipo `IMyInterfacePtr` pode então ser usado no lugar do ponteiro de interface bruto `IMyInterface*`. Consequentemente, não é necessário chamar as várias `IUnknown` funções de membro  
  
- Declarações de TypeInfo: consiste basicamente em definições de classe e outros itens que expõem os itens individuais de typeinfo retornados por `ITypeLib:GetTypeInfo`. Nesta seção, cada typeinfo da biblioteca de tipos é refletido no cabeçalho em um formato que depende das informações de `TYPEKIND`.  
  
- Definição de GUID de estilo antigo opcional: contém inicializações das constantes de GUID nomeadas. Esses são os nomes do formulário `CLSID_CoClass` e `IID_Interface`, semelhantes aos gerados pelo compilador MIDL.  
  
- Instrução `#include` para o cabeçalho secundário da biblioteca de tipos.  
  
- Texto clichê de rodapé: atualmente, inclui `#pragma pack(pop)`.  
  
Todas as seções, exceto a seção de texto clichê título clichê e rodapé, são colocadas em um namespace com o nome especificado pelo `library` instrução no arquivo IDL original. Você pode usar os nomes do cabeçalho de biblioteca de tipos por meio de uma qualificação explícita com o nome do namespace ou incluindo a instrução a seguir:  
  
```  
using namespace MyLib;  
```  
  
imediatamente após o **#import** instrução no código-fonte.  
  
O namespace pode ser suprimido usando o [no_namespace](#_predir_no_namespace) atributo da **#import** diretiva. No entanto, suprimir o namespace pode resultar em colisões de nomes. O namespace também pode ser renomeado com o [rename_namespace](#_predir_rename_namespace) atributo.  
  
O compilador fornece o caminho completo para qualquer dependência de biblioteca de tipos exigida pela biblioteca que esteja em processamento. O caminho é escrito, na forma de comentários, no cabeçalho da biblioteca de tipos (.TLH) gerado pelo compilador para cada biblioteca de tipos processada.  
  
Se uma biblioteca de tipos incluir referências a tipos definidos em outras bibliotecas, o arquivo .TLH incluirá comentários do seguinte tipo:  
  
```  
//  
// Cross-referenced type libraries:  
//  
//  #import "c:\path\typelib0.tlb"  
//  
```  
  
O nome do arquivo real na **#import** comentário é o caminho completo da biblioteca de tipos com referência cruzada, conforme armazenado no registro. Se você encontrar erros devidos à ausência de definições de tipo, verifique os comentários no cabeçalho do .TLH para saber quais bibliotecas de tipos dependentes precisarão ser importadas primeiro. Erros prováveis são erros de sintaxe (por exemplo, C2143, C2146, C2321), C2501 (especificadores de declarações ausentes) ou C2433 ("embutido" não permitido na declaração de dados) ao compilar o arquivo .TLI.  
  
Você deve determinar qual a dependência de comentários não são fornecidos de outra forma por cabeçalhos do sistema e, em seguida, fornecem uma **#import** diretiva em algum momento antes do **#import** diretiva do dependente biblioteca de tipos para resolver os erros.  

##  <a name="_predir_the_23import_directive_import_attributes"></a> atributos de #import

**#import** pode opcionalmente incluir um ou mais atributos. Esses atributos instruem o compilador a modificar o conteúdo dos cabeçalhos de biblioteca de tipos. Uma barra invertida (**\\**) símbolo pode ser usado para incluir linhas adicionais em um único **#import** instrução. Por exemplo:  
  
```  
#import "test.lib" no_namespace \  
   rename("OldName", "NewName")  
```  
  
Para obter mais informações, consulte [#import atributos](../preprocessor/hash-import-attributes-cpp.md).  
  
**FIM de específico de C++**  
  
## <a name="see-also"></a>Consulte também  

[Diretivas do pré-processador](../preprocessor/preprocessor-directives.md)<br/>
[Suporte para COM do compilador](../cpp/compiler-com-support.md)