---
title: "Les param&#232;tres &lt;type&gt; ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;Optional&#39; | Microsoft Docs"
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
  - "bc33010"
  - "vbc33010"
helpviewer_keywords: 
  - "BC33010"
ms.assetid: ec4023e7-9ba6-4532-a6b9-4ae6b4f9063a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les param&#232;tres &lt;type&gt; ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;Optional&#39;
Une définition d’un délégué, d’un événement ou d’un opérateur déclare un paramètre [Optional](/dotnet/visual-basic/language-reference/modifiers/optional).  
  
 Les paramètres `Optional` sont autorisés uniquement sur les paramètres `Declare`, `Function`, `Property` et `Sub`.  
  
 **ID d’erreur :** BC33010  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Optional` de la liste de paramètres.  
  
-   Si vous définissez un opérateur, vous pourrez peut\-être obtenir la fonctionnalité `Optional` avec une série de surcharges.  
  
-   Si vous définissez un délégué ou un événement, vous devez revoir toute la logique de cette partie de votre application. Vous ne pouvez pas utiliser les paramètres `Optional` ou [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray), ni les versions surchargées, sur des paramètres de délégué ou d’événement.  
  
## Voir aussi  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)