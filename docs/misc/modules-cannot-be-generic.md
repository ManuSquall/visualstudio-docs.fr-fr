---
title: "Les modules ne peuvent pas &#234;tre g&#233;n&#233;riques | Microsoft Docs"
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
  - "BC32073"
  - "vbc32073"
helpviewer_keywords: 
  - "BC32073"
ms.assetid: 47246e2b-51d4-4a10-a3ac-bc77b44fa2ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les modules ne peuvent pas &#234;tre g&#233;n&#233;riques
Une instruction `Module` utilise le mot clé `Of` pour introduire des paramètres de type générique.  
  
 Vous pouvez définir et utiliser des délégués, structures, interfaces, procédures et classes génériques. Vous ne pouvez pas définir de modules génériques.  
  
 **ID d’erreur :** BC32073  
  
### Pour corriger cette erreur  
  
1.  Supprimez le mot clé `Of` de l’instruction `Module`.  
  
2.  Si vous souhaitez bénéficier de la fonctionnalité d’un module générique, l’approximation la plus proche est une classe générique. Utilisez une [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement) au lieu d’une instruction `Module`.  
  
## Voir aussi  
 [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement)   
 [Of](/dotnet/visual-basic/language-reference/statements/of-clause)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Comment : définir une classe qui fournisse des fonctionnalités identiques pour différents types de données](../Topic/How%20to:%20Define%20a%20Class%20That%20Can%20Provide%20Identical%20Functionality%20on%20Different%20Data%20Types%20\(Visual%20Basic\).md)