---
title: "D&#233;bogage ASP.NET&#160;: configuration requise | Microsoft Docs"
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
  - "déboguer les applications web ASP.NET, configuration système requise"
  - "déboguer les applications web ASP.NET, conditions de sécurité"
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# D&#233;bogage ASP.NET&#160;: configuration requise
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit les conditions de sécurité et les logiciels requis pour les scénarios de débogage de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] :  
  
-   Débogage local, dans lequel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et l'application Web s'exécutent sur le même ordinateur. Il y a deux versions de ce scénario :  
  
    -   Le code [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] réside sur le système de fichiers.  
  
    -   Le code de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] réside sur un site Web IIS.  
  
-   Débogage distant, dans lequel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] s'exécute sur un ordinateur client et débogue une application Web qui s'exécute sur un ordinateur de serveur distant.  
  
## Conditions de sécurité  
 Pour le débogage distant, les ordinateurs locaux et distants doivent être sur une installation de domaine ou une installation de groupe de travail.  
  
 Pour déboguer le processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vous devez disposer de l'autorisation pour déboguer ce processus. Par défaut, les applications [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] s'exécutent en tant qu'utilisateur **ASPNET**. Si le processus de traitement s'exécute en tant qu'**ASPNET** ou que **SERVICE RÉSEAU**, vous devez disposer de droits d'administrateur pour le déboguer.  
  
 Le nom du processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] varie en fonction du scénario de débogage et de la version d'IIS. Pour plus d'informations, consultez [Comment : rechercher le nom du processus ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Vous pouvez changer le compte d'utilisateur sous lequel s'exécute le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en modifiant le fichier machine.config sur le serveur qui exécute IIS. La meilleure façon de procéder consiste à utiliser le **Gestionnaire IIS**. Pour plus d'informations, consultez [Comment : exécuter le processus de travail sous un compte d'utilisateur](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Si vous modifiez le processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pour qu'il s'exécute sous votre propre compte d'utilisateur, vous n'avez pas besoin d'être administrateur sur le serveur qui exécute IIS.  
  
> [!CAUTION]
>  Avant de modifier le processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pour qu'il s'exécute sous un compte différent, envisagez les conséquences que pourrait avoir un piratage du processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] lors de son exécution sous ce compte. Les comptes d'utilisateur ASPNET et SERVICE RÉSEAU s'exécutent avec des autorisations minimales, réduisant les dommages possibles en cas de piratage du processus. Si vous devez modifier le processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pour qu'il s'exécute sous un compte qui a des autorisations supérieures, le risque de dommage est accru.  
  
## Voir aussi  
 [Débogage d'applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Comment : exécuter le processus de travail sous un compte d'utilisateur](../debugger/how-to-run-the-worker-process-under-a-user-account.md)