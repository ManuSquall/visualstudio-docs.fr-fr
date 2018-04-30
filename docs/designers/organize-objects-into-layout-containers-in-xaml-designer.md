---
title: Organiser les objets en conteneurs de disposition dans le concepteur XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 2da34d180a59212b171e484129df27d94f580a1a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organiser les objets en conteneurs de disposition dans le concepteur XAML

Cet article décrit les panneaux de disposition et les contrôles du concepteur XAML.

Réfléchissez à l’endroit où vous souhaitez faire figurer les objets dans une page (des objets tels que des images, des boutons et des vidéos). Peut-être souhaiterez-vous qu'ils apparaissent dans des lignes et des colonnes, dans une seule ligne verticale ou horizontale ou bien à des emplacements fixes ?

Une fois que vous avez déterminé l’aspect que vous voulez donner à la page, choisissez un panneau de disposition. Il s'agit de la structure de base de toutes les pages à laquelle vous allez ajouter vos objets. Par défaut, il s’agit d’une **grille**, mais vous pouvez changer cela.

Si les panneaux de disposition permettent de disposer les objets dans une page, leur fonction ne s'arrête pas là. Ils vous permettent de concevoir pour différentes tailles et résolutions d'écran. Quand les utilisateurs exécutent votre application, tout ce qui figure dans le panneau de disposition est redimensionné pour s'adapter à la taille d'écran de leur appareil. Bien entendu, vous pouvez éviter cela en changeant tout ou partie du comportement de la disposition. Pour ce faire, vous pouvez utiliser les propriétés de hauteur et de largeur.

## <a name="layout-panels"></a>Panneaux de disposition

Commencez votre page en choisissant l'un de ces panneaux de disposition. Votre page peut en contenir plusieurs. Par exemple, vous pouvez commencer par un panneau de disposition **Grid** et ajouter à une zone de ce dernier un **StackPanel** pour disposer les contrôles à la verticale dans cet élément **Grid**.

Les panneaux de disposition suivants sont les plus couramment utilisés, mais il en existe d'autres. Vous les trouverez tous dans le panneau **Composants**.

- [Grid](#Grid)

- [UniformGrid](#UniformGrid)

- [Canvas](#Canvas)

- [StackPanel](#stackpanel)

- [WrapPanel](#wrappanel)

- [DockPanel](#dockpanel)

### <a name="grid"></a>Grille

Permet de disposer les objets dans des lignes et des colonnes.

![Panneau de disposition de grille](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>UniformGrid

Permet de disposer les objets dans des régions de grille égales ou uniformes. Ce panneau est très pratique pour organiser une liste d'images.

![Panneau de disposition UniformGrid](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

(Disponible seulement pour les projets WPF)

### <a name="canvas"></a>Canvas

Permet de disposer les objets librement. Quand les utilisateurs exécutent votre application, ces éléments ont des positions fixes sur l'écran.

![Panneau de disposition de canevas](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

Permet de disposer les objets dans une seule ligne horizontale ou verticale.

![Panneau de disposition StackPanel](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

Permet de disposer les objets les uns à la suite des autres, de gauche à droite. Quand il n’y a plus de place à l’extrémité droite du panneau, il *renvoie* le contenu à la ligne suivante, et ainsi de suite de gauche à droite et de haut en bas. Vous pouvez aussi disposer un panneau de renvoi à la ligne à la verticale de sorte que les objets se suivent de haut en bas et de gauche à droite.

(Disponible seulement pour les projets WPF)

![Panneau de disposition WrapPanel](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

Permet de disposer les objets de telle sorte qu’il restent, ou s’*ancrent*, sur un bord du panneau.

(Disponible seulement pour les projets WPF)

![Panneau de disposition DockPanel](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**Regarder une courte vidéo :** ![Bouton Lecture](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo).

## <a name="layout-controls"></a>Contrôles de disposition

Vous pouvez aussi ajouter vos objets à des contrôles de disposition. Ils n’offrent pas autant de fonctionnalités qu’un panneau de disposition, mais ils peuvent s’avérer utiles pour certains scénarios.

Les contrôles de disposition suivants sont les plus couramment utilisés, mais il en existe d’autres. Vous les trouverez tous dans le panneau **Composants**.

- [Border](#Border)

- [Popup](#Popup)

- [ScrollViewer](#scrollviewer)

- [Viewbox](#viewbox)

### <a name="border"></a>Bordure

Permet de créer une bordure, un arrière-plan ou les deux autour d'un objet. Vous ne pouvez ajouter qu’un seul objet à un **Border**. Si vous voulez appliquer une bordure ou un arrière-plan à plusieurs objets, ajoutez un panneau de disposition au **Border**. Ajoutez ensuite les objets à ce panneau ou contrôle.

![Contrôle de disposition de bordure](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>Fenêtre contextuelle

Permet d'afficher des informations ou des options à l'intention des utilisateurs dans une fenêtre. Vous ne pouvez ajouter qu’un seul objet à un **Popup**. Par défaut, un **Popup** contient un **Grid**, mais vous disposez d’autres options.

### <a name="scrollviewer"></a>Visionneuse de défilement

Permet aux utilisateurs de faire défiler une page ou une de ses zones vers le bas. Sachant que vous ne pouvez ajouter qu’un seul objet à un **ScrollViewer**, il est judicieux d’ajouter un panneau de disposition tel qu’un **Grid** ou un **StackPanel**.

![Contrôle de disposition ScrollViewer](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Viewbox

Met à l'échelle les objets à la façon d'un contrôle de zoom. Vous ne pouvez ajouter qu’un seul objet à un **Viewbox**. Si vous voulez appliquer cet effet à plusieurs objets, ajoutez un panneau de disposition au **ViewBox**, puis ajoutez vos contrôles à ce panneau.

(Disponible seulement pour les projets WPF)

![Contrôle de disposition ViewBox](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>Voir aussi

- [Travailler avec des éléments dans le concepteur XAML](../designers/working-with-elements-in-xaml-designer.md)
- [Créer une IU à l’aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)