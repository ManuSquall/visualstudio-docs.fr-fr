---
title: "Erreur du compilateur CS0312 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0312"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0312"
ms.assetid: 552db0ae-2ecf-4beb-9606-bbe58e5708f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0312
Impossible d’utiliser le type 'type1' comme paramètre de type 'nom' dans le type ou la méthode générique 'nom'. Le type Nullable 'type1' ne satisfait pas la contrainte de 'type2'.  
  
 Un type Nullable est distinct de son équivalent non nullable ; il n’existe pas de conversion de référence implicite ou de conversion d’identification entre eux. Une conversion boxing nullable ne satisfait pas la contrainte de type générique. Dans l’exemple qui suit, le premier paramètre de type est un `Nullable<int>` et le deuxième est un `System.Int32`.  
  
### Pour corriger cette erreur  
  
1.  Supprimez la contrainte.  
  
2.  Dans l’exemple suivant, changez le deuxième argument de type en `int?` ou `object`.  
  
## Exemple  
 Le code suivant génère l’erreur CS0312 :  
  
```  
// cs0312.cs class Program { static void MTyVar<T, U>() where T : U { } static int Main() { MTyVar<int?, int>(); // CS0312 return 1; } }  
```  
  
 Bien qu’un type Nullable soit distinct d’un type non nullable, différents types de conversions sont autorisés entre les valeurs nullables et non nullables.  
  
## Voir aussi  
 [Types Nullable](/dotnet/csharp/programming-guide/nullable-types/index)