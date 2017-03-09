---
title: "&#39;&lt;nom&gt;&#39; ne peut pas &#234;tre nomm&#233; en tant que param&#232;tre dans un sp&#233;cificateur d’attribut, car ce n’est ni un champ ni une propri&#233;t&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "10/25/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32010"
  - "bc32010"
helpviewer_keywords: 
  - "BC32010"
ms.assetid: bfa68729-71ea-410e-bef1-83a7dab44d2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom&gt;&#39; ne peut pas &#234;tre nomm&#233; en tant que param&#232;tre dans un sp&#233;cificateur d’attribut, car ce n’est ni un champ ni une propri&#233;t&#233;
Un bloc d’attributs définit une valeur pour un membre de l’attribut qui n’est pas une variable. Vous pouvez uniquement assigner des valeurs à des membres variables tels que des champs ou des propriétés.  
  
 **ID d’erreur :** BC32010  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que les noms des attributs et des membres sont correctement orthographiés.  
  
2.  Supprimez l’argument du bloc d’attributs si le membre n’est pas une variable.  
  
## Voir aussi  
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)