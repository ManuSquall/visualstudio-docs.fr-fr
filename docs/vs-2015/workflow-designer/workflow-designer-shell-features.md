---
title: Fonctionnalités de Shell du Concepteur de flux de travail | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6b432dd6dd0a19f6509ad1ff133424fcbc387fb6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952316"
---
# <a name="workflow-designer-shell-features"></a>Fonctionnalités du shell Workflow Designer
[!INCLUDE[wfd1](../includes/wfd1-md.md)] est composé de trois zones d'interface utilisateur principales : l'aire du concepteur, la barre de navigation au-dessus et l'interpréteur de commandes en dessous. La barre de navigation, située en haut de l'écran, sert à afficher la liste des ancêtres de l'activité racine actuelle. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Guide pratique pour Utilisez l’arborescence de Navigation](../workflow-designer/how-to-use-breadcrumb-navigation.md). L'aire du concepteur, située au centre de l'écran, permet de composer des flux de travail. L'interpréteur de commandes, situé en bas de l'écran, contient plusieurs boutons pour gérer l'affichage actuel.  
  
## <a name="shell-features"></a>Fonctionnalités de l'interpréteur de commandes  
 La barre de l'interpréteur de commandes comporte des boutons à droite qui permettent d'effectuer un zoom avant ou arrière dans le flux de travail, d'ajuster le contenu du flux de travail à la taille de l'écran et d'afficher ou masquer la vue d'ensemble. Vous pouvez également effectuer un zoom avant ou arrière dans un flux de travail à l'aide des raccourcis clavier CTRL++ et CTRL+-.  
  
## <a name="overview-map"></a>Vue d'ensemble  
 La vue d'ensemble affiche une version réduite de l'activité entière à la racine de la barre de navigation actuelle, notamment tous ses enfants et tous leurs enfants développés. Une fenêtre d'affichage, un rectangle avec une bordure orange, met en surbrillance la partie de l'activité actuellement affichée dans l'éditeur. Faire glisser le rectangle dans la vue d'ensemble fait défiler Workflow Designer et modifie l'affichage de l'éditeur.  
  
> [!NOTE]
>  L'interface utilisateur de [!INCLUDE[wfd2](../includes/wfd2-md.md)] est virtualisée. Les concepteurs d'activités ne sont affichés que s'ils sont nécessaires. Si une partie du flux de travail n'a jamais été dessinée dans l'aire du concepteur, elle apparaît en blanc dans la vue d'ensemble. Le défilement de la vue d'ensemble permet de dessiner l'intégralité du flux de travail.  
  
## <a name="copying-or-saving-workflows-as-images"></a>Copie ou enregistrement de flux de travail en tant qu'images  
 Les flux de travail peuvent être copiés au format bitmap ou enregistrés aux formats bitmap ou vectoriel. La copie ou l'enregistrement d'une image permettent d'exporter vers un autre programme une vue d'activité entière à la racine de la barre de navigation actuelle, notamment tous ses enfants et tous leurs enfants développés.  
  
 Pour copier en tant qu’image, avec le bouton droit n’importe où dans le concepteur et sélectionnez **copie comme Image**. Pour enregistrer en tant qu’image, avec le bouton droit n’importe où dans le concepteur et sélectionnez **enregistrer en tant qu’Image**. Les flux de travail peuvent être enregistrés aux formats JPG, PNG, GIF ou XPS. Le format est sélectionné sur la **enregistrer en tant que** boîte de dialogue dans le **enregistrer en tant que Type :** zone de liste en bas de la fenêtre de liste déroulante.  
  
## <a name="fonts-and-colors"></a>Polices et couleurs  
 Les polices utilisées dans [!INCLUDE[wfd2](../includes/wfd2-md.md)] sous [!INCLUDE[vs2010](../includes/vs2010-md.md)] sont contrôlées par la police d'environnement. Les couleurs affichées dans [!INCLUDE[wfd2](../includes/wfd2-md.md)] changent si vous utilisez un modèle de couleurs à contraste élevé pour le thème de votre système d'exploitation. Vous devez redémarrer [!INCLUDE[vs2010](../includes/vs2010-md.md)] après avoir modifié les paramètres de police ou de couleur pour que vos modifications prennent effet dans [!INCLUDE[wfd2](../includes/wfd2-md.md)].