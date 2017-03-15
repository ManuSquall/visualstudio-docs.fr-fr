---
title: "Les arguments de type pour la m&#233;thode &#39;&lt;nom_proc&#233;dure&gt;&#39; n’ont pas pu &#234;tre inf&#233;r&#233;s &#224; partir du d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39; | Microsoft Docs"
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
  - "vbc30952"
  - "bc30952"
helpviewer_keywords: 
  - "BC30952"
ms.assetid: 5eb804ce-2e93-4668-b655-7fe00815e552
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les arguments de type pour la m&#233;thode &#39;&lt;nom_proc&#233;dure&gt;&#39; n’ont pas pu &#234;tre inf&#233;r&#233;s &#224; partir du d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39;
Une instruction d’assignation utilise `AddressOf` pour assigner l’adresse d’une procédure générique à un délégué, mais elle ne fournit aucun argument de type à la procédure générique.  
  
 En général, lorsque vous appelez un type générique, vous fournissez un argument de type pour chaque paramètre de type défini par le type générique. Si vous ne fournissez pas d’arguments de type, le compilateur tente de déduire les types à passer aux paramètres de type. Si le contexte ne fournit pas au compilateur suffisamment d’informations pour déduire les types, celui\-ci génère une erreur.  
  
 **ID d’erreur :** BC30952  
  
### Pour corriger cette erreur  
  
-   Spécifiez les arguments de type pour la procédure générique dans l’expression `AddressOf`.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)