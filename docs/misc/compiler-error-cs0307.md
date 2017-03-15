---
title: "Erreur du compilateur CS0307 | Microsoft Docs"
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
  - "CS0307"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0307"
ms.assetid: 202a9985-ed7a-4e0a-9573-5624e066d314
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0307
'construct' 'identifier' n’est pas une méthode générique. Si vous voulez une liste d’expressions, utilisez les parenthèses autour de l’expression \<.  
  
 La construction nommée ne correspond pas à un type ni à une méthode, les seules constructions qui peuvent prendre des arguments génériques Supprimez les arguments de type figurant entre crochets. Si un générique est exigé, déclarez votre construction générique en tant que type ou méthode générique.  
  
 L’exemple suivant génère l’erreur CS0307 :  
  
```  
// CS0307.cs class C { public int P { get { return 1; } } public static void Main() { C c = new C(); int p = c.P<int>();  // CS0307 – C.P is a property // Try this instead // int p = c.P; } }  
```