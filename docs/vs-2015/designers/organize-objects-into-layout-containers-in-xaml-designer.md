---
title: Organiser les objets en conteneurs de disposition dans le concepteur XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 90c30f27ada6673608a1c5cf9500207f9aeb2d72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664200"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organiser les objets en conteneurs de disposition dans le concepteur XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Réfléchissez à l'endroit où vous souhaitez faire figurer les objets dans une page (des objets tels que des images, des boutons et des vidéos). Peut-être souhaiterez-vous qu'ils apparaissent dans des lignes et des colonnes, dans une seule ligne verticale ou horizontale ou bien à des emplacements fixes ?

 Une fois que vous avez déterminé l'aspect que vous voulez donner à la page, choisissez un panneau de disposition. Il s'agit de la structure de base de toutes les pages à laquelle vous allez ajouter vos objets. Par défaut, il s’agit d’une **grille**, mais vous pouvez changer cela.

 Si les panneaux de disposition permettent de disposer les objets dans une page, leur fonction ne s'arrête pas là. Ils vous permettent de concevoir pour différentes tailles et résolutions d'écran. Quand les utilisateurs exécutent votre application, tout ce qui figure dans le panneau de disposition est redimensionné pour s'adapter à la taille d'écran de leur appareil. Bien entendu, vous pouvez éviter cela en changeant tout ou partie du comportement de la disposition. Pour ce faire, vous pouvez utiliser les propriétés de hauteur et de largeur.

 Vous trouverez dans cette page une description des différents panneaux de disposition et contrôles, ainsi que des liens vers de courtes vidéos qui vous aideront à les prendre en main.

> [!NOTE]
> Certaines vidéos peuvent faire référence à Blend ou à Expression Blend, qui utilisent le même concepteur XAML que Visual Studio et Blend pour Visual Studio.

## <a name="layout-panels"></a>Panneaux de disposition
 Commencez votre page en choisissant l'un de ces panneaux de disposition. Votre page peut en contenir plusieurs. Par exemple, vous pouvez commencer par un panneau de disposition **Grid** et ajouter à une zone de ce dernier un **StackPanel** pour disposer les contrôles à la verticale dans cet élément **Grid**.

 Les panneaux de disposition suivants sont les plus couramment utilisés, mais il en existe d'autres. Vous les trouverez tous dans le panneau **Composants**.

- [Grid](#Grid)

- [UniformGrid](#Uniform)

- [Canvas](#Canvas)

- [StackPanel](#Stack)

- [WrapPanel](#Wrap)

- [DockPanel](#Dock)

### <a name="Grid"></a> Grid
 Permet de disposer les objets dans des lignes et des colonnes.

 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441f-9136-98375fee87b7")

 **Regardez une brève vidéo :** ![configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [à l’aide de grilles](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)

### <a name="Uniform"></a> UniformGrid
 Permet de disposer les objets dans des régions de grille égales ou uniformes. Ce panneau est très pratique pour organiser une liste d'images.

 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")

 (Disponible uniquement pour les projets WPF)

 **Regardez une brève vidéo :** ![configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [utilisation d’un UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)

### <a name="Canvas"></a> Canvas
 Permet de disposer les objets librement. Quand les utilisateurs exécutent votre application, ces éléments ont des positions fixes sur l'écran.

 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")

 **Regardez une brève vidéo :** ![configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [utilisation du canevas](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)

### <a name="Stack"></a> StackPanel
 Permet de disposer les objets dans une seule ligne horizontale ou verticale.

 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")

 **Regardez une brève vidéo :** ![configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [utilisation de StackPanel et WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)

### <a name="Wrap"></a> WrapPanel
 Permet de disposer les objets les uns à la suite des autres, de gauche à droite. Quand il n’y a plus de place à l’extrémité droite du panneau, il *renvoie* le contenu à la ligne suivante, et ainsi de suite de gauche à droite et de haut en bas. Vous pouvez aussi disposer un panneau de renvoi à la ligne à la verticale de sorte que les objets se suivent de haut en bas et de gauche à droite.

 (Disponible uniquement pour les projets WPF)

 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")

 **Regardez une brève vidéo :** ![configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [utilisation de StackPanel et WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)

### <a name="Dock"></a> DockPanel
 Permet de disposer les objets de telle sorte qu’il restent, ou s’*ancrent*, sur un bord du panneau.

 (Disponible uniquement pour les projets WPF)

 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")

 **Regardez une brève vidéo :** ![configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [WPF-DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Contrôles de disposition
 Vous pouvez aussi ajouter vos objets à des contrôles de disposition. Ils n'offrent pas autant de fonctionnalités qu'un panneau de disposition, mais ils peuvent s'avérer utiles pour certains scénarios.

 Les contrôles de disposition suivants sont les plus couramment utilisés, mais il en existe d'autres. Vous les trouverez tous dans le panneau **Composants**.

- [Border](#Border)

- [Fenêtre contextuelle](#Popup)

- [ScrollViewer](#Scroll)

- [UniformGrid](#Uniform)

- [Viewbox](#View)

### <a name="Border"></a> Border
 Permet de créer une bordure, un arrière-plan ou les deux autour d'un objet. Vous ne pouvez ajouter qu’un seul objet à un **Border**. Si vous voulez appliquer une bordure ou un arrière-plan à plusieurs objets, ajoutez un panneau de disposition au **Border**. Ajoutez ensuite les objets à ce panneau ou contrôle.

 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-bbc4-57538b8289ff")

 **Regardez une brève vidéo :** ![configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "Installées bldadminconsoleinitialconfigicon") [utilisation des bordures](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)

### <a name="Popup"></a> Popup
 Permet d'afficher des informations ou des options à l'intention des utilisateurs dans une fenêtre. Vous ne pouvez ajouter qu’un seul objet à un **Popup**. Par défaut, un **Popup** contient un **Grid**, mais vous disposez d’autres options.

### <a name="Scroll"></a> ScrollViewer
 Permet aux utilisateurs de faire défiler une page ou une de ses zones vers le bas. Sachant que vous ne pouvez ajouter qu’un seul objet à un **ScrollViewer**, il est judicieux d’ajouter un panneau de disposition tel qu’un **Grid** ou un **StackPanel**.

 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")

### <a name="View"></a> Viewbox
 Met à l'échelle les objets à la façon d'un contrôle de zoom. Vous ne pouvez ajouter qu’un seul objet à un **Viewbox**. Si vous voulez appliquer cet effet à plusieurs objets, ajoutez un panneau de disposition au **ViewBox**, puis ajoutez vos contrôles à ce panneau.

 (Disponible uniquement pour les projets WPF)

 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")

## <a name="see-also"></a>Voir aussi
 [Utilisation d’éléments dans Concepteur XAML](../designers/working-with-elements-in-xaml-designer.md) [la création d’une interface utilisateur à l’aide de concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
