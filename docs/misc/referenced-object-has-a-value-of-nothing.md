---
title: "L’objet r&#233;f&#233;renc&#233; a la valeur &#39;Nothing&#39; | Microsoft Docs"
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
  - "bc30760"
  - "vbc30760"
helpviewer_keywords: 
  - "BC30760"
ms.assetid: 7e792fd8-2880-402b-a908-c89e5b028300
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’objet r&#233;f&#233;renc&#233; a la valeur &#39;Nothing&#39;
L’objet utilisé a la valeur `Nothing`, alors qu’une valeur utilisable est attendue.`Nothing` est une valeur qui indique qu’un objet n’a pas de valeur, soit parce qu’aucune valeur ne lui a été attribuée, soit parce que la valeur `Nothing` lui a été attribuée.  
  
 **ID d’erreur :** BC30760  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l’objet pour vous assurer qu’il a été déclaré dans la portée de la procédure où s’est produite l’erreur.  
  
2.  Vérifiez que la valeur de l’objet est définie.  
  
    > [!NOTE]
    >  La valeur `Nothing` n’est pas égale à zéro et ne correspond pas non plus à une chaîne vide. Vous pouvez utiliser `IsNothing` pour vérifier si un objet contient la valeur `Nothing`.  
  
## Voir aussi  
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [NOT IN BUILD : IsNothing, fonction](http://msdn.microsoft.com/fr-fr/5b2a4626-e6a9-49d1-b9b1-fcc6a1302319)