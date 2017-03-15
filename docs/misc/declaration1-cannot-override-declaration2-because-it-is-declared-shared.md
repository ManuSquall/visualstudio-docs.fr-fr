---
title: "&#39;&lt;d&#233;claration1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;d&#233;claration2&gt;&#39;, car il est d&#233;clar&#233; &#39;Shared&#39; | Microsoft Docs"
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
  - "vbc30268"
  - "bc30268"
helpviewer_keywords: 
  - "BC30268"
ms.assetid: d011fb26-6236-462e-9173-622f8bbeb536
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;d&#233;claration1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;d&#233;claration2&gt;&#39;, car il est d&#233;clar&#233; &#39;Shared&#39;
Une déclaration de procédure ou de propriété tente de se substituer à un élément hérité du même nom, mais l’élément hérité est spécifié comme `Shared`. Les éléments partagés ne sont pas associés à une instance de la classe pour ne pas être substitués.  
  
 **ID d’erreur :** BC30268  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Shared` de l’élément hérité ou supprimez la déclaration de substitution.  
  
## Voir aussi  
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)