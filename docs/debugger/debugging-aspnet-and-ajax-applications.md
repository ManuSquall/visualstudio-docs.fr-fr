---
title: "D&#233;bogage d&#39;applications ASP.NET et AJAX | Microsoft Docs"
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
  - "déboguer (ASP.NET), à propos du débogage ASP.NET"
  - "déboguer les applications Web ASP.NET"
  - "débogage, WCF"
  - "WCF, débogage"
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# D&#233;bogage d&#39;applications ASP.NET et AJAX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le débogage d'applications Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ressemble au débogage d'un Windows Form ou d'une application Windows quelconque, ces applications impliquant dans l'un et l'autre cas des contrôles et des événements.  Il existe néanmoins aussi des différences fondamentales entre elles :  
  
-   Assurer le suivi de l'état est plus complexe dans une application Web.  
  
-   Dans une application Windows, le code à déboguer se trouve essentiellement rassemblé au même endroit ; dans une application Web, le code peut se trouver sur le client et sur le serveur.  Alors que le code [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] se trouve entièrement sur le serveur, il peut y avoir également du code JavaScript ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] sur le client.  
  
## Dans cette section  
 [Préparation d'un débogage ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Décrit les étapes nécessaires pour activer le débogage d'applications [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
 [Débogage d'applications Web](../debugger/debugging-web-applications.md)  
 Explique comment déboguer une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], y compris des applications de script compatibles AJAX.  
  
## Rubriques connexes  
 [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)  
 Explique pourquoi Uniquement mon code doit être activé pour le débogage d'exceptions [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)  
 Présente quelques techniques et outils qui peuvent vous aider à déboguer votre code AJAX plus facilement.  
  
 [Utilisation d'IntelliTrace](../debugger/intellitrace.md)  
 Déboguez votre code plus rapidement à l'aide de IntelliTrace pour enregistrer et tester un historique de l'état de votre application sans redémarrer l'application fréquemment.  Vous pouvez consulter les informations sur les événements et les appels qui surviennent pendant l'exécution de votre application et commencer le débogage à temps.  Requiert Visual Studio Ultimate.  
  
## Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage d'applications et de scripts Web](../debugger/debugging-web-applications-and-script.md)   
 [Paramètres et préparation du débogage](../debugger/debugger-settings-and-preparation.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)