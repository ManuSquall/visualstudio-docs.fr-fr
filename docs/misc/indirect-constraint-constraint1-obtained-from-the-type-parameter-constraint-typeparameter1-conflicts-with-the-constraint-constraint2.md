---
title: "La contrainte indirecte &#39;&lt;contrainte1&gt;&#39; obtenue &#224; partir de la contrainte de param&#232;tre de type &#39;&lt;param&#232;tre_type1&gt;&#39; est en conflit avec la contrainte &#39;&lt;contrainte2&gt;&#39;. | Microsoft Docs"
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
  - "bc32111"
  - "vbc32111"
helpviewer_keywords: 
  - "BC32111"
ms.assetid: b03b5840-5318-4844-b2da-1bca4c28d097
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La contrainte indirecte &#39;&lt;contrainte1&gt;&#39; obtenue &#224; partir de la contrainte de param&#232;tre de type &#39;&lt;param&#232;tre_type1&gt;&#39; est en conflit avec la contrainte &#39;&lt;contrainte2&gt;&#39;.
Un type générique est déclaré avec des contraintes en conflit en raison d’une combinaison de contraintes directes et indirectes.  
  
 L’instruction suivante peut générer cette erreur.  
  
 `Public Class testClass(Of t1 As {t2, Class}, t2 As Structure)`  
  
 La contrainte indirecte `Structure` et la contrainte directe `Class` provoquent un conflit pour le paramètre de type `t1`, car la contrainte `Structure` exige que l’argument de type correspondant soit un type valeur, alors que `Class` exige qu’il soit un type référence.  
  
 **ID d’erreur :** BC32111  
  
### Pour corriger cette erreur  
  
-   Modifiez les contraintes de paramètre de type pour éviter les conflits entre contraintes.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Class \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)