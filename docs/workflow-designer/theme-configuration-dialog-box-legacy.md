---
title: Concepteur de flux de travail - boîte de dialogue de Configuration de thème (hérité)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.ComponentModel.Design.ThemeConfigurationDialog.UI
helpviewer_keywords:
- themes, configuring
- Theme Configuration dialog box
ms.assetid: 9e6d182a-c4d9-4e71-b2b9-02f675fc2b29
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07ae376a09afd73c5744f7d1587c637a4b55410d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="theme-configuration-dialog-box-legacy"></a>Configuration du thème, boîte de dialogue (héritée)

Cette rubrique décrit comment utiliser le **Configuration du thème** boîte de dialogue dans le Concepteur de flux de travail Windows hérité. Utilisez le Concepteur de flux de travail hérité lorsque vous avez besoin cibler le .NET Framework version 3.5 ou du WinFX.

Un thème définit les couleurs d'arrière-plan et de premier plan, les styles, les icônes et les autres éléments visuels d'un workflow. Vous pouvez enregistrer des thèmes en vue de les réutiliser pour d'autres workflows.

Vous créez et modifiez des thèmes à l’aide de la **Configuration du thème** boîte de dialogue. Pour ouvrir la boîte de dialogue, sélectionnez **créer un nouveau thème** sur la **Workflow** menu, ou sélectionnez le flux de travail aire de conception et sélectionnez **créer un nouveau thème**.

Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **Configuration du thème** boîte de dialogue.

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Nom du thème :**|Le nom qui identifie le thème dans le [thèmes, Concepteur de Workflow, Options de boîte de dialogue (héritée)](../workflow-designer/themes-workflow-designer-options-dialog-box-legacy.md). Un nom modifiable est généré pour les nouveaux thèmes.|
|**Emplacement du thème :**|Chemin d’accès et nom du fichier de thème. Un nom de fichier modifiable est généré pour les nouveaux thèmes, sur la base du nom de thème généré. Si vous modifiez le nom de thème généré, vous pouvez modifier le nom de fichier pour qu'il corresponde au nom de thème.|
|**...**|Cliquez pour sélectionner l’emplacement d’enregistrement du fichier du thème de workflow, qui utilise une extension de nom de fichier .wtm. Le chemin d’accès sélectionné s’affichent dans le **emplacement du thème** zone de texte.|
|**Sélectionnez le concepteur et configurer les propriétés :**|Le volet gauche répertorie une arborescence des activités pour lesquelles le thème peut être personnalisé. Sélectionnez une activité dans l'arborescence ; les propriétés de thème correspondant à l'activité s'affichent dans le volet de propriétés, qui se trouve à droite du volet d'arborescence. Cliquez sur une propriété pour modifier sa valeur.|
|**Aperçu**|Cliquez pour afficher une fenêtre permettant de voir les effets des modifications de propriété apportées.|

## <a name="see-also"></a>Voir aussi

- [Thèmes, Concepteur de flux de travail, Options, boîte de dialogue (hérité)](../workflow-designer/themes-workflow-designer-options-dialog-box-legacy.md)
- [Aide de l’interface utilisateur du concepteur hérité pour Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)