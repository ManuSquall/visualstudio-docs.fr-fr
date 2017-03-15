---
title: "La propri&#233;t&#233; ne peut pas &#234;tre d&#233;clar&#233;e &#39;&lt;modificateur_propri&#233;t&#233;&gt;&#39;, car elle contient un accesseur &#39;Private&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31108"
  - "bc31108"
helpviewer_keywords: 
  - "BC31108"
ms.assetid: 74fb36f4-54cd-4fda-bcc6-e965b5c7c37b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propri&#233;t&#233; ne peut pas &#234;tre d&#233;clar&#233;e &#39;&lt;modificateur_propri&#233;t&#233;&gt;&#39;, car elle contient un accesseur &#39;Private&#39;
Une propriété avec une procédure de propriété `Private` \(`Get` ou `Set`\) est marquée [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable).  
  
 Si une propriété de classe de base ou une procédure est déclarée [Private](/dotnet/visual-basic/language-reference/modifiers/private), une classe dérivée ne peut pas substituer cette propriété ou procédure car elle ne peut pas y accéder. Pour cette raison, vous ne pouvez pas utiliser `Private` associé avec `Overridable`. Cela s’applique non seulement à la propriété proprement dite, mais aussi aux procédures de propriété.  
  
 **ID d’erreur :** BC31108  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Overridable` à partir de l’[Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement), ou supprimez le mot clé `Private` de l’[Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) ou de l’[Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
## Voir aussi  
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)