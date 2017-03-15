---
title: "Le nom de source sp&#233;cifi&#233; dans le journal est inscrit aupr&#232;s d’un journal autre que celui sp&#233;cifi&#233; dans EventLogName | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le nom de source sp&#233;cifi&#233; dans le journal est inscrit aupr&#232;s d’un journal autre que celui sp&#233;cifi&#233; dans EventLogName
Le `EventLog` essaie de faire référence à une source qui est inscrite auprès d’un autre journal. Si vous écrivez des entrées dans le journal des événements, vous devez spécifier la propriété <xref:System.Diagnostics.EventLog.Source%2A>. La propriété <xref:System.Diagnostics.EventLog.Source%2A> inscrit votre composant auprès du journal des événements comme source d’entrées valide. Une même source ne peut être associée \(et donc écrire des entrées\) qu’à un seul journal des événements à la fois.  
  
 Par défaut, si vous tentez d’écrire une entrée sans avoir d’abord inscrit votre composant en tant que source valide, le système inscrit automatiquement la source auprès du journal des événements, en utilisant la valeur de la propriété <xref:System.Diagnostics.EventLog.Source%2A> comme chaîne source.  
  
### Pour corriger cette erreur  
  
-   Vérifiez que la source est inscrite auprès du journal approprié. Pour ce faire, utilisez la méthode <xref:System.Diagnostics.EventLog.CreateEventSource%2A> ou l’une de ses surcharges pour spécifier une chaîne qui identifie votre composant auprès du journal des événements.  
  
## Voir aussi  
 [Administering Event Logs](http://msdn.microsoft.com/fr-fr/35f53238-bdd2-417b-acd8-2fd9f7397f18)   
 [Event Log References](http://msdn.microsoft.com/fr-fr/4af0661c-6c96-49f4-961d-b26ed9bc3e87)   
 [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/fr-fr/948ff920-a739-4e66-a191-ee951512d42c)   
 [How to: Remove an Event Source](http://msdn.microsoft.com/fr-fr/bc66c900-4b8a-426a-b8e2-17031a20167e)