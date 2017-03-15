---
title: "&#39;&lt;nom_membre&gt;&#39; n’est pas membre de &#39;&lt;nom_contexte&gt;&#39;&#160;; il n’existe pas dans le contexte actuel | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36557"
  - "bc36557"
helpviewer_keywords: 
  - "BC36557"
ms.assetid: d8671f1c-d545-44da-89b3-7d892e01e8be
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_membre&gt;&#39; n’est pas membre de &#39;&lt;nom_contexte&gt;&#39;&#160;; il n’existe pas dans le contexte actuel
Un nom de membre inexistant a été affecté à une propriété dans une déclaration de type anonyme. Dans l’exemple suivant, `.Prop1` et `.Prop2` sont les propriétés du type anonyme. La tentative d’affectation de `.Prop3` à `.Prop2` provoque l’erreur.  
  
```vb#  
' Not valid.  
Dim anon1 = New With {.Prop1 = 27, .Prop2 = .Prop3}  
  
' The assignment is valid if the assigned property has been declared   
' and initialized.  
Dim anon2 = New With {.Prop1 = 27, .Prop2 = .Prop1}  
```  
  
 **ID d’erreur :** BC36657  
  
### Pour corriger cette erreur  
  
-   Examinez votre code pour déterminer ce que vous souhaitez affecter. Le nom de la variable est peut\-être mal orthographié, ou une qualification est peut\-être nécessaire s’il s’agit d’une propriété d’un autre objet.  
  
## Voir aussi  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)