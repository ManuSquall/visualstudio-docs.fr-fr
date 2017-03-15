---
title: "L’argument de type &#39;&lt;nom_argument_type&gt;&#39; ne satisfait pas la contrainte &#39;Class&#39; du param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32106"
  - "bc32106"
helpviewer_keywords: 
  - "BC32106"
ms.assetid: 1bac1dd6-f86b-4e98-ba2d-57d1936e3658
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’argument de type &#39;&lt;nom_argument_type&gt;&#39; ne satisfait pas la contrainte &#39;Class&#39; du param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39;
Un argument de type fourni à un type générique ne satisfait pas la contrainte de type référence sur son paramètre de type correspondant.  
  
 Une liste de contraintes impose des exigences sur l’argument de type passé au paramètre de type. Si vous n’incluez pas de classe ou d’interface spécifique dans la liste de contraintes, vous pouvez imposer une condition générale en spécifiant l’une des obligations suivantes :  
  
-   L’argument de type doit être un type valeur \(inclure la contrainte [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)\).  
  
-   L’argument de type doit être un type référence \(inclure la contrainte [Class \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)\).  
  
 Vous ne pouvez pas spécifier à la fois `Structure` et `Class` pour le même paramètre de type et vous ne pouvez pas spécifier l’une des deux plusieurs fois.  
  
 **ID d’erreur :** BC32106  
  
### Pour corriger cette erreur  
  
-   Sélectionnez un argument de type de n’importe quel type référence.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Comment : utiliser une classe générique](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)