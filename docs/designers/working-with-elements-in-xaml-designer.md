---
title: Working with elements in XAML Designer
ms.date: 05/14/2018
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: b8654c9a414549c4e1fee4515d359bfce4555df8
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823824"
---
# <a name="work-with-elements-in-xaml-designer"></a>Utiliser des éléments dans le concepteur XAML

Vous pouvez ajouter des éléments (contrôles, dispositions et formes) à votre application en XAML, en code ou en utilisant le concepteur XAML. Cette rubrique décrit comment utiliser des éléments dans le concepteur XAML dans Visual Studio ou Blend pour Visual Studio.

## <a name="add-an-element-to-a-layout"></a>Ajouter un élément à une disposition

La *disposition* est le processus de dimensionnement et de positionnement des éléments dans une interface utilisateur. Pour positionner des éléments visuels, vous devez les placer dans un élément [Panel](/uwp/api/Windows.UI.Xaml.Controls.Panel) de disposition. Un `Panel` a une propriété enfant qui est une collection de types [FrameworkElement](/uwp/api/Windows.UI.Xaml.FrameworkElement). Vous pouvez utiliser différents éléments enfants de `Panel`, tels que [Canvas](/uwp/api/Windows.UI.Xaml.Controls.Canvas), [StackPanel](/uwp/api/Windows.UI.Xaml.Controls.StackPanel) et [Grid](/uwp/api/Windows.UI.Xaml.Controls.Grid), pour servir de conteneurs de disposition, et positionner et organiser les éléments dans une page.

Par défaut, un panneau `Grid` est utilisé comme conteneur de disposition de niveau supérieur dans un formulaire ou une page. Vous pouvez ajouter des panneaux de disposition, des contrôles ou d'autres éléments dans la mise en page de niveau supérieur.

Pour ajouter un élément à une disposition dans le Concepteur XAML, effectuez l’une des opérations suivantes :

- Double-cliquez sur un élément dans la **Boîte à outils** (ou sélectionnez un élément dans la boîte à outils et appuyez sur **Entrée**).

- Faites glisser un élément depuis la **boîte à outils** vers la planche graphique.

- Dans la **boîte à outils**, sélectionnez l’un des outils de dessin (par exemple, [Ellipse](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) ou [Rectangle](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle)), puis dessinez un élément dans le panneau actif.

## <a name="change-the-layering-order-of-elements"></a>Changer l’ordre de superposition des éléments

Lorsque deux éléments de la planche graphique sont dans le concepteur XAML, un élément apparaît devant l'autre dans l'ordre de superposition. Sauf si la propriété **ZIndex** d’un élément est définie, l’élément au premier plan se trouve en bas de la liste des éléments dans la fenêtre Structure du document. Quand vous insérez un élément dans une page, un formulaire ou un conteneur de disposition, l'élément est automatiquement placé devant les autres éléments dans l'élément de conteneur actif. Pour modifier l’ordre des éléments, vous pouvez utiliser les commandes **Ordre** ou faire glisser les éléments dans l’arborescence d’objets de la fenêtre Structure du document.

Pour changer l’ordre de superposition, effectuez l’une des opérations suivantes :

- Dans la fenêtre **Structure du document**, faites glisser les éléments vers le haut ou le bas pour créer l’ordre de superposition souhaité.

- Dans la fenêtre Structure du document ou la planche graphique, cliquez avec le bouton droit sur l’élément pour lequel vous souhaitez modifier l’ordre de superposition, pointez sur **Ordre**, puis cliquez sur l’une des options suivantes :

  - **Mettre au premier plan** pour placer l’élément tout au début dans l’ordre.

  - **Avancer d’un plan** pour faire avancer l’élément d’un niveau dans l’ordre.

  - **Reculer d’un plan** pour faire reculer l’élément d’un niveau dans l’ordre.

  - **Mettre en arrière-plan** pour placer l’élément tout à la fin dans l’ordre.

  Modifiez la propriété **ZIndex** dans la section **Disposition** de la fenêtre Propriétés. Dans le cas des éléments qui se chevauchent, la propriété **ZIndex** est prioritaire sur l’ordre des éléments affiché dans la fenêtre Structure du document. Quand des éléments se chevauchent, l’élément qui possède une valeur **ZIndex** supérieure apparaît devant.

## <a name="change-the-alignment-of-an-element"></a>Changer l’alignement d’un élément

Vous pouvez aligner des éléments dans la planche graphique à l'aide de commandes de menu ou en faisant glisser les éléments vers des lignes d'alignement.

Une *ligne d’alignement* est un repère visuel qui vous aide à aligner un élément par rapport à d’autres éléments dans l’application.

Pour aligner deux éléments ou plus à l’aide des commandes de menu :

1. Sélectionnez les éléments que vous souhaitez aligner. Pour sélectionner plusieurs éléments, maintenez enfoncée la touche **Ctrl** et sélectionnez les éléments.

2. Sélectionnez l’une des propriétés suivantes sous **HorizontalAlignment** dans la section **Disposition** de la fenêtre Propriétés : **Gauche**, **Centre**, **Droite** ou **Étirer**.

3. Sélectionnez l’une des propriétés suivantes sous **VerticalAlignment** dans la section **Disposition** de la fenêtre Propriétés : **Haut**, **Centre**, **Bas** ou **Étirer**.

Pour aligner deux éléments ou plus à l’aide des lignes d’alignement, dans le Concepteur XAML, dans une disposition contenant au moins deux éléments, faites glisser ou redimensionnez l’un des éléments afin que le bord soit aligné sur un autre élément.

Quand les bords sont alignés, une *limite d’alignement* s’affiche pour indiquer l’alignement. La limite d'alignement est une ligne en pointillés rouge. Les limites d'alignement n'apparaissent que si l' **alignement sur les lignes d'alignement** est activé. Pour une illustration de la planche graphique montrant une limite d’alignement, consultez [Création d’une interface utilisateur à l’aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="change-an-elements-margins"></a>Changer les marges d’un élément

Dans le concepteur XAML, les marges déterminent la quantité d'espace vide autour d'un élément sur la planche graphique. Par exemple, les marges spécifient l'espace entre les bords extérieurs d'un élément et les limites d'un panneau `Grid` contenant cet élément. Les marges spécifient également la quantité d'espace entre les éléments contenus dans un `StackPanel`.

Pour changer les marges d’un élément dans la fenêtre Propriétés :

1. Sélectionnez l'élément pour lequel vous souhaitez modifier les marges.

2. Sous **Disposition** dans la fenêtre Propriétés, modifiez la valeur en pixels ou en dip (device independent pixel), qui représentent approximativement 1/96e de pouce, de toutes les propriétés **Marge** (**Haut**, **Gauche**, **Droite** ou **Bas**).

Dans la planche graphique, pour changer les marges d’un élément par rapport à son conteneur de disposition, cliquez sur les *ornements de marge* qui apparaissent autour de l’élément quand il est sélectionné et qu’il se trouve dans un conteneur de disposition. Pour une illustration des ornements de marge, consultez [Création d’une interface utilisateur à l’aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

Si un ornement de marge est ouvert, verticalement ou horizontalement, la marge n'est pas définie. Si un ornement de marge est fermé, cela signifie que la marge en question est définie.

Quand vous ouvrez un ornement de marge et que la marge opposée n'est pas définie, celle-ci se voit attribuer une valeur appropriée en fonction de l'emplacement de l'élément dans la planche graphique. Pour les marges opposées, telles que les marges **Gauche** et **Droite**, au moins une propriété est toujours définie.

> [!IMPORTANT]
> Les éléments placés à l'intérieur de certains conteneurs de disposition (par exemple, un <xref:Windows.UI.Xaml.Controls.Canvas>) n'ont pas d'ornements de marge. Les éléments placés dans un <xref:Windows.UI.Xaml.Controls.StackPanel> ont des ornements de marge pour les marges de gauche et de droite ou les marges supérieure et inférieure, en fonction de l'orientation du `StackPanel`.

## <a name="group-and-ungroup-elements"></a>Regrouper et dissocier des éléments

Le regroupement de plusieurs éléments dans le concepteur XAML crée un conteneur de disposition et place ces éléments dans le conteneur. Le fait de regrouper des éléments dans un conteneur de disposition permet de faciliter la sélection, le déplacement et la transformation du groupe, comme si les éléments de ce groupe ne constituaient qu'un seul élément. Le regroupement est également utile pour l'identification d'éléments liés les uns aux autres d'une certaine façon, tels que les boutons qui composent un élément de navigation. Lorsque vous dissociez des éléments, vous supprimez simplement le conteneur de disposition contenant ceux-ci.

Pour regrouper des éléments dans un nouveau conteneur de disposition :

1. Sélectionnez les éléments que vous souhaitez regrouper. (Pour sélectionner plusieurs éléments, maintenez enfoncée la touche **Ctrl** et cliquez sur les éléments.)

2. Cliquez avec le bouton droit sur les éléments sélectionnés, pointez sur **Grouper**, puis cliquez sur le type de conteneur de disposition dans lequel vous souhaitez que le groupe réside.

    > [!TIP]
    > Si vous sélectionnez <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> ou <xref:Windows.UI.Xaml.Controls.ScrollViewer> pour regrouper vos éléments, les éléments sont placés dans un nouveau panneau <xref:Windows.UI.Xaml.Controls.Grid> dans le <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> ou <xref:Windows.UI.Xaml.Controls.ScrollViewer>. Si vous dissociez des éléments dans l'un de ces conteneurs de disposition, seul le panneau <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> ou <xref:Windows.UI.Xaml.Controls.ScrollViewer> est supprimé. Le panneau <xref:Windows.UI.Xaml.Controls.Grid> est conservé. Pour supprimer le panneau `Grid`, redissociez les éléments.

Pour dissocier des éléments et supprimer la disposition, cliquez avec le bouton droit sur le groupe à dissocier, puis cliquez sur **Dissocier**. Vous pouvez également regrouper ou dissocier des éléments en cliquant avec le bouton droit sur les éléments concernés dans la fenêtre Structure du document, puis en cliquant sur **Grouper** ou **Dissocier**.

## <a name="reset-the-element-layout"></a>Réinitialiser la disposition des éléments

Vous pouvez restaurer les valeurs par défaut de propriétés de disposition spécifiques d'un élément à l'aide des commandes de réinitialisation de la disposition. Cette commande vous permet de réinitialiser la marge, l'alignement, la largeur, la hauteur et la taille d'un élément, de manière individuelle ou collective.

Pour réinitialiser la disposition des éléments, cliquez avec le bouton droit sur l’élément souhaité dans la fenêtre Structure du document ou dans la planche graphique, puis choisissez **Disposition** > **Réinitialiser** *nom_propriété*, où *nom_propriété* représente la propriété à réinitialiser (ou choisissez **Disposition** > **Tout réinitialiser** pour réinitialiser toutes les propriétés de disposition de l’élément).

## <a name="see-also"></a>Voir aussi

- [Créer une IU à l’aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
