---
title: "Erreur du compilateur CS0200 | Microsoft Docs"
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
  - "CS0200"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0200"
ms.assetid: 1990704a-edfa-4dbd-8477-d9c7aae58c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0200
La propriété ou l’indexeur 'propriété' ne peut pas être assigné — il est en lecture seule  
  
 L’utilisateur a tenté d’affecter une valeur à une [propriété](/dotnet/csharp/programming-guide/classes-and-structs/using-properties), mais celle\-ci n’a pas d’accesseur set. Pour résoudre l’erreur, ajoutez un accesseur set. Pour plus d'informations, consultez [Comment : déclarer et utiliser des propriétés en lecture\-écriture](../Topic/How%20to:%20Declare%20and%20Use%20Read%20Write%20Properties%20\(C%23%20Programming%20Guide\).md).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0200 :  
  
```  
// CS0200.cs public class MainClass { // private int _mi; int I { get { return 1; } // uncomment the set accessor and declaration for _mi /* set { _mi = value; } */ } public static void Main () { MainClass II = new MainClass(); II.I = 9;   // CS0200 } }  
```