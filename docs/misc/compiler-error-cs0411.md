---
title: "Erreur du compilateur CS0411 | Microsoft Docs"
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
  - "CS0411"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0411"
ms.assetid: 290947c9-10d0-427e-99f2-bff20299d533
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0411
Les arguments de type pour la méthode 'method' ne peut pas être déduits à partir de l’utilisation. Essayez de spécifier les arguments de type de façon explicite.  
  
 Cette erreur se produit si vous appelez une méthode générique sans fournir explicitement les arguments de type et que le compilateur ne peut pas déduire les arguments de type prévus. Pour éviter cette erreur, ajoutez les arguments de type prévus entre crochets pointus.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0411 :  
  
```  
// CS0411.cs class C { void G<T>() { } public static void Main() { G();  // CS0411 // Try this instead: // G<int>(); } }  
```  
  
## Exemple  
 Des erreurs peuvent également se produire quand le paramètre est `null`, car celui\-ci ne contient aucune information de type :  
  
```  
// CS0411b.cs class C { public void F<T>(T t) where T : C { } public static void Main() { C c = new C(); c.F(null);  // CS0411 } }  
```