---
title: "Erreur du compilateur CS0454 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0454"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0454"
ms.assetid: 2c83bc5e-53bb-473e-92aa-5122dadd79d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0454
Dépendance de contrainte circulaire utilisant 'Type Parameter 1' et 'Type Parameter 2'  
  
 Cette erreur se produit parce qu’un paramètre de type fait référence à un autre paramètre de type et que ce dernier fait référence au premier. Pour corriger cette erreur, arrêtez la dépendance circulaire en supprimant l’une des contraintes. Notez que la dépendance de contrainte circulaire peut être indirecte.  
  
## Exemple  
 Le code suivant génère l’erreur CS0454.  
  
```  
// CS0554 using System; public class GenericsErrors { public class G4<T> where T : T { } // CS0454 }  
```  
  
## Exemple  
 L’exemple suivant illustre une dépendance circulaire entre deux contraintes de type.  
  
```  
public class Gen<T,U> where T : U where U : T  // CS0454 { }  
```