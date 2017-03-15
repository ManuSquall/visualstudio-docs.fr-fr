---
title: "Les instructions d’attribut Assembly ou Module doivent pr&#233;c&#233;der toutes les d&#233;clarations dans un fichier | Microsoft Docs"
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
  - "vbc30637"
  - "bc30637"
helpviewer_keywords: 
  - "BC30637"
ms.assetid: 80242581-fa8a-4903-9395-6f7ad1610231
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions d’attribut Assembly ou Module doivent pr&#233;c&#233;der toutes les d&#233;clarations dans un fichier
Les attributs globaux doivent être déclarés au début d’un fichier source, après les instructions `Option` et `Imports`, mais avant toute autre instruction.  
  
 **ID d’erreur :** BC30637  
  
### Pour corriger cette erreur  
  
1.  Placez les attributs globaux, tels que `<Module:>` et `<Assembly:>`, au début de votre fichier source.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [NOT IN BUILD : Attributs globaux en Visual Basic](http://msdn.microsoft.com/fr-fr/253a32d8-1531-4504-b687-088554ab71d2)