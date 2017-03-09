---
title: "Les m&#233;thodes g&#233;n&#233;riques ne peuvent pas utiliser une clause &#39;Handles&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32080"
  - "BC32080"
helpviewer_keywords: 
  - "BC32080"
ms.assetid: 88c62a1c-aee3-46b2-ad78-76790022c04c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les m&#233;thodes g&#233;n&#233;riques ne peuvent pas utiliser une clause &#39;Handles&#39;
Une procédure `Sub` générique comprend une clause [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause) dans sa déclaration.  
  
 Une clause `Handles` spécifie une liste d’événements gérés par la procédure `Sub`. Pour être un gestionnaire d’événements, la procédure `Sub` doit avoir la même signature que chaque événement qu’elle doit gérer. Une procédure générique peut être créée plusieurs fois, avec des signatures que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas prévoir au moment de la compilation. Ainsi, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas garantir une signature qui correspond à celles des événements dans la clause `Handles`.  
  
 **ID d’erreur :** BC32080  
  
### Pour corriger cette erreur  
  
-   Si la procédure `Sub` doit être générique, supprimez la clause `Handles` de sa déclaration. Utilisez [AddHandler Statement](/dotnet/visual-basic/language-reference/statements/addhandler-statement) pour associer ce gestionnaire d’événements à un événement.  
  
-   Si la procédure `Sub` doit utiliser la clause `Handles` pour associer des événements, supprimez la clause [Of](/dotnet/visual-basic/language-reference/statements/of-clause) de sa déclaration. Vous devez utiliser une procédure non générique avec `Handles`.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NOT IN BUILD : Événements et gestionnaires d’événements](http://msdn.microsoft.com/fr-fr/95074a0d-1cbc-4221-a95a-964185c7f962)