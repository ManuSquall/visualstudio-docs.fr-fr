---
title: Animer des objets dans le concepteur XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ea2fdf1f47385a9be26fa65a93b9104b2d864079
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658019"
---
# <a name="animate-objects-in-xaml-designer"></a>Animer des objets dans le concepteur XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez créer des animations courtes qui déplacent des objets ou les font apparaître ou disparaître en fondu.

 Pour commencer, créez un *storyboard*. Un storyboard contient une ou plusieurs *chronologies*. Définissez des *images clés* sur une chronologie pour représenter les modifications apportées aux propriétés. Ensuite, au moment d'exécuter l'animation, Blend interpole les modifications apportées aux propriétés au cours de la période désignée. Il en résulte une transition en douceur. Vous pouvez animer n'importe quelle propriété appartenant à un objet, y compris les propriétés non visuelles.

 L'illustration suivante montre un storyboard nommé **MoveUp**. La chronologie contient des images clés qui représentent les positions X et Y d'un rectangle. Quand cette animation s'exécute, le rectangle se déplace en douceur d'une position à un autre.

 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")

 Découvrez comment créer des animations en regardant ces vidéos.

|Regardez une courte vidéo :|Apprenez à :|
|--------------------------|-------------------|
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [créer des chronologies](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Créer une chronologie et y utiliser des objets.|
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [Ajouter des images clés et répéter l’animation](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Ajouter des images clés et définir les propriétés de chaque image clé. Exécutez ensuite l'animation et observez les objets s'enchaîner en douceur.|
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [Ajouter des déclencheurs d’événements pour l’interactivité](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Démarrer une animation quand un événement se produit, par exemple, au moment où la fenêtre se charge.|
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [animer les couleurs](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Utiliser une animation pour modifier la couleur d'un objet.|
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [créer et modifier des](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths) trajectoires|Animer des objets le long d’un tracé.|
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [facilitent les images clés](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Accélérer ou ralentir une animation vers le début (*atténuation en entrée*) ou vers la fin (*atténuation en sortie*) d'une animation.|
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [animer le bouton](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Créer des effets intéressants qui apparaissent sur un bouton quand l'utilisateur pointe dessus.|
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [créer une animation et utiliser l’accélération](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Animer des effets qui apparaissent quand un utilisateur clique sur un bouton dans l'image d'une calculatrice.|

## <a name="see-also"></a>Voir aussi
 [Création d’une interface utilisateur à l’aide de Blend pour Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
