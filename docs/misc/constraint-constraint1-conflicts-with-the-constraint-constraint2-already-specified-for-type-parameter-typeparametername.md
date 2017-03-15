---
title: "La contrainte &#39;&lt;contrainte1&gt;&#39; est en conflit avec la contrainte &#39;&lt;contrainte2&gt;&#39; d&#233;j&#224; sp&#233;cifi&#233;e pour le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; | Microsoft Docs"
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
  - "vbc32119"
  - "bc32119"
helpviewer_keywords: 
  - "BC32119"
ms.assetid: 30e6778d-5c2b-4f2d-a136-4e66fa9fbe4d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La contrainte &#39;&lt;contrainte1&gt;&#39; est en conflit avec la contrainte &#39;&lt;contrainte2&gt;&#39; d&#233;j&#224; sp&#233;cifi&#233;e pour le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39;
Un type générique est déclaré avec des contraintes incompatibles sur un paramètre de type.  
  
 L’instruction suivante peut générer cette erreur.  
  
 `Public Class testClass(Of t As {Structure, Class })`  
  
 Les contraintes `Structure` et `Class` entraînent un conflit pour le paramètre de type `t`, car la contrainte `Structure` exige que l’argument de type correspondant soit un type valeur, alors que `Class` exige qu’il soit un type référence.  
  
 **ID d’erreur :** BC32119  
  
### Pour corriger cette erreur  
  
-   Modifiez les contraintes de paramètre de type pour éviter les conflits.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Class \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)