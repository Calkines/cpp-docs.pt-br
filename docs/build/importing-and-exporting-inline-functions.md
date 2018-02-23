---
title: "Importando e exportando funções embutidas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a6f8d159a1537cdfee02d45805632ba9ad4afa7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="importing-and-exporting-inline-functions"></a>Importando e exportado funções embutidas
Funções importadas podem ser definidas como embutidos. O efeito é aproximadamente o mesmo que definir um padrão de função embutida; chamadas para a função são expandidas em código embutido, assim como uma macro. Isso é útil principalmente como uma maneira de dar suporte a C++ classes em uma DLL que embutido pode alguns de seus membros funções para maior eficiência.  
  
 Um recurso de uma função embutida importado é que você pode obter seu endereço em C++. O compilador retorna o endereço da cópia da função embutida que residem na DLL. Outro recurso de funções embutidas importado é que você pode inicializar dados estáticos de locais da função importada, ao contrário dos dados importados global.  
  
> [!CAUTION]
>  Você deve ter cuidado quando fornecendo importado funções embutidas, pois eles podem criar a possibilidade de conflitos de versão. Uma função embutida obtém expandida em código do aplicativo; Portanto, se você posteriormente reescrever a função, ele não é atualizado, a menos que o aplicativo em si é recompilado. (Normalmente, as funções DLL podem ser atualizadas sem recompilar os aplicativos que os utilizam.)  
  
## <a name="what-do-you-want-to-do"></a>O que você deseja fazer?  
  
-   [Exportação de uma DLL](../build/exporting-from-a-dll.md)  
  
-   [Exportação de uma DLL usando. Arquivos DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar de uma DLL usando dllexport](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar usando AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funções C++ para uso em executáveis da linguagem C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Determinar qual método de exportação a ser usado](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar para um aplicativo usando __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
## <a name="see-also"></a>Consulte também  
 [Importando e exportando](../build/importing-and-exporting.md)