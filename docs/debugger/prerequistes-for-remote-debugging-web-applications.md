---
title: "Conditions requises pour le d&#233;bogage &#224; distance d&#39;applications Web | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "déboguer les applications Web ASP.NET, serveurs distants"
  - "débogage distant, composants requis"
  - "serveurs distants, déboguer les applications Web"
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Conditions requises pour le d&#233;bogage &#224; distance d&#39;applications Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Avec le débogueur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez déboguer une application Web de façon transparente, sur l'ordinateur local ou sur un serveur distant.  Cela signifie que le débogueur fonctionne de la même façon et vous permet d'utiliser les mêmes fonctionnalités sur l'un ou sur l'autre.  Cependant, afin que le débogage distant fonctionne correctement, vous devez respecter certaines conditions.  
  
-   Les composants de débogage distant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doivent être installés sur le serveur que vous souhaitez déboguer.  Pour plus d'informations, consultez [Configuration du débogage distant](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
-   Par défaut, le processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] s'exécute comme un processus utilisateur ASPNET.  En conséquence, vous devez avoir des privilèges d'administrateur sur l'ordinateur où [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] s'exécute pour le déboguer.  Le nom du processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] varie en fonction du scénario de débogage et de la version d'IIS.  Pour plus d'informations, consultez [Comment : rechercher le nom du processus ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## Voir aussi  
 [Débogage d'applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Configuration requise](../debugger/aspnet-debugging-system-requirements.md)