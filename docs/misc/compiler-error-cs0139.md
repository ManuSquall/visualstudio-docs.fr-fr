---
title: "Erreur du compilateur CS0139 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0139"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0139"
ms.assetid: 235ba3d4-566c-4ef6-801a-a338f4f2a12d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0139
Absence de boucle englobant 'break' ou 'continue'  
  
 Une instruction break ou continue a été rencontrée en dehors d’une boucle.  
  
 Pour plus d’informations, consultez [Instructions de saut](/dotnet/csharp/language-reference/keywords/jump-statements).  
  
 L’exemple suivant génère deux fois l’erreur CS0139 :  
  
```  
// CS0139.cs namespace x { public class a { public static void Main() { continue;  // CS0139 break;     // CS0139 } } }  
```