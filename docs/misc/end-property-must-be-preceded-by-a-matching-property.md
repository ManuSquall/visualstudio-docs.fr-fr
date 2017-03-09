---
title: "&#39;End Property&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Property&#39; correspondant | Microsoft Docs"
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
  - "vbc30431"
  - "bc30431"
helpviewer_keywords: 
  - "BC30431"
ms.assetid: b1e02d97-b38a-4acf-b351-1726f17a0051
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Property&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Property&#39; correspondant
Une instruction `End Property` n’est précédée d’aucune déclaration `Property` correspondante dans votre code.  
  
 **ID d’erreur :** BC30431  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction `End Property` si elle est redondante.  
  
-   Fournissez la procédure `Property` manquante, le cas échéant.  
  
-   Déplacez `End Property` vers l’emplacement de code approprié.  
  
## Voir aussi  
 [NOT IN BUILD : Propriétés et procédures de propriétés](http://msdn.microsoft.com/fr-fr/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)