---
title: "Les d&#233;l&#233;gu&#233;s ne peuvent pas g&#233;rer les &#233;v&#233;nements | Microsoft Docs"
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
  - "bc30019"
  - "vbc30019"
helpviewer_keywords: 
  - "BC30019"
ms.assetid: 7f0c7bb9-8e81-44bf-acc5-80d9785708aa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les d&#233;l&#233;gu&#233;s ne peuvent pas g&#233;rer les &#233;v&#233;nements
Un délégué est un type référence qui pointe vers une procédure partagée ou une procédure d’instance sur un objet. Étant donné que la procédure vers laquelle elle pointe peut être modifiée par assignation, l’instruction `Delegate` ne peut pas prendre en charge les clauses `Handles` ou `Implements`.  
  
 **ID d'erreur :** BC30019  
  
### Pour corriger cette erreur  
  
-   Supprimez la clause `Handles` de l’instruction `Delegate`.  
  
## Voir aussi  
 [NOT IN BUILD : Délégués et opérateur AddressOf](http://msdn.microsoft.com/fr-fr/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)