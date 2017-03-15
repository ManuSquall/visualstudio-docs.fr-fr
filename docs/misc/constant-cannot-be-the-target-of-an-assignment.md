---
title: "Une constante ne peut pas &#234;tre la cible d’une assignation | Microsoft Docs"
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
  - "bc30074"
  - "vbc30074"
helpviewer_keywords: 
  - "BC30074"
ms.assetid: e805a517-228a-4147-a2c0-9dba93d3ba42
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une constante ne peut pas &#234;tre la cible d’une assignation
Une constante apparaît dans un contexte qui lui assigne une valeur. Seuls les variables, les propriétés et les éléments de tableau accessibles en écriture peuvent recevoir des valeurs durant l’exécution.  
  
 **ID d’erreur :** BC30074  
  
### Pour corriger cette erreur  
  
-   Remplacez la constante par une variable, une propriété ou un élément de tableau unique accessible en écriture.  
  
## Voir aussi  
 [Constants and Enumerations](/dotnet/visual-basic/programming-guide/language-features/constants-enums/index)   
 [NotInBuild : Instructions d’affectation](http://msdn.microsoft.com/fr-fr/eb4f91e9-fbbf-45ca-b21d-e8ae069de4f9)