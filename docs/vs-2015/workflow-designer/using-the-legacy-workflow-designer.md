---
title: Utilisation du Concepteur de flux de travail hérité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72c92b4431c21c27bc1fe2ff86b24c850cc34694
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846080"
---
# <a name="using-the-legacy-workflow-designer"></a>Utilisation du Concepteur de Workflow hérité
Le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité fourni par [!INCLUDE[vs2010](../includes/vs2010-md.md)] peut être utilisé pour cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Pour y accéder, vous pouvez sélectionner l’option **.NET Framework 3,0** ou l’option **.NET Framework 3,5** dans la liste déroulante en haut de la fenêtre **nouveau projet** . L’option par défaut dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] est **.NET Framework 4** qui est utilisé pour créer des [!INCLUDE[wf](../includes/wf-md.md)] applications qui ciblent [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] .

 Le [!INCLUDE[wfd2](../includes/wfd2-md.md)] permet de créer graphiquement des applications [!INCLUDE[wf](../includes/wf-md.md)] grâce à l'interface utilisateur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que vous connaissez bien. Les applications [!INCLUDE[wf](../includes/wf-md.md)] sont composées d'étapes du processus de workflow appelées activités. Pour créer un workflow, composez des activités sur l’aire de conception en faisant glisser leurs concepteurs d’activités respectifs de la **boîte à outils** vers l’aire de conception.

 Le tableau suivant répertorie les fonctionnalités clés de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour Windows Workflow Foundation.

|Fonctionnalité|Description|
|-------------|-----------------|
|Activité de glisser-déplacer|Faites glisser les activités de la **boîte à outils** vers l’aire de conception pour créer un Workflow.|
|Explorateur de propriétés|La fenêtre **Propriétés** standard de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est utilisée pour configurer les propriétés d’une activité.|
|Zoom|L’icône de **niveau de zoom** jumelles se trouve sous la barre de défilement verticale sur le côté droit de l’aire de conception. Cliquez sur les jumelles et sélectionnez un pourcentage de zoom pour faire en sorte que le graphique du flux de travail effectue un zoom avant ou arrière. Vous pouvez également utiliser les options de curseur de la loupe de l’icône **panoramique** pour effectuer un zoom avant et arrière.|
|Panoramique|L’icône **panoramique** , un cercle contenant quatre flèches croisées pointant dans quatre directions, se trouve sous la barre de défilement verticale, à droite de l’aire de conception, juste en dessous de l’icône de zoom jumelles. Si vous cliquez sur l'icône de panoramique, un menu contextuel affiche les options de curseur suivantes :<br /><br /> -Le curseur de loupe **Zoom avant** vous permet d’effectuer un zoom avant en cliquant sur l’aire de conception.<br />-Le curseur de loupe **Zoom** arrière vous permet d’effectuer un zoom arrière en cliquant sur l’aire de conception.<br />-Le curseur manuel de l' **outil de navigation** vous permet de « récupérer » et de déplacer l’affichage d’un flux de travail dans l’aire de conception.<br />-Le curseur fléché **par défaut** vous permet de basculer des autres curseurs vers le curseur fléché par défaut.|
|Défilement automatique|En cas de workflow de grande taille, vous pouvez placer une activité au delà de l'affichage visible de la zone d'aire de conception. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vous permet de faire glisser une activité vers le bord de l'aire de conception, près de l'emplacement où vous souhaitez placer l'activité. La vue de l'aire de conception défile automatiquement dans cette direction.|
|Balises actives|Les activités qui ne sont pas configurées complètement ou correctement sont signalées par une icône en forme de point d'exclamation. Vous pouvez cliquer sur l'icône afin d'afficher la liste déroulante des besoins de configuration répertoriés pour cette activité. Vous pouvez ensuite utiliser la fenêtre **Propriétés** pour configurer l’activité de façon appropriée. Une fois que toutes les propriétés sont valides pour l'activité, l'icône de point d'exclamation disparaît.|

## <a name="in-this-section"></a>Dans cette section
 [Visual Studio pour Windows Workflow (hérité)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [Création de projets de workflows hérités](../workflow-designer/creating-legacy-workflow-projects.md)

 [Vues de workflow séquentiel (héritées)](../workflow-designer/sequential-workflow-views-legacy.md)

 [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)

 [Utilisation de thèmes dans les flux de travail (hérité)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [Utilisation du Concepteur de Workflow d'ordinateur d'état hérité](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [Utilisation du concepteur d'activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)

 [Aide de l’interface utilisateur du concepteur hérité pour Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>Voir aussi
 [Développement de workflows](https://msdn2.microsoft.com/library/bb628448.aspx)
