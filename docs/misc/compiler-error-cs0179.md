---
title: "Erreur du compilateur CS0179 | Microsoft Docs"
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
  - "CS0179"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0179"
ms.assetid: bef000ca-64d7-4809-b2a0-de6927b04b0d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0179
'member' ne peut pas être extern et être déclaré  
  
 Quand un membre de classe est marqué [extern](/dotnet/csharp/language-reference/keywords/extern), cela signifie que la définition du membre se trouve dans un autre fichier. Un membre de classe marqué comme **extern** ne peut donc pas être défini dans la classe. Supprimez le mot clé `extern` ou la définition. Pour plus d'informations, consultez [Méthodes](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 L’exemple suivant génère l’erreur CS0179 :  
  
```  
// CS0179.cs public class MyClass { public extern int ExternMethod(int aa)   // CS0179 { return 0; } // try the following line instead // public extern int ExternMethod(int aa); public static void Main() { } }  
```