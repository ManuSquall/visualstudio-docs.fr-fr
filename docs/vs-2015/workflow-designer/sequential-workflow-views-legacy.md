---
title: Vues de Workflow séquentiel (hérité) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 46c37ec7f3813078b9e70076bf92e6d0e1b86453
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507602"
---
# <a name="sequential-workflow-views-legacy"></a>Vues de workflow séquentiel (héritées)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] fournit un [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité qui peut être utilisé pour cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Le [!INCLUDE[wfd2](../includes/wfd2-md.md)] permet de créer graphiquement des applications [!INCLUDE[wf](../includes/wf-md.md)] grâce à l'interface utilisateur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que vous connaissez bien. Les applications [!INCLUDE[wf](../includes/wf-md.md)] sont composées d'étapes du processus de workflow appelées activités. Pour créer un workflow, composez des activités sur l’aire de conception en faisant glisser leurs concepteurs d’activités respectifs de **boîte à outils** sur l’aire de conception.  
  
 Lorsque vous créez un workflow séquentiel, qui est un [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), trois vues du flux de travail sont disponibles. Ces vues sont accessibles à partir de la **Workflow** menu et dans le menu contextuel sur l’aire de conception.  
  
 Le tableau suivant contient le nom et la description de chaque vue.  
  
|Option de menu/d'onglet|Description|  
|----------------------|-----------------|  
|**Afficher le workflow séquentiel**|Cliquez sur l’aire de conception et sélectionnez le **afficher le workflow séquentiel** option dans le menu contextuel pour afficher la **Workflow séquentiel** vue, qui indique l’activité en graphique représentation sous forme de flux de travail séquentiel. Ou sélectionnez **afficher le workflow séquentiel** à partir de la **Workflow** menu.|  
|**Afficher le Gestionnaire d’annulation**|Cliquez sur l’aire de conception et sélectionnez le **afficher le Gestionnaire d’annuler** option dans le menu contextuel pour afficher le **Workflow séquentiel** afficher, qui affiche le [CancellationHandlerActivity ](http://go.microsoft.com/fwlink?LinkID=65050) activité associée au workflow. Ou sélectionnez **le Gestionnaire d’annulation vue** à partir de la **Workflow** menu.|  
|**Afficher le Gestionnaire d’erreur**|Cliquez sur l’aire de conception et sélectionnez le **afficher le Gestionnaire d’erreur** option dans le menu contextuel pour afficher le **erreurs** afficher, qui affiche le [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) activité associée au workflow. Ou sélectionnez **afficher le Gestionnaire d’erreur** à partir de la **Workflow** menu.|  
  
 Pour plus d’informations sur des vues similaires, consultez [vues d’activité (hérité)](../workflow-designer/activity-views-legacy.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues d’activité (hérité)](../workflow-designer/activity-views-legacy.md)   
 [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Modes de création de flux de travail](http://go.microsoft.com/fwlink?LinkID=65014)