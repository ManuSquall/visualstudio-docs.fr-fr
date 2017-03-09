---
title: "D&#233;pannage des exceptions&#160;: System.DuplicateWaitObjectException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DuplicateWaitObjectException (classe)"
ms.assetid: b9ff6932-a7cf-4a89-bd7d-e4ef1a3ff353
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.DuplicateWaitObjectException
Une exception <xref:System.DuplicateWaitObjectException> est levée si le tableau d'objets <xref:System.Threading.WaitHandle> passé à <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> contient des handles du système d'exploitation en double.  
  
## Conseils associés  
 **Assurez\-vous que les objets WaitHandle passés à WaitAll ou WaitAny sont uniques.**  
 Un tableau <xref:System.Threading.WaitHandle> ne peut pas contenir plusieurs références au même objet.  
  
### Notes  
 Le Common Language Runtime \(CLR\) fournit un mécanisme de synchronisation de threads fondé sur des objets de synchronisation qui attendent d'être exécutés dans un tableau d'objets <xref:System.Threading.WaitHandle>.  
  
## Voir aussi  
 <xref:System.DuplicateWaitObjectException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)