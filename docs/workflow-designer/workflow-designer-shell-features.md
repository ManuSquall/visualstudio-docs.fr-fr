---
title: Fonctionnalités de Shell du Concepteur de flux de travail | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecf7d88b6436ba117b85c2ea6cc423520f9fd873
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="workflow-designer-shell-features"></a>Fonctionnalités du shell Workflow Designer

Concepteur de flux de travail Windows se compose de trois principales zones de l’interface utilisateur : l’aire du concepteur, la barre de navigation au-dessus de lui et l’interpréteur de commandes en dessous. La barre de navigation, située en haut de l'écran, sert à afficher la liste des ancêtres de l'activité racine actuelle. Pour plus d’informations, consultez [Comment : utiliser arborescence de Navigation](../workflow-designer/how-to-use-breadcrumb-navigation.md). L'aire du concepteur, située au centre de l'écran, permet de composer des flux de travail. L'interpréteur de commandes, situé en bas de l'écran, contient plusieurs boutons pour gérer l'affichage actuel.

## <a name="shell-features"></a>Fonctionnalités de l'interpréteur de commandes
 La barre de l'interpréteur de commandes comporte des boutons à droite qui permettent d'effectuer un zoom avant ou arrière dans le flux de travail, d'ajuster le contenu du flux de travail à la taille de l'écran et d'afficher ou masquer la vue d'ensemble. Vous pouvez également effectuer un zoom avant ou arrière dans un flux de travail à l'aide des raccourcis clavier CTRL++ et CTRL+-.

## <a name="overview-map"></a>Vue d'ensemble
 La vue d'ensemble affiche une version réduite de l'activité entière à la racine de la barre de navigation actuelle, notamment tous ses enfants et tous leurs enfants développés. Une fenêtre d'affichage, un rectangle avec une bordure orange, met en surbrillance la partie de l'activité actuellement affichée dans l'éditeur. Faire glisser le rectangle dans la vue d'ensemble fait défiler Workflow Designer et modifie l'affichage de l'éditeur.

> [!NOTE]
> L'interface utilisateur de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] est virtualisée. Les concepteurs d'activités ne sont affichés que s'ils sont nécessaires. Si une partie du flux de travail n'a jamais été dessinée dans l'aire du concepteur, elle apparaît en blanc dans la vue d'ensemble. Le défilement de la vue d'ensemble permet de dessiner l'intégralité du flux de travail.

## <a name="copying-or-saving-workflows-as-images"></a>Copie ou enregistrement de flux de travail en tant qu'images
 Les flux de travail peuvent être copiés au format bitmap ou enregistrés aux formats bitmap ou vectoriel. La copie ou l’enregistrement d’une image permettent d’exporter vers un autre programme une vue d’activité entière à la racine de la barre de navigation actuelle, notamment tous ses enfants et tous leurs enfants développés.

 Pour copier en tant qu’image, avec le bouton droit n’importe où dans le concepteur et sélectionnez **copie comme Image**. Pour enregistrer en tant qu’image, avec le bouton droit n’importe où dans le concepteur et sélectionnez **enregistrer en tant qu’Image**. Les flux de travail peuvent être enregistrés aux formats JPG, PNG, GIF ou XPS. Le format est sélectionné sur la **enregistrer en tant que** boîte de dialogue de la **enregistrer en tant que Type :** liste déroulante en bas de la fenêtre.

## <a name="fonts-and-colors"></a>Polices et couleurs

Les polices utilisées dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] sous [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] sont contrôlées par la police d'environnement. Les couleurs affichées dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] changent si vous utilisez un modèle de couleurs à contraste élevé pour le thème de votre système d'exploitation. Vous devez redémarrer [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] après avoir modifié les paramètres de police ou de couleur pour que vos modifications prennent effet dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].