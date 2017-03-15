---
title: "Erreur&#160;: Impossible d’effectuer automatiquement un pas &#224; pas d&#233;taill&#233; sur le serveur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.causality_no_server_response"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogage distant, erreur de notification"
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Erreur&#160;: Impossible d’effectuer automatiquement un pas &#224; pas d&#233;taill&#233; sur le serveur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L’erreur affiche le message suivant :  
  
 Impossible d’effectuer automatiquement un pas à pas détaillé sur le serveur. Le débogueur n’a pas été notifié avant l’exécution de la procédure distante.  
  
 Cette erreur peut se produire lorsque vous essayez d’effectuer un pas à pas détaillé dans un service Web \(consultez [Exécution pas à pas d’un service Web XML](http://msdn.microsoft.com/fr-fr/8e67de38-bf5f-41cc-a457-1b88ce63d764)\). Elle peut survenir toute les fois que [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n’est pas installé correctement.  
  
 Causes possibles :  
  
-   Le fichier web.config pour votre application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n’affecte pas la valeur "true" au débogage \(consultez [Mode débogage dans les applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)\).  
  
-   Une version de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a été installée après l’installation de Visual Studio.[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] doit être installé avant Visual Studio. Pour résoudre ce problème, dans le **Panneau de configuration** Windows, accédez à **Programmes et Fonctionnalités** afin de réparer votre installation Visual Studio.  
  
## Voir aussi  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Débogage distant](../debugger/remote-debugging.md)