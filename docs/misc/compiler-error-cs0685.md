---
title: "Erreur du compilateur CS0685 | Microsoft Docs"
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
  - "CS0685"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0685"
ms.assetid: 20d7c6cf-a388-430f-b22b-232536912491
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0685
Le membre conditionnel 'member' ne peut pas avoir un paramètre out  
  
 Lors de l’utilisation de l’attribut <xref:System.Diagnostics.ConditionalAttribute> sur une méthode, cette dernière ne peut pas avoir de paramètre out \(de sortie\). En effet, la valeur de la variable utilisée pour le paramètre out n’est pas définie au cas où l’appel de la méthode ne serait compilé vers aucun élément. Pour éviter cette erreur, supprimez le paramètre out de la déclaration de méthode conditionnelle, ou n’utilisez pas l’attribut Conditional.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0685 :  
  
```  
// CS0685.cs using System.Diagnostics; class C { [Conditional("DEBUG")] void trace(out int i)  // CS0685 { i = 1; } }  
```