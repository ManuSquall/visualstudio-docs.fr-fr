---
title: "L’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; ne peut pas &#234;tre g&#233;r&#233;, car il n’est pas accessible &#224; partir de &#39;&lt;nom&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30585"
  - "vbc30585"
helpviewer_keywords: 
  - "BC30585"
ms.assetid: fe039f8f-be6f-4b52-86bd-d551c54b85cd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; ne peut pas &#234;tre g&#233;r&#233;, car il n’est pas accessible &#224; partir de &#39;&lt;nom&gt;&#39;
Vous avez tenté de gérer un événement qui n’est pas accessible. Par exemple, si une variable `Handles` est partagée, la méthode gérant les événements doit également être partagée.  
  
 **ID d’erreur :** BC30585  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que l’événement est accessible.  
  
## Voir aussi  
 [NOT IN BUILD : Événements et gestionnaires d’événements](http://msdn.microsoft.com/fr-fr/95074a0d-1cbc-4221-a95a-964185c7f962)