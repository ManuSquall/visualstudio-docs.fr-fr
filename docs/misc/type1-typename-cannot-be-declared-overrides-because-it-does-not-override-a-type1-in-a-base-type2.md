---
title: "&lt;type1&gt; &#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre d&#233;clar&#233; &#39;Overrides&#39;, car il ne se substitue pas &#224; un &lt;type1&gt; dans une classe de base &lt;type2&gt; | Microsoft Docs"
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
  - "vbc30284"
  - "bc30284"
helpviewer_keywords: 
  - "BC30284"
ms.assetid: 8166bd09-dad3-495d-8cf7-66f90824a288
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt; &#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre d&#233;clar&#233; &#39;Overrides&#39;, car il ne se substitue pas &#224; un &lt;type1&gt; dans une classe de base &lt;type2&gt;
Une instruction `Sub`, `Function` ou `Property` spécifie `Overrides` quand une classe de base ne comprend pas plusieurs types de même nom.  
  
 **ID d’erreur :** BC30284  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que le nom du type est correctement orthographié.  
  
2.  Supprimez le mot clé `Overrides` redondant.  
  
## Voir aussi  
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)