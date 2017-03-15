---
title: "Avertissement du compilateur (niveau&#160;1) CS3022 | Microsoft Docs"
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
  - "CS3022"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3022"
ms.assetid: 9340645c-10c3-4e21-a825-3f05fae02ff7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS3022
l’attribut CLSCompliant n’a pas de sens lorsqu’il est appliqué à des paramètres. Essayez de le placer dans la méthode à la place.  
  
 La conformité CLS n’est pas vérifiée pour les paramètres de méthode, car les règles de conformité CLS s’appliquent aux méthodes et aux déclarations de type.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS3022 :  
  
```  
// CS3022.cs // compile with: /W:1 using System; [assembly: CLSCompliant(true)] [CLSCompliant(true)] public class C { public void F([CLSCompliant(true)] int i) { } public static void Main() { } }  
```