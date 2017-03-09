---
title: "Erreur du compilateur CS0277 | Microsoft Docs"
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
  - "CS0277"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0277"
ms.assetid: 8abec3eb-4d4c-4aab-87cc-d0444ab23535
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0277
'classe' n’implémente pas le membre d’interface 'accesseur'. 'accesseur\_de\_classe' n’est pas public  
  
 Cette erreur se produit quand vous essayez d’implémenter une propriété d’une interface et que l’implémentation de l’accesseur de propriété dans la classe n’est pas public. Les méthodes qui implémentent des membres d’interface doivent avoir une accessibilité publique. Pour résoudre cette erreur, supprimez le modificateur d’accès sur l’accesseur de propriété.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0277 :  
  
```  
// CS0277.cs public interface MyInterface { int Property { get; set; } } public class MyClass : MyInterface   // CS0277 { public int Property { get { return 0; } // Try this instead: //set { } protected set { } } }  
```