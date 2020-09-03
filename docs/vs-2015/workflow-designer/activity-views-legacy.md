---
title: Vues d’activité (héritées) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7546f752ef7ee1053d1b0b785334a8da814720c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851483"
---
# <a name="activity-views-legacy"></a>Vues d'activité (héritées)
La plupart des activités fournies par [!INCLUDE[wf](../includes/wf-md.md)], et depuis lesquelles sont composés les workflows, proposent plusieurs vues de création disponibles dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Quand vous faites glisser un concepteur d’activités de la **boîte à outils** vers l’aire de conception, et ensuite, chaque fois que vous sélectionnez l’activité, vous pouvez basculer entre les différentes vues de conception à l’aide du menu **Workflow** ou en cliquant avec le bouton droit sur l’activité sélectionnée. De la même façon, lorsque vous déplacez le pointeur sur le nom d’une activité sélectionnée, un jeu déroulant d’onglets apparaît, que vous pouvez utiliser pour alterner entre les différentes vues.

 Chaque activité a au moins une vue ; Il s’agit de la vue par défaut affichée lorsque vous faites glisser un concepteur d’activités de la **boîte à outils** vers l’aire de conception. Cette vue par défaut de l’activité est disponible sous l’option **vue [type d’activité]** dans les menus et onglets, par exemple **afficher en parallèle**. La plupart des activités possède des vues supplémentaires et des activités différentes peuvent posséder des vues différentes. Par exemple, l’activité [activité TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx) a la vue compensation et l’activité [activité EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx) a une vue événements. La plupart des activités fournies avec Windows Workflow Foundation ont des vues de conception **afficher le gestionnaire d’annulation** et afficher les **erreurs** pour afficher les [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) et les [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) associés.

 Le tableau suivant contient le nom et la description de chaque vue.

|Option de menu/d'onglet|Description|
|----------------------|-----------------|
|**Vue [type d'activité]**|Sélectionnez cette option de menu ou d'onglet pour afficher la représentation graphique par défaut de l'activité sélectionnée.|
|**Afficher le gestionnaire d'annulation**|Sélectionnez cette vue de menu ou d’onglet pour afficher le [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) associé à l’activité sélectionnée.|
|**Afficher le gestionnaire d'erreur**|Sélectionnez cette vue de menu ou d’onglet pour afficher le [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) associé à l’activité sélectionnée.|
|**Afficher le gestionnaire de compensation**|Sélectionnez cette vue de menu ou d’onglet pour afficher le [CompensationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensationhandleractivity.aspx) associé au [activité TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx)sélectionné.|
|**Afficher le gestionnaire d'événements**|Sélectionnez cette vue de menu ou d’onglet pour afficher le [EventHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlersactivity.aspx) associé au [activité EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx)sélectionné.|

 Pour plus d’informations sur les vues similaires, consultez [vues de workflow séquentielles (héritées)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Voir aussi
 Vues de workflow séquentiel des [activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md) [(héritées)](../workflow-designer/sequential-workflow-views-legacy.md)
