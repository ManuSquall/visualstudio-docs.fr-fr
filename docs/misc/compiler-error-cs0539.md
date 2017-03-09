---
title: "Erreur du compilateur CS0539 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0539"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0539"
ms.assetid: 41b8975c-abd1-4a36-98a4-8efa5fb0502a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0539
'membre' dans une déclaration d’interface explicite n’est pas un membre d’interface  
  
 Une tentative a été effectuée pour déclarer explicitement un membre d’[interface](/dotnet/csharp/language-reference/keywords/interface) qui n’existe pas. Vous devez supprimer la déclaration ou la modifier pour qu’elle fasse référence à un membre d’interface valide.  
  
 L’exemple suivant génère l’avertissement CS0539 :  
  
```  
// CS0539.cs namespace x { interface I { void m(); } public class clx : I { void I.x()   // CS0539 { } public static int Main() { return 0; } } }  
```