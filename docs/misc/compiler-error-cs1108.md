---
title: "Erreur du compilateur CS1108 | Microsoft Docs"
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
  - "CS1108"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1108"
ms.assetid: 26e82d6a-6ebf-4beb-912e-1bcb86b668aa
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1108
Un paramètre ne peut pas avoir tous les modificateurs spécifiés ; il y a trop de modificateurs dans le paramètre.  
  
 Certaines combinaisons de modificateurs de paramètres, tels que `ref` et `out`, ne sont pas autorisées en raison de significations mutuellement exclusives pour le compilateur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1108 :  
  
```  
// cs1108.cs // Compile with: /target:library public class Test { // Regular Instance Method. public void TestMethod(ref out int i) {} // CS1108 }  
```