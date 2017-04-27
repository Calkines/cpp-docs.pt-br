---
title: Baixar, instalar e configurar a carga de trabalho do Linux | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
author: BrianPeek
ms.author: brpeek
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
ms.sourcegitcommit: dff1e9e03911f65dfcffcd078e0739224f73f4aa
ms.openlocfilehash: 09ce0024b7a98729b28968fff081ed105b5463e1

---

# <a name="download-install-and-setup-the-linux-workload"></a>Baixar, instalar e configurar a carga de trabalho do Linux

## <a name="visual-studio-setup"></a>Configuração do Visual Studio
1. Inicie o instalador do Visual Studio e selecione a carga de trabalho **Desenvolvimento Linux com C++**.

   ![Visual C++ para extensão de desenvolvimento do Linux](media/linuxworkload.png)

2. Clique em **Instalar** para continuar a instalação.

## <a name="linux-setup"></a>Configuração do Linux
O computador Linux de destino deve ter **openssh-server**, **g++**, **gdb** e **gdbserver** instalados e o daemon ssh deve estar em execução.  Se eles ainda não estiverem presentes, você poderá instalá-los da seguinte maneira:
 
1. Em um prompt de shell no seu computador Linux, execute:

   `sudo apt-get install openssh-server g++ gdb gdbserver`

   Sua senha raiz pode ser solicitada devido ao comando sudo.  Nesse caso, insira-a e continue.  Depois de concluído, esses serviços e ferramentas serão instaladas.

1. Verifique se o serviço ssh está em execução no seu computador Linux executando:

   `sudo service ssh start`
   
   Isso iniciará o serviço e o executará em segundo plano, pronto para aceitar as conexões.



<!--HONumber=Feb17_HO4-->

