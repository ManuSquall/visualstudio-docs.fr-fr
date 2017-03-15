---
title: "Une contrainte &#39;Structure&#39; et une contrainte de type classe sp&#233;cifique ne peuvent pas &#234;tre combin&#233;es | Microsoft Docs"
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
  - "vbc32108"
  - "bc32108"
helpviewer_keywords: 
  - "BC32108"
ms.assetid: de461824-5aec-48d1-967d-b0e0609a8ba6
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une contrainte &#39;Structure&#39; et une contrainte de type classe sp&#233;cifique ne peuvent pas &#234;tre combin&#233;es
Une liste de contraintes comprend à la fois la contrainte [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) et le nom d’une classe définie.  
  
 Une liste de contraintes impose des exigences sur l’argument de type passé au paramètre de type. Vous pouvez spécifier les exigences suivantes dans toute combinaison :  
  
-   L’argument de type doit implémenter une ou plusieurs interfaces.  
  
-   L’argument de type doit hériter d’une classe au plus.  
  
-   L’argument de type doit exposer un constructeur sans paramètre accessible par le code de création \(ajoutez la contrainte `New`\).  
  
 Si vous n’incluez pas de classe ou d’interface spécifique dans la liste de contraintes, vous pouvez imposer une condition plus générale en spécifiant l’une des obligations suivantes :  
  
-   L’argument de type doit être un type valeur \(ajoutez la contrainte `Structure`\)  
  
-   L’argument de type doit être un type référence \(ajoutez la contrainte `Class`\)  
  
 Vous ne pouvez pas spécifier à la fois `Structure` et `Class` pour le même paramètre de type et vous ne pouvez pas spécifier l’une des deux plusieurs fois.  
  
 **ID d’erreur :** BC32108  
  
### Pour corriger cette erreur  
  
-   Si vous voulez que l’argument de type soit un type valeur, supprimez le nom de classe de la liste des contraintes.  
  
-   Si vous voulez que l’argument de type hérite du nom de classe spécifié, supprimez le mot clé `Structure` de la liste des contraintes.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)