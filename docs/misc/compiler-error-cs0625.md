---
title: "Erreur du compilateur CS0625 | Microsoft Docs"
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
  - "CS0625"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0625"
ms.assetid: 44091813-9988-436c-b35e-e24094793782
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0625
'champ' : les types de champ d’instance marqués avec StructLayout\(LayoutKind.Explicit\) doivent posséder un attribut FieldOffset  
  
 Quand un struct est marqué avec un attribut **StructLayout** explicite, tous les champs du struct doivent avoir l’attribut [FieldOffset](frlrfsystemruntimeinteropservicesfieldoffsetattributeclasstopic). Pour plus d’informations, consultez [StructLayoutAttribute, classe](frlrfSystemRuntimeInteropServicesStructLayoutAttributeClassTopic).  
  
 L’exemple suivant génère l’erreur CS0625 :  
  
```  
// CS0625.cs // compile with: /target:library using System; using System.Runtime.InteropServices; [StructLayout(LayoutKind.Explicit)] struct A { public int i;   // CS0625 not static; an instance field } // OK [StructLayout(LayoutKind.Explicit)] struct B { [FieldOffset(5)] public int i; }  
```