---
title: Conditions préalables pour le débogage des Applications Web à distance | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 448e6e7705e4df7330abce0e919adc705721102c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227290"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Conditions requises pour le débogage à distance d'applications Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avec le débogueur de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous pouvez déboguer une application Web de façon transparente, sur l'ordinateur local ou sur un serveur distant. Cela signifie que le débogueur fonctionne de la même façon et vous permet d'utiliser les mêmes fonctionnalités sur l'un ou sur l'autre. Cependant, afin que le débogage distant fonctionne correctement, vous devez respecter certaines conditions.  
  
-   Les composants de débogage distant [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] doivent être installés sur le serveur que vous souhaitez déboguer. Pour plus d’informations, consultez [configuration du débogage distant](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
-   Par défaut, le processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] s'exécute comme un processus utilisateur ASPNET. En conséquence, vous devez avoir des privilèges d'administrateur sur l'ordinateur où [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] s'exécute pour le déboguer. Le nom du processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varie en fonction du scénario de débogage et de la version d'IIS. Pour plus d'informations, consultez [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage des Applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Configuration système requise](../debugger/aspnet-debugging-system-requirements.md)



