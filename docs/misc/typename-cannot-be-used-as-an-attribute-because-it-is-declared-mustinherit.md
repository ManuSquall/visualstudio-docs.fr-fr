---
title: "&#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre utilis&#233; en tant qu’attribut, car il est d&#233;clar&#233; &#39;MustInherit&#39; | Microsoft Docs"
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
  - "vbc31506"
  - "bc31506"
helpviewer_keywords: 
  - "BC31506"
ms.assetid: ea2baf3d-b8e8-4738-9b6d-53409fc4d282
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre utilis&#233; en tant qu’attribut, car il est d&#233;clar&#233; &#39;MustInherit&#39;
Les classes d’attributs personnalisés ne peuvent pas être déclarées en tant que `MustInherit`.  
  
 **ID d’erreur :** BC31506  
  
### Pour corriger cette erreur  
  
-   Supprimez le modificateur `MustInherit` des attributs personnalisés.  
  
## Voir aussi  
 <xref:System.AttributeUsageAttribute>   
 [NOT IN BUILD : Attributs personnalisés en Visual Basic](http://msdn.microsoft.com/fr-fr/d72d8a5c-8f64-4614-b15b-cad66845d047)