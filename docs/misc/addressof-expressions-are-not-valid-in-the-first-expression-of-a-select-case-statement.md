---
title: "Les expressions &#39;AddressOf&#39; ne sont pas valides dans la premi&#232;re expression d’une instruction &#39;Select Case&#39; | Microsoft Docs"
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
  - "bc36636"
  - "vbc36636"
helpviewer_keywords: 
  - "BC36636"
ms.assetid: 2ccc0ccc-d4d0-4910-8859-dedfa57c8126
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les expressions &#39;AddressOf&#39; ne sont pas valides dans la premi&#232;re expression d’une instruction &#39;Select Case&#39;
Vous ne pouvez pas utiliser d’expression `AddressOf` pour l’expression de test dans une instruction `Select Case`. Les expressions `AddressOf` retournent des délégués de fonction, et l’expression de test d’une instruction `Select Case` doit être un type de données élémentaire.  
  
 **ID d’erreur :** BC36636  
  
### Pour corriger cette erreur  
  
-   Examinez votre code pour déterminer si une construction conditionnelle différente, comme une instruction `If...Then...Else`, répond à vos besoins.  
  
## Voir aussi  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)