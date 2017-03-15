---
title: "D&#233;pannage des exceptions&#160;: System.ServiceModel.ServerTooBusyException | Microsoft Docs"
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
  - "System.ServiceModel.ServerTooBusyException (exception)"
  - "ServerTooBusyException (exception)"
ms.assetid: 80eb606a-ab3c-48af-b747-c9902989a059
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.ServiceModel.ServerTooBusyException
Une exception <xref:System.ServiceModel.ServerTooBusyException> est renvoyée si un serveur est trop occupé à accepter un message.  
  
## Notes  
 Cette exception dérive du <xref:System.ServiceModel.CommunicationException> qui représente une classe d'erreurs récupérables qui peuvent être renvoyées pendant la communication entre des points de terminaison. Il est attendu que les applications [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] clientes et de service fiables gèrent ces exceptions. Pour empêcher un gestionnaire de <xref:System.ServiceModel.CommunicationException> d'intercepter le <xref:System.ServiceModel.ServerTooBusyException> plus spécifique, interceptez cette exception avant de gérer <xref:System.ServiceModel.CommunicationException>.  
  
## Voir aussi  
 <xref:System.ServiceModel.ServerTooBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)