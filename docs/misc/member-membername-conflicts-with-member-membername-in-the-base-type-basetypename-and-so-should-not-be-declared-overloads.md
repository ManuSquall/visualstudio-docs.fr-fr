---
title: "Le membre &#39;&lt;nom_membre&gt;&#39; est en conflit avec le membre &#39;&lt;nom_membre&gt;&#39; dans le type de base &#39;&lt;nom_type_base&gt;&#39; et ne doit donc pas &#234;tre d&#233;clar&#233; comme &#39;Overloads&#39; | Microsoft Docs"
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
  - "bc40021"
  - "vbc40021"
helpviewer_keywords: 
  - "BC40021"
ms.assetid: 2ec72726-ab0e-4545-9c1e-2409eb54482e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le membre &#39;&lt;nom_membre&gt;&#39; est en conflit avec le membre &#39;&lt;nom_membre&gt;&#39; dans le type de base &#39;&lt;nom_type_base&gt;&#39; et ne doit donc pas &#234;tre d&#233;clar&#233; comme &#39;Overloads&#39;
Une propriété ou une procédure utilise le mot clé [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) pour redéclarer une procédure ou une propriété existante portant le même nom, mais la procédure ou la propriété existante se trouve dans la classe de base.  
  
 La surcharge permet de définir plusieurs versions d’une propriété ou d’une procédure dans la même classe. Vous ne pouvez pas définir une version supplémentaire d’un membre de classe de base tant que ce membre ne spécifie pas [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads).  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40021  
  
### Pour corriger cette erreur  
  
-   Si vous souhaitez définir une version supplémentaire du membre de classe de base et avoir accès au code source de la classe de base, ajoutez le mot clé [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) à la définition de la classe de base.  
  
-   Si vous n’avez pas accès au code source de la classe de base, vous ne pouvez pas surcharger le membre dans une classe dérivée. Supprimez le mot clé `Overloads`.  
  
-   Si vous souhaitez remplacer le membre de classe de base au lieu de définir une version supplémentaire de celui\-ci, utilisez le mot clé [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides) à la place de `Overloads`.  
  
-   Si vous souhaitez masquer le membre de classe de base avec un nouveau membre dans la classe dérivée, utilisez le mot clé [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) à la place de `Overloads`.  
  
## Voir aussi  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)