---
title: "Les membres non partag&#233;s dans une Structure ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;New&#39; | Microsoft Docs"
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
  - "vbc30795"
  - "BC30795"
helpviewer_keywords: 
  - "BC30795"
ms.assetid: 8e4e1ad8-3bac-475f-82e8-e4f134692204
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les membres non partag&#233;s dans une Structure ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;New&#39;
Une variable non partagée dans une structure est déclarée avec une clause `New`.  
  
 Vous pouvez initialiser une variable de référence partagée dans une structure et vous pouvez avoir une variable de référence non partagée sans initialisation, comme l’illustrent les lignes de code suivantes.  
  
 `Shared structVar1 As New System.ApplicationException`  
  
 `Dim structVar2 As System.ApplicationException`  
  
 En revanche, vous ne pouvez pas initialiser une variable de référence non partagée dans une structure. La ligne de code suivante n’est pas valide.  
  
 `Dim structVar3 As New System.ApplicationException ' INVALID IN A STRUCTURE`  
  
 **ID d’erreur :** BC30795  
  
### Pour corriger cette erreur  
  
-   Supprimez le modificateur `Shared` ou le mot clé `New` de la déclaration de variable de référence.  
  
## Voir aussi  
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)