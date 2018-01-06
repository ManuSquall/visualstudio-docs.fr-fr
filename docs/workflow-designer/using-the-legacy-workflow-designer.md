---
title: "À l’aide du Concepteur de Workflow hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 7faec3b7a6bf33886928034e1f68ab31c7a60b03
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-legacy-workflow-designer"></a>Utilisation du Concepteur de Workflow hérité
Le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité fourni par [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] peut être utilisé pour cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Il est accessible en sélectionnant le le **.NET Framework 3.0** option ou **.NET Framework 3.5** option dans la liste déroulante située en haut de la **nouveau projet** fenêtre. L’option par défaut dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] est **.NET Framework 4** qui sert à créer [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] les applications qui ciblent le [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].  
  
 Le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] permet de créer graphiquement des applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] grâce à l'interface utilisateur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que vous connaissez bien. Les applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] sont composées d'étapes du processus de workflow appelées activités. Pour créer un workflow, composez des activités sur l’aire de conception en faisant glisser leurs concepteurs d’activités respectifs de **boîte à outils** sur l’aire de conception.  
  
 Le tableau suivant répertorie les fonctionnalités clés de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour Windows Workflow Foundation.  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Activité de glisser-déposer|Faites glisser les activités à partir de la **boîte à outils** sur l’aire de conception pour créer un flux de travail.|  
|Explorateur de propriétés|La norme **propriétés** fenêtre dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est utilisé pour configurer les propriétés d’une activité.|  
|Zoom|Les jumelles **le niveau de Zoom** située sous la barre de défilement verticale sur le côté droit de l’aire de conception. Cliquez sur les jumelles et sélectionnez un pourcentage de zoom pour effectuer un zoom avant ou arrière du graphique de workflow. Vous pouvez également utiliser le **panoramique** options de curseur icône en forme de loupe pour effectuer un zoom avant et arrière.|  
|Panoramique|Le **panoramique** , un cercle contenant quatre flèches qui pointent dans quatre directions, est située sous la barre de défilement verticale sur le côté droit de l’aire de conception juste en dessous de l’icône de zoom (jumelles). Si vous cliquez sur l'icône de panoramique, un menu contextuel affiche les options de curseur suivantes :<br /><br /> -La **zoom avant** curseur de loupe vous permet de faire un zoom en cliquant sur l’aire de conception.<br />-La **Zoom arrière** curseur de loupe vous permet d’effectuer un zoom arrière en cliquant sur l’aire de conception.<br />-La **outil de Navigation** main vous permet de « saisissez » et déplacez la vue d’un flux de travail dans l’aire de conception.<br />-La **par défaut** pointeur vous permet de basculer d’autres curseurs vers le pointeur par défaut.|  
|Défilement automatique|En cas de workflow de grande taille, vous pouvez placer une activité au delà de l'affichage visible de la zone d'aire de conception. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous permet de faire glisser une activité vers le bord de l'aire de conception, près de l'emplacement où vous souhaitez placer l'activité. La vue de l'aire de conception défile automatiquement dans cette direction.|  
|Balises actives|Les activités qui ne sont pas configurées complètement ou correctement sont signalées par une icône en forme de point d'exclamation. Vous pouvez cliquer sur l’icône afin d’afficher la liste déroulante des besoins de configuration répertoriés pour cette activité. Vous pouvez ensuite utiliser le **propriétés** fenêtre Configurer l’activité de manière appropriée. Une fois que toutes les propriétés sont valides pour l'activité, l'icône de point d'exclamation disparaît.|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Visual Studio pour Windows Workflow (hérité)](../workflow-designer/visual-studio-workflow-windows-legacy.md)  
  
 [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)  
  
 [Vues Flux de travail séquentiels (hérité)](../workflow-designer/sequential-workflow-views-legacy.md)  
  
 [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)  
  
 [Utilisation de thèmes dans les flux de travail (hérité)](../workflow-designer/using-themes-in-workflows-legacy.md)  
  
 [Utilisation du Concepteur de flux de travail de machine à états hérité](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)  
  
 [Utilisation du concepteur d’activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)  
  
 [Aide de l’interface utilisateur du concepteur hérité pour Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de flux de travail](http://go.microsoft.com/fwlink?LinkID=65010)