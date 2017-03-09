---
title: "Erreur du compilateur CS1622 | Microsoft Docs"
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
  - "CS1622"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1622"
ms.assetid: 6b53a777-4cd8-423a-84ff-22ff588044d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1622
Impossible de retourner une valeur à partir d’un itérateur. Utilisez l’instruction yield return pour retourner une valeur ou yield break pour mettre fin à l’itération.  
  
 Un itérateur est une fonction spéciale qui retourne une valeur via l’instruction yield au lieu de l’instruction return. Pour plus d’informations, consultez **Itérateurs**.  
  
 L’exemple suivant génère l’erreur CS1622 :  
  
```  
// CS1622.cs // compile with: /target:library using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { return (IEnumerator) this;  // CS1622 yield return this;   // OK } }  
```