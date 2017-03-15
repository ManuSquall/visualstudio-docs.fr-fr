---
title: "Le mot cl&#233; &#39;&lt;mot_cl&#233;&gt;&#39; est utilis&#233; pour surcharger les membres h&#233;rit&#233;s&#160;; n’utilisez pas le mot cl&#233; &#39;&lt;mot_cl&#233;&gt;&#39; lors de la surcharge de &#39;Sub New&#39; | Microsoft Docs"
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
  - "vbc32040"
  - "bc32040"
helpviewer_keywords: 
  - "BC32040"
ms.assetid: 39e6ee0d-b8a0-498e-bdaf-a4ceb13892fe
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le mot cl&#233; &#39;&lt;mot_cl&#233;&gt;&#39; est utilis&#233; pour surcharger les membres h&#233;rit&#233;s&#160;; n’utilisez pas le mot cl&#233; &#39;&lt;mot_cl&#233;&gt;&#39; lors de la surcharge de &#39;Sub New&#39;
Un constructeur est déclaré avec le mot clé `Overloads`.  
  
 Visual Basic ne prend pas en charge l’héritage ni la surcharge des constructeurs.  
  
 **ID d’erreur :** BC32040  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Overloads` de toutes les déclarations de constructeur.  
  
## Voir aussi  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [NOT IN BUILD : Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/fr-fr/548eebe1-86c4-4377-b2f5-447cb8be3d90)