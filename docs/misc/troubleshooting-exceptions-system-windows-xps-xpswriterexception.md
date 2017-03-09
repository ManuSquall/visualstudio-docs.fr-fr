---
title: "D&#233;pannage des exceptions&#160;: System.Windows.Xps.XpsWriterException | Microsoft Docs"
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
  - "EHWXXpsWriter"
helpviewer_keywords: 
  - "System.Windows.Xps.XpsWriterException (exception)"
  - "XpsWriterException (exception)"
ms.assetid: 3b9fbb94-ed67-44f2-82bb-af5cb5ada1ef
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Windows.Xps.XpsWriterException
Une exception <xref:System.Windows.Xps.XpsWriterException> est renvoyée lorsqu'une méthode d'un objet <xref:System.Windows.Xps.XpsDocumentWriter> ou <xref:System.Windows.Xps.VisualsToXpsDocument> est appelée et est incompatible avec l'état actuel de l'objet.  
  
## Notes  
 Par exemple, cette exception est renvoyée si la méthode `CancelAsync` de l'un des types d'objets est appelée alors que l'objet n'exécute pas d'opération d'écriture asynchrone.  
  
## Voir aussi  
 <xref:System.Windows.Xps.XpsWriterException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)