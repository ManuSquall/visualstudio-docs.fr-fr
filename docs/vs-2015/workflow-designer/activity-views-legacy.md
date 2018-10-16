---
title: Vues d’activité (hérité) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: e5fb8368228118b210865b1a351d12b1b5da4b27
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229308"
---
# <a name="activity-views-legacy"></a>Vues d'activité (héritées)
La plupart des activités fournies par [!INCLUDE[wf](../includes/wf-md.md)], et depuis lesquelles sont composés les workflows, proposent plusieurs vues de création disponibles dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Lorsque vous faites glisser un concepteur d’activités à partir de la **boîte à outils** sur l’aire de conception et par la suite, chaque fois que vous sélectionnez l’activité, vous pouvez basculer entre les différents modes design à l’aide la **Workflow**menu ou en double-cliquant sur l’activité sélectionnée. De la même façon, lorsque vous déplacez le pointeur sur le nom d’une activité sélectionnée, un jeu déroulant d’onglets apparaît, que vous pouvez utiliser pour alterner entre les différentes vues.  
  
 Chaque activité possède au moins une vue ; Il s’agit d’affichage par défaut lorsque vous faites glisser un concepteur d’activités à partir de la **boîte à outils** sur l’aire de conception. Cette vue par défaut d’activité est disponible en tant que le **afficher [type d’activité]** option sous l’onglet, par exemple et les menus **vue parallèle**. La plupart des activités possède des vues supplémentaires et des activités différentes peuvent posséder des vues différentes. Par exemple, le [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) activité possède la vue de compensation et la [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) activité a des événements d’une vue. La plupart des activités qui sont fournis avec Windows Workflow Foundation ont **le Gestionnaire d’annulation vue** et **afficher les erreurs** concevoir des vues pour afficher le [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) et un [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) qui s’y rapportent.  
  
 Le tableau suivant contient le nom et la description de chaque vue.  
  
|Option de menu/d'onglet|Description|  
|----------------------|-----------------|  
|**Vue [type d’activité]**|Sélectionnez cette option de menu ou d'onglet pour afficher la représentation graphique par défaut de l'activité sélectionnée.|  
|**Afficher le Gestionnaire d’annulation**|Sélectionnez cette option de menu ou d’onglet pour consulter les [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associé à l’activité sélectionnée.|  
|**Afficher le Gestionnaire d’erreur**|Sélectionnez cette option de menu ou d’onglet pour consulter les [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associé à l’activité sélectionnée.|  
|**Afficher le Gestionnaire de Compensation**|Sélectionnez cette option de menu ou d’onglet pour consulter les [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) associéau [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|  
|**Afficher le Gestionnaire d’événements**|Sélectionnez cette option de menu ou d’onglet pour consulter les [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) associée le [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|  
  
 Pour plus d’informations sur des vues similaires, consultez [vues de Workflow séquentiel (héritées)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Activités de flux de travail hérité](../workflow-designer/legacy-workflow-activities.md)   
 [Vues Flux de travail séquentiels (hérité)](../workflow-designer/sequential-workflow-views-legacy.md)