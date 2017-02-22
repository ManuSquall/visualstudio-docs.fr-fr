---
title: "Vues d&#39;activit&#233; (h&#233;rit&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "activités, vues d'activité"
  - "vues d'activité"
  - "vues, activité"
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Vues d&#39;activit&#233; (h&#233;rit&#233;es)
La plupart des activités fournies par [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], et depuis lesquelles sont composés les workflows, proposent plusieurs vues de création disponibles dans le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité.Lorsque vous faites glisser un concepteur d'activités de la **boîte à outils** vers l'aire de conception, et par la suite toutes les fois que vous sélectionnez l'activité, vous pouvez alterner entre les différentes vues de création en utilisant le menu **Workflow** ou en cliquant avec le bouton droit sur l'activité sélectionnée.De la même façon, lorsque vous déplacez le pointeur sur le nom d'une activité sélectionnée, un jeu déroulant d'onglets apparaît, que vous pouvez utiliser pour alterner entre les différentes vues.  
  
 Chaque activité possède au minimum une vue qui est la vue par défaut affichée lorsque vous faites glisser un concepteur d'activités de la **boîte à outils** vers l'aire de conception.Cette vue par défaut d'activité est disponible via l'option **Vue \[type d'activité\]** dans les menus et dans l'onglet \(**Vue parallèle**, par exemple\).La plupart des activités possède des vues supplémentaires et des activités différentes peuvent posséder des vues différentes.Par exemple, l'activité [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) possède la vue de compensation et l'activité [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) possède une vue d'événements.Les activités contenues dans Windows Workflow Foundation possèdent pour la plupart les vues **Afficher le gestionnaire d'annulation** et **Afficher les erreurs**, qui permettent de consulter l'activité [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) et l'activité [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associées.  
  
 Le tableau suivant contient le nom et la description de chaque vue.  
  
|Option de menu\/d'onglet|Description|  
|------------------------------|-----------------|  
|**Vue \[type d'activité\]**|Sélectionnez cette option de menu ou d'onglet pour afficher la représentation graphique par défaut de l'activité sélectionnée.|  
|**Afficher le gestionnaire d'annulation**|Sélectionnez cette option de menu ou d'onglet pour afficher l'activité [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associée à l'activité sélectionnée.|  
|**Afficher le gestionnaire d'erreur**|Sélectionnez cette option de menu ou d'onglet pour afficher l'activité [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associée à l'activité sélectionnée.|  
|**Afficher le gestionnaire de compensation**|Sélectionnez cette option de menu ou d'onglet pour consulter l'activité [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) associée à l'activité [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) sélectionnée.|  
|**Afficher le gestionnaire d'événements**|Sélectionnez cette option de menu ou d'onglet pour consulter l'activité [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) associée à l'activité [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) sélectionnée.|  
  
 Pour plus d'informations sur des vues similaires, consultez [Vues de workflow séquentiel \(héritées\)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## Voir aussi  
 [Activités de workflow héritées](../workflow-designer/legacy-workflow-activities.md)   
 [Vues de workflow séquentiel \(héritées\)](../workflow-designer/sequential-workflow-views-legacy.md)