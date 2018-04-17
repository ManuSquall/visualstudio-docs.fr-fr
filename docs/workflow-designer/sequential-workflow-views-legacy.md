---
title: Vues de Workflow séquentiel (héritées) | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6b42ba9c1c9f7dbe2beb4a741501967e4968508
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sequential-workflow-views-legacy"></a>Vues de workflow séquentiel (héritées)
[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] fournit un concepteur de flux de travail Windows hérité qui peut être utilisé pour cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] permet de créer graphiquement des applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] grâce à l'interface utilisateur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que vous connaissez bien. Les applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] sont composées d'étapes du processus de workflow appelées activités. Pour créer un workflow, composez des activités sur l’aire de conception en faisant glisser leurs concepteurs d’activités respectifs de **boîte à outils** sur l’aire de conception.

 Lorsque vous créez un flux de travail séquentiel, qui est un [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), trois vues du flux de travail sont disponibles. Ces vues sont accessibles à partir de la **Workflow** menu et dans le menu contextuel sur l’aire de conception.

 Le tableau suivant contient le nom et la description de chaque vue.

|Option de menu/d'onglet|Description|
|----------------------|-----------------|
|**Afficher le workflow séquentiel**|Cliquez sur l’aire de conception et sélectionnez le **afficher le workflow séquentiel** option dans le menu contextuel pour afficher la **Workflow séquentiel** vue, qui montre l’activité basée graphique représentation sous forme de flux de travail séquentiel. Ou sélectionnez **afficher le workflow séquentiel** à partir de la **Workflow** menu.|
|**Afficher le Gestionnaire d’annulation**|Avec le bouton droit de l’aire de conception et sélectionnez le **afficher le Gestionnaire d’annulation** option dans le menu contextuel pour afficher la **Workflow séquentiel** afficher, qui affiche le [CancellationHandlerActivity ](http://go.microsoft.com/fwlink?LinkID=65050) activité associée au workflow. Ou sélectionnez **afficher le Gestionnaire d’annulation** à partir de la **Workflow** menu.|
|**Afficher le Gestionnaire d’erreur**|Cliquez sur l’aire de conception et sélectionnez le **afficher le Gestionnaire d’erreur** option dans le menu contextuel pour afficher le **erreurs** afficher, qui affiche le [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) activité associée au flux de travail. Ou sélectionnez **afficher le Gestionnaire d’erreur** à partir de la **Workflow** menu.|

 Pour plus d’informations sur des vues similaires, consultez [vues d’activité (héritées)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Voir aussi

- [Vues Activité (hérité)](../workflow-designer/activity-views-legacy.md)
- [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)
- [Modes de création de flux de travail](http://go.microsoft.com/fwlink?LinkID=65014)