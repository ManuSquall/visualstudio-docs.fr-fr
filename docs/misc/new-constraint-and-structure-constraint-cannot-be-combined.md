---
title: "La contrainte &#39;New&#39; et la contrainte &#39;Structure&#39; ne peuvent pas &#234;tre combin&#233;es | Microsoft Docs"
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
  - "bc32103"
  - "vbc32103"
helpviewer_keywords: 
  - "BC32103"
ms.assetid: 5418b420-a014-4006-84aa-20ddac6739e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La contrainte &#39;New&#39; et la contrainte &#39;Structure&#39; ne peuvent pas &#234;tre combin&#233;es
Une liste de contraintes comprend à la fois la contrainte [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator) et la contrainte [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0).  
  
 Une liste de contraintes sur un paramètre de type peut spécifier que l’argument de type passé à ce paramètre de type doit être un type valeur \(avec la contrainte `Structure`\) ou un type référence \(avec la contrainte [Classe \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)\). Vous ne pouvez pas spécifier les deux contraintes sur le même paramètre de type et vous ne pouvez pas spécifier l’une des deux plusieurs fois.  
  
 La contrainte `New` spécifie que l’argument de type doit exposer un constructeur sans paramètre et auquel le code de création peut accéder. Cependant, une structure ne peut pas avoir un constructeur sans paramètre non partagé. Par conséquent, les contraintes `New` et `Structure` sont en conflit.  
  
 **ID d’erreur :** BC32103  
  
### Pour corriger cette erreur  
  
1.  Décidez si vous souhaitez exiger un type valeur ou un type référence pour l’argument de type.  
  
2.  Si vous voulez que l’argument de type soit un type valeur, supprimez le mot clé `New` de la liste des contraintes.  
  
3.  Si vous voulez que l’argument de type soit un type référence, supprimez le mot clé `Structure` de la liste des contraintes.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)