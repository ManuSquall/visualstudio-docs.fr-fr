---
title: "Erreur du compilateur CS1662 | Microsoft Docs"
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
  - "CS1662"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1662"
ms.assetid: e61a4fc8-0ef1-4a4a-a27b-3a015c3ba38a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1662
Impossible de convertir le bloc de méthode anonyme en type délégué 'type délégué', car certains types de retour ne sont pas implicitement convertibles en type de retour délégué  
  
 Cette erreur se produit si l’instruction return du bloc de méthode anonyme avait un type qui n’était pas implicitement convertible en type de retour du délégué.  
  
 L’exemple suivant génère l’erreur CS1662 :  
  
```  
// CS1662.cs delegate int MyDelegate(int i); class C { public static void Main() { MyDelegate d = delegate(int i) { return 1.0; };  // CS1662 // Try this instead: // MyDelegate d = dekegate(int i) { return (int)1.0; }; } }  
```