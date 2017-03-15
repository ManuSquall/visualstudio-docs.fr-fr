---
title: "Erreur&#160;: Impossible de se connecter &#224; l&#39;ordinateur &lt;nom&gt;. L&#39;ordinateur est introuvable sur le r&#233;seau. | Microsoft Docs"
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
  - "vs.debug.remote.dcom_disabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DCOM, erreur : impossible de se connecter"
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erreur&#160;: Impossible de se connecter &#224; l&#39;ordinateur &lt;nom&gt;. L&#39;ordinateur est introuvable sur le r&#233;seau.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ce problème se produit si l'une des conditions suivantes est remplie :  
  
-   Votre connexion à l'ordinateur distant a été interrompue.  
  
-   Votre compte d'utilisateur sur l'ordinateur distant est désactivé.  
  
-   Votre mot de passe sur l'ordinateur distant a expiré.  
  
### Pour résoudre ce problème  
  
-   Assurez\-vous que l'ordinateur local et l'ordinateur distant se trouvent dans le même réseau.  Pour cela, à l'aide de l'Explorateur Microsoft Windows \(ou de l'Explorateur de fichiers\), tentez d'accéder à l'ordinateur distant.  
  
     — et —  
  
-   Assurez\-vous que le compte d'utilisateur que vous utilisez pour vous connecter à l'ordinateur distant est activé.  
  
     — et —  
  
-   Assurez\-vous que le mot de passe que vous utilisez pour vous connecter à l'ordinateur distant est valide et n'a pas expiré.  
  
## Voir aussi  
 [Configurer les outils de contrôle à distance sur le périphérique](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [Paramètres et préparation du débogage](../debugger/debugger-settings-and-preparation.md)