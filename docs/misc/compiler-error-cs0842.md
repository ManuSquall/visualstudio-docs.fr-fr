---
title: "Erreur du compilateur CS0842 | Microsoft Docs"
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
  - "CS0842"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0842"
ms.assetid: 93a8b333-efc4-40c7-ae53-5264f721a74f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0842
Impossible d’utiliser des propriétés implémentées automatiquement dans un type marqué avec StructLayout\(LayoutKind.Explicit\).  
  
 Les champs de stockage des propriétés implémentées automatiquement sont fournis par le compilateur, et le champ n’est pas accessible au code source. Elles ne sont donc pas compatibles avec <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
### Pour corriger cette erreur  
  
1.  Définissez la propriété en tant que propriété normale dans laquelle vous fournissez les corps d’accesseur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0842 :  
  
```  
// cs0842.cs using System; using System.Runtime.InteropServices; namespace TestNamespace { [StructLayout(LayoutKind.Explicit)] struct Str { public int Num // CS0842 { get; set; } static int Main() { return 1; } } }  
```