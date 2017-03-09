---
title: "Impossible d’utiliser cet attribut, car il n’a pas de constructeur Public | Microsoft Docs"
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
  - "vbc30758"
  - "bc30758"
helpviewer_keywords: 
  - "BC30758"
ms.assetid: b72d1ff2-f6b2-4a89-9ac2-8765f77bcc97
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’utiliser cet attribut, car il n’a pas de constructeur Public
Le constructeur de l’attribut utilisé est `Private`, et ne peut pas être utilisé.  
  
 **ID d’erreur :** BC30758  
  
### Pour corriger cette erreur  
  
1.  Si vous recevez cette erreur avec un attribut personnalisé que vous avez développé, modifiez le modificateur d’accès de son constructeur `Sub``New`en `Public`.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)