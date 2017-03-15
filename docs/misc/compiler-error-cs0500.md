---
title: "Erreur du compilateur CS0500 | Microsoft Docs"
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
  - "CS0500"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0500"
ms.assetid: b1a45708-702b-482c-bd71-c0c2531e29f3
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0500
'membre\_classe' ne peut pas déclarer un corps, car il est marqué comme abstract  
  
 Une méthode [abstract](/dotnet/csharp/language-reference/keywords/abstract) ne peut pas contenir son implémentation.  
  
 L’exemple suivant génère l’erreur CS0500 :  
  
```  
// CS0500.cs namespace x { abstract public class clx { abstract public void f(){}   // CS0500 // try the following line instead // abstract public void f(); } public class cly { public static int Main() { return 0; } } }  
```