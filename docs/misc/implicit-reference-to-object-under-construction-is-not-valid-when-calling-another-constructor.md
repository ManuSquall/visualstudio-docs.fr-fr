---
title: "Toute r&#233;f&#233;rence implicite &#224; un objet en construction n’est pas valide lors de l’appel d’un autre constructeur | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31096"
  - "bc31096"
helpviewer_keywords: 
  - "BC31096"
ms.assetid: 558a2beb-aa5d-41a8-8655-ad3d16ac8acd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Toute r&#233;f&#233;rence implicite &#224; un objet en construction n’est pas valide lors de l’appel d’un autre constructeur
Une référence à un membre d’objet a été effectuée avant que le constructeur de l’objet ne termine la construction de l’objet.  
  
 **ID d’erreur :** BC31096  
  
### Pour corriger cette erreur  
  
-   N’utilisez pas `MyBase`, `MyClass` ni `Me` lors de l’appel d’un constructeur à partir d’un autre constructeur.  
  
## Voir aussi  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/fr-fr/548eebe1-86c4-4377-b2f5-447cb8be3d90)