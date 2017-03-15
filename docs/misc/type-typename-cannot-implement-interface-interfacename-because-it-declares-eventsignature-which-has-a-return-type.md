---
title: "Le type &#39;&lt;nom_type&gt;&#39; ne peut pas impl&#233;menter l’interface &#39;&lt;nom_interface&gt;&#39;, car il d&#233;clare &#39;&lt;signature_&#233;v&#233;nement&gt;&#39; qui a un type de retour. | Microsoft Docs"
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
  - "bc30945"
  - "vbc30945"
helpviewer_keywords: 
  - "BC30945"
ms.assetid: 4f26e71a-949d-4103-b565-35cc8e833d29
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type &#39;&lt;nom_type&gt;&#39; ne peut pas impl&#233;menter l’interface &#39;&lt;nom_interface&gt;&#39;, car il d&#233;clare &#39;&lt;signature_&#233;v&#233;nement&gt;&#39; qui a un type de retour.
Une classe ou une structure tente d’implémenter une interface qui déclare un événement qui retourne une valeur.  
  
 Actuellement, Visual Basic ne prend pas en charge la déclaration d’événements qui retournent des valeurs.  
  
 **ID d’erreur :** BC30945  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction `Implements` de la définition de la classe ou de la structure, ou implémentez une autre interface.  
  
## Voir aussi  
 [NOT IN BUILD : Événements et gestionnaires d’événements](http://msdn.microsoft.com/fr-fr/95074a0d-1cbc-4221-a95a-964185c7f962)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NOT IN BUILD : Implements, mot clé et instruction](http://msdn.microsoft.com/fr-fr/b96560f7-6413-480f-a1e2-f80253bab5be)