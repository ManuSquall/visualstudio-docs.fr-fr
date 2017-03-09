---
title: "D&#233;pannage des exceptions&#160;: System.Workflow.Runtime.Hosting.PersistenceException | Microsoft Docs"
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
  - "EHWRHPersistence"
helpviewer_keywords: 
  - "PersistenceException (exception)"
  - "System.Workflow.Runtime.Hosting.PersistenceException (exception)"
ms.assetid: cb2fb820-f990-4728-9a7f-5ec6fd8d5b10
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Workflow.Runtime.Hosting.PersistenceException
Une exception <xref:System.Workflow.Runtime.Hosting.PersistenceException> est renvoyée lorsque le service de persistance ne peut pas satisfaire une demande.  
  
## Notes  
 Le <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> renvoie une <xref:System.Workflow.Runtime.Hosting.PersistenceException> s'il ne peut pas exécuter une demande pour valider une portée terminée ou l'état de l'instance du workflow dans sa base de données.  
  
 Si vous implémentez un service de persistance par dérivation de la classe <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> ou <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, vous pouvez renvoyer l'<xref:System.Workflow.Runtime.Hosting.PersistenceException> avec un message approprié pour indiquer toute condition d'erreur rencontrée par votre service qui l'empêche de satisfaire une demande du moteur d'exécution du workflow.  
  
 Pour plus d'informations, voir <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService>.  
  
## Voir aussi  
 <xref:System.Workflow.Runtime.Hosting.PersistenceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)