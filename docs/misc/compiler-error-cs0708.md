---
title: "Erreur du compilateur CS0708 | Microsoft Docs"
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
  - "CS0708"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0708"
ms.assetid: 19e1907f-b78c-4c8b-b78c-eedfd57115f2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0708
'champ' : impossible de déclarer des membres d’instance dans une classe static  
  
 Cette erreur se produit si vous déclarez un membre non static dans une classe qui est déclarée static. La création d’instances de classes static étant impossible, les variables d’instance ne seraient pas significatives. Le mot clé **static** doit être appliqué à tous les membres de classes static.  
  
 L’exemple suivant génère l’erreur CS0708 :  
  
```  
// CS0708.cs // compile with: /target:library public static class C { int i;  // CS0708 static int j;  // OK }  
```