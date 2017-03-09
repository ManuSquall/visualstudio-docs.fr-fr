---
title: "Erreur du compilateur CS0550 | Microsoft Docs"
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
  - "CS0550"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0550"
ms.assetid: 57278c17-443c-40f2-9ebd-853558743564
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0550
'accessor' ajoute un accesseur introuvable dans le membre d’interface 'property'  
  
 L’implémentation d’une propriété dans une classe dérivée contient un accesseur qui n’a pas été spécifié dans l’interface de base.  
  
 Pour plus d'informations, consultez [Utilisation de propriétés](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0550.  
  
```  
// CS0550.cs namespace x { interface ii { int i { get; // add the following accessor to resolve this CS0550 // set; } } public class a : ii { int ii.i { get { return 0; } set {}   // CS0550  no set in interface } public static void Main() {} } }  
```