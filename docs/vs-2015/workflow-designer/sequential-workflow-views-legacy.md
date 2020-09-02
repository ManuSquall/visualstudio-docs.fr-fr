---
title: Vues de workflow séquentiel (hérité) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 76d357c1f6ebc770d0e625e60bae237e37e0a6aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846215"
---
# <a name="sequential-workflow-views-legacy"></a>Vues de workflow séquentiel (héritées)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] fournit un hérité [!INCLUDE[wfd1](../includes/wfd1-md.md)] qui peut être utilisé pour cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Le [!INCLUDE[wfd2](../includes/wfd2-md.md)] permet de créer graphiquement des applications [!INCLUDE[wf](../includes/wf-md.md)] grâce à l'interface utilisateur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que vous connaissez bien. Les applications [!INCLUDE[wf](../includes/wf-md.md)] sont composées d'étapes du processus de workflow appelées activités. Pour créer un workflow, composez des activités sur l’aire de conception en faisant glisser leurs concepteurs d’activités respectifs de la **boîte à outils** vers l’aire de conception.

 Lorsque vous créez un workflow séquentiel, qui est un [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx), trois vues du workflow sont disponibles. Ces affichages sont accessibles à partir du menu **Workflow** et du menu contextuel sur l’aire de conception.

 Le tableau suivant contient le nom et la description de chaque vue.

|Option de menu/d'onglet|Description|
|----------------------|-----------------|
|**Afficher le workflow séquentiel**|Cliquez avec le bouton droit sur l’aire de conception et sélectionnez l’option **afficher le workflow séquentiel** dans le menu contextuel pour afficher la vue de **Workflow séquentiel** , qui affiche la représentation graphique basée sur les activités du workflow séquentiel. Ou sélectionnez **Afficher Workflow séquentiel** dans le menu **Workflow** .|
|**Afficher le gestionnaire d'annulation**|Cliquez avec le bouton droit sur l’aire de conception et sélectionnez l’option **afficher le gestionnaire d’annulation** dans le menu contextuel pour afficher la vue de **Workflow séquentiel** , qui affiche l’activité [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) associée au workflow. Ou sélectionnez **afficher le gestionnaire d’annulation** dans le menu **Workflow** .|
|**Afficher le gestionnaire d'erreur**|Cliquez avec le bouton droit sur l’aire de conception et sélectionnez l’option **afficher le gestionnaire d’erreurs** dans le menu contextuel pour afficher la vue **Erreurs** , qui affiche l’activité [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) associée au workflow. Ou sélectionnez **afficher le gestionnaire d’erreurs** dans le menu **Workflow** .|

 Pour plus d’informations sur les affichages similaires, consultez [vues d’activité (héritées)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Voir aussi
 [Vues d’activité (héritées) création de projets de](../workflow-designer/activity-views-legacy.md) [Workflow hérités](../workflow-designer/creating-legacy-workflow-projects.md) [modes de création de flux de travail](https://msdn2.microsoft.com/library/bb628440.aspx)
