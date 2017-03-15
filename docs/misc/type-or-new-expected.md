---
title: "Type ou &#39;New&#39; attendu. | Microsoft Docs"
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
  - "vbc32092"
  - "bc32092"
helpviewer_keywords: 
  - "BC32092"
ms.assetid: b3041c1d-837c-4d58-bbb4-5c46f227b66d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Type ou &#39;New&#39; attendu.
Un paramètre de type dans la déclaration d’un type générique introduit une liste de contraintes avec le mot clé `As` mais ne spécifie pas de contrainte valide.  
  
 Une contrainte sur un paramètre de type doit être une classe ou une interface valide, ou l’un des mots clés `Class`, `Structure` ou `New`. Si vous spécifiez une contrainte non valide ou si vous n’en spécifiez aucune, le compilateur génère cette erreur.  
  
 **ID d’erreur :** BC32092  
  
### Pour corriger cette erreur  
  
1.  Déterminez comment le paramètre de type doit être contraint et spécifiez la contrainte appropriée dans la liste des contraintes.  
  
2.  Si vous souhaitez contraindre le paramètre de type par une classe ou une interface, vérifiez que la contrainte l’orthographie correctement.  
  
3.  N’oubliez pas de séparer les contraintes sur un paramètre de type par des virgules et de placer la liste des contraintes entre accolades \(`{ }`\).  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Classe \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)