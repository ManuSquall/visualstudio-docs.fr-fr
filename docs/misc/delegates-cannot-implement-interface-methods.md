---
title: "Les d&#233;l&#233;gu&#233;s ne peuvent pas impl&#233;menter des m&#233;thodes d’interface | Microsoft Docs"
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
  - "bc30018"
  - "vbc30018"
helpviewer_keywords: 
  - "BC30018"
ms.assetid: 71851072-c0c7-4131-aaf7-f3e9e6a2a448
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les d&#233;l&#233;gu&#233;s ne peuvent pas impl&#233;menter des m&#233;thodes d’interface
Un délégué est un type de référence qui pointe vers une procédure partagée ou une procédure d’instance sur un objet. Étant donné que la procédure vers laquelle elle pointe peut être modifiée par assignation, l’instruction `Delegate` ne peut pas prendre en charge les clauses `Handles` ou `Implements`.  
  
 **ID d’erreur :** BC30018  
  
### Pour corriger cette erreur  
  
-   Supprimez la clause `Implements` de l’instruction `Delegate`.  
  
## Voir aussi  
 [NOT IN BUILD : Délégués et opérateur AddressOf](http://msdn.microsoft.com/fr-fr/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)