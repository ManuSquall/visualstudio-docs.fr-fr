---
title: "Les param&#232;tres &lt;type&gt; ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;ParamArray&#39; | Microsoft Docs"
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
  - "bc33009"
  - "vbc33009"
helpviewer_keywords: 
  - "BC33009"
ms.assetid: faba9aef-ca4e-4c4d-934c-a3e3d3fa3c3e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les param&#232;tres &lt;type&gt; ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;ParamArray&#39;
Une définition d’un délégué, événement ou opérateur déclare un paramètre [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray).  
  
 Les paramètres `ParamArray` sont uniquement autorisés sur les paramètres `Declare`, `Function`, `Property` et `Sub`.  
  
 **ID d’erreur :** BC33009  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `ParamArray` de la liste de paramètres.  
  
-   Si vous définissez un opérateur, vous pouvez peut\-être obtenir la fonctionnalité `ParamArray` avec une série de surcharges.  
  
-   Si vous définissez un délégué ou un événement, vous devez revoir toute la logique de cette partie de votre application. Vous ne pouvez pas utiliser les paramètres [Optional](/dotnet/visual-basic/language-reference/modifiers/optional) ou `ParamArray`, ni les versions surchargées, sur des paramètres de délégué ou d’événement.  
  
## Voir aussi  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)