---
title: "D&#233;pannage des exceptions&#160;: System.ServiceModel.Persistence.InstanceNotFoundException | Microsoft Docs"
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
  - "InstanceNotFoundException (exception)"
  - "System.ServiceModel.Persistence.InstanceNotFoundException (exception)"
ms.assetid: e3905352-dff0-41d4-b970-8e1b26d85a83
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.ServiceModel.Persistence.InstanceNotFoundException
Une exception <xref:System.ServiceModel.Persistence.InstanceNotFoundException> est levée dans les circonstances suivantes :  
  
-   une opération est exécutée sur une instance de service durable marquée pour conclusion ;  
  
-   un fournisseur de persistance créé par un <xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory> essaie de verrouiller, de déverrouiller ou de traiter de toute autre façon des données d'état de processus qui sont introuvables dans la base de données.  
  
## Voir aussi  
 <xref:System.ServiceModel.Persistence.InstanceNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)