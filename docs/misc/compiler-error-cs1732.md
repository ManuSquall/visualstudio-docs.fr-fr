---
title: "Erreur du compilateur CS1732 | Microsoft Docs"
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
  - "CS1732"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1732"
ms.assetid: 72c7f7fc-d5f2-4538-9b02-50dda54d3b1e
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1732
Paramètre attendu  
  
 Cette erreur se produit quand une expression lambda contient une virgule à la suite d’un paramètre d’entrée, mais ne spécifie pas le paramètre suivant.  
  
### Pour corriger cette erreur  
  
1.  Supprimez la virgule ou ajoutez le paramètre d’entrée que le compilateur s’attend à trouver après la virgule.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1732 :  
  
```  
// cs1732.cs // compile with: /target:library class Test { delegate void D(int x, int y); static void Main() { D d = (x,) => { }; // CS1732 } }  
```