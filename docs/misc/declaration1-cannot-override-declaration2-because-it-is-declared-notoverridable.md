---
title: "&#39;&lt;d&#233;claration1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;d&#233;claration2&gt;&#39;, car il est d&#233;clar&#233; &#39;NotOverridable&#39; | Microsoft Docs"
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
  - "bc30267"
  - "vbc30267"
helpviewer_keywords: 
  - "BC30267"
ms.assetid: fb1f6797-4e49-442e-a660-59d602132631
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;d&#233;claration1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;d&#233;claration2&gt;&#39;, car il est d&#233;clar&#233; &#39;NotOverridable&#39;
Une déclaration de procédure ou de propriété tente de se substituer à un élément hérité du même nom, mais l’élément hérité est spécifié comme `NotOverridable`.  
  
 **ID d’erreur :** BC30267  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `NotOverridable` de la déclaration de l’élément hérité ou supprimez la déclaration de substitution.  
  
## Voir aussi  
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)