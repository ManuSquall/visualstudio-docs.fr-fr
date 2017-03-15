---
title: "D&#233;pannage des exceptions&#160;: System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException | Microsoft Docs"
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
  - "EHWRTTrackingProfileDeserialization"
helpviewer_keywords: 
  - "System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException (exception)"
  - "TrackingProfileDeserializationException (exception)"
ms.assetid: ce8fe4c1-43e3-4930-947e-74b8d94f32bf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException
Une exception <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException> est levée lorsqu'un document XML ne peut pas être désérialisé dans un <xref:System.Workflow.Runtime.Tracking.TrackingProfile> par un <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer>.  
  
## Notes  
 Lorsque <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> renvoie cette exception, il fournit un message qui décrit le motif de l'exception. Dans certains cas, <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> fournit la liste des avertissements et erreurs de validation rencontrées lors de la tentative de désérialisation de <xref:System.Workflow.Runtime.Tracking.TrackingProfile>. Lorsqu'une telle liste est fournie, la propriété <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException.ValidationEventArgs%2A> la contient.  
  
## Voir aussi  
 <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)