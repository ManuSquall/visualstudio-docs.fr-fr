---
title: "&#39;&lt;nom_membre&gt;&#39; n’est pas d&#233;clar&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30816"
  - "bc30816"
helpviewer_keywords: 
  - "BC30816"
ms.assetid: d6704bed-bb76-47c6-ac28-09608d5e6912
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_membre&gt;&#39; n’est pas d&#233;clar&#233;
'`<membername>`' n’est pas déclaré. La fonctionnalité d’objet `Debug` est disponible dans `System.Diagnostics.Debug` dans l’assembly `System`.  
  
 Le nom du membre spécifié est introuvable.  
  
 **ID d’erreur :** BC30816  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l’orthographe du membre.  
  
2.  Utilisez une instruction `Imports` ou des membres qualifiés complets définis dans d’autres espaces de noms. Par exemple, la fonction `WriteLine` est déclarée dans l’espace de noms `System.Diagnostics.Debug`.  
  
## Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)