---
title: "Erreur du compilateur CS0841 | Microsoft Docs"
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
  - "CS0841"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0841"
ms.assetid: eb67c244-a930-4291-ae2a-5832e8916ed7
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0841
Impossible d’utiliser la variable 'name' avant de la déclarer.  
  
 Pour pouvoir être utilisée, une variable doit être préalablement déclarée.  
  
### Pour corriger cette erreur  
  
1.  Déplacez la déclaration de variable avant la ligne où l’erreur se produit.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0841 :  
  
```  
// cs0841.cs using System; public class C { public static int Main() { j = 5; // CS0841 int j; // To fix, move this line up. return 1; } }  
```