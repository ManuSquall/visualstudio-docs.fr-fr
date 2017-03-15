---
title: "Erreur du compilateur CS0418 | Microsoft Docs"
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
  - "CS0418"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0418"
ms.assetid: b78fafde-428b-4fa2-a933-c4614760bb71
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0418
'class name' : une classe abstraite ne peut pas être sealed ou static  
  
 Une classe abstraite ne peut pas servir à créer des objets, sauf si elle est dérivée ; le fait qu’elle soit sealed n’a donc aucun sens. Le fait qu’une classe abstraite soit static n’a pas non plus de sens ; les classes abstraites sont conçues pour prendre en charge une hiérarchie d’objets qui utilise la classe abstraite comme base.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0418 :  
  
```  
// CS0418.cs public abstract sealed class C  // CS0418 { } sealed static class S  // CS0418 { } public class MyClass { public static void Main() { } }  
```