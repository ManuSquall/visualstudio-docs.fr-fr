---
title: Fonctionnalités du shell Workflow Designer
description: Découvrez comment les fonctionnalités du shell Concepteur de flux de travail contiennent un certain nombre de boutons pour la gestion de l’affichage actuel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04de797b991b2c660b61ae401fb928561343b812
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875144"
---
# <a name="workflow-designer-shell-features"></a>Fonctionnalités du shell Workflow Designer

Concepteur de flux de travail est composé de trois zones d’interface utilisateur majeures : l’aire du concepteur, la barre de navigation au-dessus et l’interpréteur de commandes situé en dessous. La barre de navigation, située en haut de l'écran, sert à afficher la liste des ancêtres de l'activité racine actuelle. Pour plus d’informations, consultez [Comment : utiliser la navigation de navigation](../workflow-designer/how-to-use-breadcrumb-navigation.md). L'aire du concepteur, située au centre de l'écran, permet de composer des flux de travail. L'interpréteur de commandes, situé en bas de l'écran, contient plusieurs boutons pour gérer l'affichage actuel.

## <a name="shell-features"></a>Fonctionnalités de l'interpréteur de commandes
 La barre de l'interpréteur de commandes comporte des boutons à droite qui permettent d'effectuer un zoom avant ou arrière dans le flux de travail, d'ajuster le contenu du flux de travail à la taille de l'écran et d'afficher ou masquer la vue d'ensemble. Vous pouvez également effectuer un zoom avant ou arrière dans un flux de travail à l'aide des raccourcis clavier CTRL++ et CTRL+-.

## <a name="overview-map"></a>Vue d'ensemble
 La vue d'ensemble affiche une version réduite de l'activité entière à la racine de la barre de navigation actuelle, notamment tous ses enfants et tous leurs enfants développés. Une fenêtre d'affichage, un rectangle avec une bordure orange, met en surbrillance la partie de l'activité actuellement affichée dans l'éditeur. Faire glisser le rectangle dans la vue d'ensemble fait défiler Workflow Designer et modifie l'affichage de l'éditeur.

> [!NOTE]
> L’interface utilisateur Concepteur de flux de travail est virtualisée. Les concepteurs d'activités ne sont affichés que s'ils sont nécessaires. Si une partie du flux de travail n'a jamais été dessinée dans l'aire du concepteur, elle apparaît en blanc dans la vue d'ensemble. Le défilement de la vue d'ensemble permet de dessiner l'intégralité du flux de travail.

## <a name="copying-or-saving-workflows-as-images"></a>Copie ou enregistrement de flux de travail en tant qu'images
 Les flux de travail peuvent être copiés au format bitmap ou enregistrés aux formats bitmap ou vectoriel. La copie ou l'enregistrement d'une image permettent d'exporter vers un autre programme une vue d'activité entière à la racine de la barre de navigation actuelle, notamment tous ses enfants et tous leurs enfants développés.

 Pour copier en tant qu’image, cliquez avec le bouton droit n’importe où dans le concepteur, puis sélectionnez **copier en tant qu’image**. Pour enregistrer en tant qu’image, cliquez avec le bouton droit n’importe où dans le concepteur et sélectionnez **enregistrer en tant qu’image**. Les flux de travail peuvent être enregistrés aux formats JPG, PNG, GIF ou XPS. Le format est sélectionné dans la boîte de dialogue **Enregistrer sous** , dans la zone de liste déroulante **type de fichier,** en bas de la fenêtre.

## <a name="fonts-and-colors"></a>Polices et couleurs

Les polices utilisées dans les Concepteur de flux de travail à l’intérieur de Visual Studio sont contrôlées par la police de l’environnement. Les couleurs affichées dans Concepteur de flux de travail changent si vous utilisez un modèle de couleurs à contraste élevé pour le thème de votre système d’exploitation. Vous devez redémarrer Visual Studio après avoir apporté une modification aux paramètres de police ou de couleur pour que les modifications soient prises en compte dans Concepteur de flux de travail.