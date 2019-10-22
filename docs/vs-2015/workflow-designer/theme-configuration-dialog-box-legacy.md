---
title: Configuration du thème, boîte de dialogue (héritée) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ThemeConfigurationDialog.UI
helpviewer_keywords:
- themes, configuring
- Theme Configuration dialog box
ms.assetid: 9e6d182a-c4d9-4e71-b2b9-02f675fc2b29
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8171c6dcfe285ade07531896893915d0e209e0c1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670192"
---
# <a name="theme-configuration-dialog-box-legacy"></a>Configuration du thème, boîte de dialogue (héritée)
Cette rubrique décrit comment utiliser la boîte de dialogue **configuration du thème** dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Un thème définit les couleurs d'arrière-plan et de premier plan, les styles, les icônes et les autres éléments visuels d'un workflow. Vous pouvez enregistrer des thèmes en vue de les réutiliser pour d'autres workflows.

 Vous créez et modifiez des thèmes à l’aide de la boîte de dialogue **configuration du thème** . Pour ouvrir la boîte de dialogue, sélectionnez **créer un nouveau thème** dans le menu **Workflow** , ou cliquez avec le bouton droit sur l’aire de conception de workflow et sélectionnez **créer un nouveau thème**.

 Le tableau suivant décrit les éléments d’interface utilisateur (IU) de la boîte de dialogue **configuration du thème** .

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Nom du thème :**|Nom qui identifie le thème dans la [boîte de dialogue thèmes, concepteur de flux de travail, options (hérité)](../workflow-designer/themes-workflow-designer-options-dialog-box-legacy.md). Un nom modifiable est généré pour les nouveaux thèmes.|
|**Emplacement du thème :**|Chemin d'accès et nom du fichier de thème. Un nom de fichier modifiable est généré pour les nouveaux thèmes, sur la base du nom de thème généré. Si vous modifiez le nom de thème généré, vous pouvez modifier le nom de fichier pour qu'il corresponde au nom de thème.|
|**...**|Cliquez pour sélectionner l'emplacement d'enregistrement du fichier du thème de workflow, qui utilise une extension de nom de fichier .wtm. Le chemin d’accès sélectionné s’affiche dans la zone de texte **emplacement du thème** .|
|**Sélectionnez Concepteur et configurez les propriétés :**|Le volet gauche répertorie une arborescence des activités pour lesquelles le thème peut être personnalisé. Sélectionnez une activité dans l’arborescence ; les propriétés de thème correspondant à l’activité s’affichent dans le volet de propriétés, qui se trouve à droite du volet d’arborescence. Cliquez sur une propriété pour modifier sa valeur.|
|**Aperçu**|Cliquez pour afficher une fenêtre permettant de voir les effets des modifications de propriété apportées.|

## <a name="see-also"></a>Voir aussi
 [Thèmes, concepteur de flux de travail, boîte de dialogue Options (hérité)](../workflow-designer/themes-workflow-designer-options-dialog-box-legacy.md) [concepteur hérité pour Windows Workflow Foundation aide sur l’interface utilisateur](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)