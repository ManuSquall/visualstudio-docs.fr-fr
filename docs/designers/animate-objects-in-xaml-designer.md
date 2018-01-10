---
title: Animer des objets dans le concepteur XAML | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 57aa814ac458fc3c893f8a2d557840d936ed033b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="animate-objects-in-xaml-designer"></a>Animer des objets dans le concepteur XAML
Vous pouvez créer des animations courtes qui déplacent des objets ou les font apparaître ou disparaître en fondu.  
  
 Pour commencer, créez un *storyboard*. Un storyboard contient une ou plusieurs *chronologies*. Définissez des *images clés* sur une chronologie pour représenter les modifications apportées aux propriétés. Ensuite, au moment d'exécuter l'animation, Blend interpole les modifications apportées aux propriétés au cours de la période désignée. Il en résulte une transition en douceur. Vous pouvez animer n'importe quelle propriété appartenant à un objet, y compris les propriétés non visuelles.  
  
 L'illustration suivante montre un storyboard nommé **MoveUp**. La chronologie contient des images clés qui représentent les positions X et Y d'un rectangle. Quand cette animation s'exécute, le rectangle se déplace en douceur d'une position à un autre.  
  
 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")  
  
 Découvrez comment créer des animations en regardant ces vidéos.  
  
|Regardez une courte vidéo :|Apprenez à :|  
|--------------------------|-------------------|  
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Créer des chronologies](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Créer une chronologie et y utiliser des objets.|  
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Ajouter des images clés et répéter l’animation](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Ajouter des images clés et définir les propriétés de chaque image clé. Exécutez ensuite l'animation et observez les objets s'enchaîner en douceur.|  
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Ajouter des déclencheurs d’événements pour l’interactivité](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Démarrer une animation quand un événement se produit, par exemple, au moment où la fenêtre se charge.|  
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Animer des couleurs](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Utiliser une animation pour modifier la couleur d'un objet.|  
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Créer et modifier des trajectoires](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Animer des objets le long d’un tracé.|  
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Atténuer des images clés](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Accélérer ou ralentir une animation vers le début (*atténuation en entrée*) ou vers la fin (*atténuation en sortie*) d'une animation.|  
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Animer un bouton](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Créer des effets intéressants qui apparaissent sur un bouton quand l'utilisateur pointe dessus.|  
|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Créer une animation et utiliser l’atténuation](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Animer des effets qui apparaissent quand un utilisateur clique sur un bouton dans l'image d'une calculatrice.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une interface utilisateur à l’aide de Blend pour Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)