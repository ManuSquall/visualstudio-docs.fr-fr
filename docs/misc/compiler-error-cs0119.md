---
title: "Erreur du compilateur CS0119 | Microsoft Docs"
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
  - "CS0119"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0119"
ms.assetid: 048924f1-378f-4021-bd20-299d3218f810
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0119
'construct1\_name' est un 'construct1', ce qui n’est pas valide dans le contexte donné.  
  
 Le compilateur a détecté une construction inattendue telle que la suivante :  
  
-   Un constructeur de classe n’est pas une expression de test valide dans une instruction conditionnelle.  
  
-   Un nom de classe a été utilisé à la place d’un nom d’instance pour référencer un élément de tableau.  
  
-   Un identificateur de méthode est utilisé comme s’il s’agissait d’un struct ou d’une classe  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0119.  
  
```  
// CS0119.cs using System; public class MyClass { public static void Test() {} public static void Main() { Console.WriteLine(Test.x);   // CS0119 } }  
```