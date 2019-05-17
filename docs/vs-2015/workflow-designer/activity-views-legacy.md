---
title: Vues d’activité (hérité) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 62b3c9185226512ff28c8d028cd0ba7d33b0f12f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977456"
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