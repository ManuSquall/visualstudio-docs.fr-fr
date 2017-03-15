---
title: "Erreur du compilateur CS0718 | Microsoft Docs"
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
  - "CS0718"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0718"
ms.assetid: f18ea7b7-7495-4039-9876-409e9fe98ba1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0718
'type' : les types static ne peuvent pas être utilisés en tant qu’arguments de type  
  
 Dans la mesure où un type static ne peut pas être instancié, il ne peut pas être utilisé comme argument générique. Pour résoudre cette erreur, supprimez le type static de l’argument générique.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0718 :  
  
```  
// CS0718.cs public static class SC { public static void F() { } } public class G<T> { } public class CMain { public static void Main() { G<SC> gsc = new G<SC>();  // CS0718 } }  
```