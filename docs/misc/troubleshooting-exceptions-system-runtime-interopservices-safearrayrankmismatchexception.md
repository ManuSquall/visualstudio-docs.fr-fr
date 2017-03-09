---
title: "D&#233;pannage des exceptions&#160;: System.Runtime.InteropServices.SafeArrayRankMismatchException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSafeArrayRankMismatch"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "SafeArrayRankMismatchException (classe)"
ms.assetid: 6c69355c-8bfd-49bb-acad-b4d7236ae2e7
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Runtime.InteropServices.SafeArrayRankMismatchException
Une exception <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> est levée lorsque le rang d'un SAFEARRAY entrant ne correspond pas au rang spécifié dans la signature managée.  
  
## Conseils associés  
 **Assurez\-vous que votre tableau dispose du nombre de dimensions requis.**  
 Étant donné que le rang et les limites d'un tableau sécurisé ne peuvent pas être déterminés à partir de la bibliothèque de types, le rang est considéré comme étant égal à 1 et la limite inférieure égale à 0. Le rang et les limites doivent être définis dans la signature managée produite par [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md).  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Default Marshaling for Arrays](../Topic/Default%20Marshaling%20for%20Arrays.md)   
 [Tableaux](/dotnet/visual-basic/programming-guide/language-features/arrays/index)