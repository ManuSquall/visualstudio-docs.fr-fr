---
title: "Avertissement du compilateur (niveau&#160;1) CS3023 | Microsoft Docs"
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
  - "CS3023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3023"
ms.assetid: fd7782f9-f18a-4ce8-843b-95bf19b54317
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS3023
L’attribut CLSCompliant n’a pas de sens quand il est appliqué à des types de retour.  Essayez de le placer dans la méthode à la place.  
  
 La conformité CLS n’est pas vérifiée pour les types de retour de fonction, car les règles de conformité CLS s’appliquent aux méthodes et aux déclarations de type.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS3023 :  
  
```  
// C3023.cs [assembly:System.CLSCompliant(true)] public class Test { [return:System.CLSCompliant(true)]  // CS3023 // Try this instead: // [method:System.CLSCompliant(true)] public static int Main() { return 0; } }  
```