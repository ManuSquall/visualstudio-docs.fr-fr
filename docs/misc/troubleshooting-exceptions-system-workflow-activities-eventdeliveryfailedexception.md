---
title: "D&#233;pannage des exceptions&#160;: System.Workflow.Activities.EventDeliveryFailedException | Microsoft Docs"
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
  - "EHWAEventDeliveryFailed"
helpviewer_keywords: 
  - "System.Workflow.Activities.EventDeliveryFailedException (exception)"
  - "EventDeliveryFailedException (exception)"
ms.assetid: 85ee2cb8-5cd1-4878-9421-2a78614e819f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Workflow.Activities.EventDeliveryFailedException
Une exception <xref:System.Workflow.Activities.EventDeliveryFailedException> est renvoyée lorsqu'un événement déclenché à partir de l'hôte ne peut pas être remis à l'instance du workflow. L'événement est généralement déclenché à partir d'un <xref:System.Workflow.Activities.ExternalDataExchangeService> sur une instance de workflow. Cette classe ne peut pas être héritée.  
  
## Notes  
 La chaîne suivante est ajoutée au journal des événements lorsque cette exception est renvoyée : `Event '{1}' on interface type '{0}' for instance id '{2}' cannot be delivered`.  
  
 Lorsque vous utilisez un workflow de machine à états, vous pouvez obtenir une exception avec le message `Queue '{0}' is not enabled`. Cela arrive lorsque l'état actuel de l'ordinateur d'état ne parvient pas à gérer un événement spécifique. Par exemple, le message se produit lorsqu'un état autre que l'état actuel contient le <xref:System.Workflow.Activities.EventDrivenActivity> qui contient le <xref:System.Workflow.Activities.HandleExternalEventActivity> représenté par la file d'attente `'{0}'`.  
  
## Voir aussi  
 <xref:System.Workflow.Activities.EventDeliveryFailedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)