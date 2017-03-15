---
title: "Erreur&#160;: L&#39;ordinateur distant n&#39;a pas pu initier les communications DCOM | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.unmarshal_callback_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erreur&#160;: L&#39;ordinateur distant n&#39;a pas pu initier les communications DCOM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une erreur DCOM s'est produite lorsque l'ordinateur distant a tenté de communiquer avec l'ordinateur local.  L'ordinateur local est l'ordinateur qui  
  
 exécute Visual Studio.  Cette erreur peut se produire pour plusieurs raisons :  
  
-   L'ordinateur local a un pare\-feu activé.  
  
-   L'authentification Windows de l'ordinateur distant vers l'ordinateur local ne fonctionne pas.  
  
### Pour corriger cette erreur  
  
1.  Si le Pare\-feu Windows est activé sur l'ordinateur local, consultez [Configurer les outils de contrôle à distance sur le périphérique](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md) pour savoir comment configurer le Pare\-feu pour le débogage local.  
  
2.  Testez l'authentification Windows en essayant d'ouvrir un partage de fichiers sur l'ordinateur local du serveur distant.  
  
3.  Pour restaurer l'authentification Windows, tentez de redémarrer les deux ordinateurs.  Vérifiez si les journaux des événements de l'ordinateur local ou distant contiennent des erreurs Kerberos et contactez les administrateurs de domaines pour les problèmes connus.  
  
## Voir aussi  
 [Configurer les outils de contrôle à distance sur le périphérique](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)