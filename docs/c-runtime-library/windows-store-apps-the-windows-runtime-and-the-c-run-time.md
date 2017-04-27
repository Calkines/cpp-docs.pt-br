---
title: Aplicativos da Windows Store, Windows Runtime e C Run-Time | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 001f4894e09a3b2ba9d59238ac6572739eb9f656
ms.lasthandoff: 02/25/2017

---
# <a name="windows-store-apps-the-windows-runtime-and-the-c-run-time"></a>Aplicativos da Windows Store, Windows Runtime  e C Run-Time
[!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] os aplicativos são programas que são executados no [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] que executa em [!INCLUDE[win8](../build/reference/includes/win8_md.md)].  O [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] é um ambiente confiável que controla as funções, variáveis e recursos que estão disponíveis para um [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplicativo. No entanto, por projeto, restrições [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] impedem o uso da maioria dos recursos de biblioteca em tempo de execução do C (CRT) nos aplicativos [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)].  
  
 O [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] não dá suporte aos seguintes recursos de CRT:  
  
-   A maioria das funções de CRT que estão relacionados à funcionalidade sem suporte.  
  
     Por exemplo, um aplicativo [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] não pode criar um processo usando as famílias de rotinas `exec` e `spawn`.  
  
     Quando uma função CRT não tem suporte em um aplicativo [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)], esse fato é observado em seu artigo de referência.  
  
-   Maioria das funções de caracteres multibyte e cadeia de caracteres.  
  
     No entanto, há suporte para texto ANSI e Unicode.  
  
-   Aplicativos de console e argumentos de linha de comando.  
  
     Entretanto, aplicativos de área de trabalho tradicionais ainda dão suporte ao console e a argumentos de linha de comando.  
  
-   Variáveis de ambiente.  
  
-   O conceito de um diretório de trabalho atual.  
  
-   [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplicativos e DLLs estaticamente vinculados a CRT e criados usando as opções [/MT](../build/reference/md-mt-ld-use-run-time-library.md) ou `/MTd` do compilador.  
  
     Ou seja, um aplicativo que usa uma versão estática multithread do CRT.  
  
-   Um aplicativo que é criado usando a opção do compilador [/MDd](../build/reference/md-mt-ld-use-run-time-library.md).  
  
     Ou seja, uma versão específica de depuração, multithread e DLL do CRT. Não há suporte para este aplicativo no [!INCLUDE[win8_appstore_long](../build/reference/includes/win8_appstore_long_md.md)].  
  
 Para obter uma lista completa das funções de CRT que não estão disponíveis em um aplicativo [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] e sugestões para funções alternativas, consulte [funções de CRT sem suporte com /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="see-also"></a>Consulte também  
 [Compatibilidade](../c-runtime-library/compatibility.md)   
 [Funções CRT sem suporte no Windows Runtime](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)   
 [Rotinas de tempo de execução por categoria](../c-runtime-library/run-time-routines-by-category.md)