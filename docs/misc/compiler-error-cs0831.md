---
title: "Erreur du compilateur CS0831 | Microsoft Docs"
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
  - "CS0831"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0831"
ms.assetid: f626a77d-3844-4438-954b-b8201e72b1b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0831
Une arborescence de l’expression ne peut pas contenir un accès de base.  
  
 L’accès de base signifie effectuer un appel de fonction qui serait normalement un appel de fonction virtuelle en tant qu’appel de fonction non virtuelle sur la méthode de classe de base. Cela n’est pas autorisé dans l’arborescence d’expression proprement dite, mais vous pouvez appeler une méthode d’assistance dans votre classe qui appelle la méthode de classe de base.  
  
### Pour corriger cette erreur  
  
1.  Si vous devez accéder à une méthode de classe de base de cette manière, créez une méthode d’assistance qui appelle la classe de base et faites en sorte que l’arborescence d’expression appelle la méthode d’assistance. Cette technique est illustrée dans le code suivant.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0831 :  
  
```  
// cs0831.cs using System; using System.Linq; using System.Linq.Expressions; public class A { public virtual int BaseMethod() { return 1; } } public class C : A { public override int BaseMethod() { return 2; } public int Test(C c) { Expression<Func<int>> e = () => base.BaseMethod(); // CS0831 // Try the following line instead, // along with the BaseAccessHelper method. // Expression<Func<int>> e2 = () => BaseAccessHelper(); return 1; } // Uncomment to call from e2 expression above. // int BaseAccessHelper() // { //     return base.BaseMethod(); // } }   
```