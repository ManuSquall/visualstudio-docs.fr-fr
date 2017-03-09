---
title: "&#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre utilis&#233; en tant qu’attribut car il n’h&#233;rite pas de &#39;System.Attribute&#39; | Microsoft Docs"
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
  - "vbc31504"
  - "bc31504"
helpviewer_keywords: 
  - "BC31504"
ms.assetid: 37517623-5099-4db9-a461-f2f5daa4957b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre utilis&#233; en tant qu’attribut car il n’h&#233;rite pas de &#39;System.Attribute&#39;
Une tentative s’est produite d’utiliser une classe qui n’est pas dérivée de `System.Attribute`.  
  
 **ID d’erreur :** BC31504  
  
### Pour corriger cette erreur  
  
1.  Définissez des attributs personnalisés en tant que classes qui dérivent de `System.Attribute` en ajoutant une instruction `Imports` à la première ligne de code dans la classe.  
  
## Voir aussi  
 <xref:System.AttributeUsageAttribute>   
 [NOT IN BUILD : Attributs personnalisé en Visual Basic](http://msdn.microsoft.com/fr-fr/d72d8a5c-8f64-4614-b15b-cad66845d047)