---
title: "D&#233;pannage des exceptions&#160;: System.Printing.PrintingCanceledException | Microsoft Docs"
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
  - "PrintingCanceledException (exception)"
  - "System.Printing.PrintingCanceledException (exception)"
ms.assetid: bec418d6-f168-4a73-962f-5ee0427600b6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Printing.PrintingCanceledException
Une exception <xref:System.Printing.PrintingCanceledException> se produit lorsque le code tente d'accéder à un travail d'impression annulé.  
  
## Notes  
 Si vous créez une application Windows Presentation Foundation \(WPF\) qui comprend des fonctionnalités d'impression et autorise l'annulation de travaux d'impression, assurez\-vous de gérer cette exception correctement. Une exception non gérée de ce type peut provoquer qu'une application Windows Presentation Foundation cesse de répondre.  
  
## Voir aussi  
 <xref:System.Printing.PrintingCanceledException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)