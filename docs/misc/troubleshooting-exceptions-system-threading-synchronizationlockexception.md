---
title: "D&#233;pannage des exceptions&#160;: System.Threading.SynchronizationLockException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SynchronizationLockException (exception)"
  - "System.Threading.SynchronizationLockException (exception)"
ms.assetid: 82d80643-fc5c-40ae-a579-46869772d25c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Threading.SynchronizationLockException
Exception levée lorsqu'une méthode exige de l'appelant qu'il possède un verrou sur un objet `Monitor` donné et que la méthode est appelée par un appelant qui ne possède pas ce verrou.  
  
## Notes  
 Une <xref:System.Threading.SynchronizationLockException> est levée par appel aux méthodes <xref:System.Threading.Monitor.Exit%2A>, <xref:System.Threading.Monitor.Pulse%2A>, <xref:System.Threading.Monitor.PulseAll%2A> et <xref:System.Threading.Monitor.Wait%2A> de la classe `Monitor` à partir d'un bloc de code non synchronisé.  
  
## Voir aussi  
 <xref:System.Threading.SynchronizationLockException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)