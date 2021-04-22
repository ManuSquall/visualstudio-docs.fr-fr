---
title: Vue d’ensemble du concepteur XAML
description: En savoir plus sur l’interface utilisateur de l’espace de travail et les fonctionnalités du Concepteur XAML dans Blend pour Visual Studio qui fournit une interface visuelle pour vous aider à concevoir des applications basées sur XAML.
ms.date: 03/03/2020
ms.topic: conceptual
ms.custom: contperf-fy21q4; SEO-VS-2020
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.DocumentOutline
- Blend.Start.Dev12
ms.devlang: CSharp
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 3d5584380b78bba05f1596a99aa2298789df018f
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879354"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>Créer une IU à l’aide du concepteur XAML

Le Concepteur XAML dans Visual Studio et Blend pour Visual Studio fournit une interface visuelle pour vous aider à concevoir des applications basées sur XAML, telles que WPF et UWP. Vous pouvez créer des interfaces utilisateur pour vos applications en faisant glisser des contrôles à partir de la fenêtre Boîte à outils (ou de la fenêtre Composants dans Blend pour Visual Studio), et en définissant des propriétés dans la fenêtre Propriétés. Vous pouvez également modifier le XAML directement en mode XAML.

Les utilisateurs expérimentés peuvent même [personnaliser le concepteur XAML](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md).

> [!NOTE]
> Xamarin. Forms ne prend pas en charge un concepteur XAML. Pour afficher vos interfaces utilisateur XAML Xamarin. Forms et les modifier pendant que l’application est en cours d’exécution, utilisez le rechargement à chaud XAML pour Xamarin. Forms. Pour plus d’informations, consultez la page [chargement à chaud XAML pour Xamarin. Forms (version préliminaire)](/xamarin/xamarin-forms/xaml/hot-reload/) .

## <a name="xaml-designer-workspace"></a>Espace de travail du concepteur XML

L'espace de travail du concepteur XML se compose de plusieurs éléments d'interface graphique. Ceux-ci incluent la *planche graphique* (c’est-à-dire, l’aire de conception visuelle), l’éditeur XAML, la fenêtre Structure du document (ou la fenêtre Objets et chronologie dans Blend pour Visual Studio), ainsi que la fenêtre Propriétés. Pour ouvrir le concepteur XAML, cliquez avec le bouton droit sur un fichier XAML dans l' **Explorateur de solutions** et choisissez **Concepteur de vues**.

Le concepteur XAML fournit un mode XAML et un mode Création synchronisé du balisage XAML rendu de votre application. Quand un fichier XAML est ouvert dans Visual Studio ou dans Blend pour Visual Studio, vous pouvez basculer entre le mode Création et le mode XAML à l’aide des onglets **Conception** et **XAML**. Vous pouvez utiliser le bouton **Permuter les volets**![bouton Permuter les volets dans le concepteur XAML](media/swap-panes.PNG) pour définir la fenêtre qui doit s’afficher au premier plan : la planche graphique ou l’éditeur XAML.

### <a name="design-view"></a>Mode création

En mode Création, la fenêtre qui contient la planche graphique est la fenêtre active, et vous pouvez l’utiliser comme surface de travail principale. Vous pouvez l’utiliser pour concevoir visuellement une page dans votre application en ajoutant, en dessinant ou en modifiant des éléments. Pour plus d’informations, consultez [Utiliser des éléments dans le concepteur XAML](../xaml-tools/working-with-elements-in-xaml-designer.md). Cette illustration montre la planche graphique en mode Création.

![Mode Design du concepteur XAML](media/xaml-artboard.png)

Les fonctionnalités suivantes sont disponibles dans la planche graphique :

**Lignes d'alignement**

Les lignes d’alignement sont des *limites d’alignement* qui s’affichent sous la forme de lignes en pointillés rouges, lorsque les bords des contrôles sont alignés ou que les lignes de base de texte sont alignées. Les limites d'alignement n'apparaissent que si l' **alignement sur les lignes d'alignement** est activé.

**Quadrillage de grille**

Les quadrillages permettent de gérer les lignes et les colonnes d’un panneau [grille](xref:Windows.UI.Xaml.Controls.Grid). Vous pouvez créer et supprimer des lignes et des colonnes, ainsi qu'ajuster leurs largeurs et hauteurs relatives. Le quadrillage de grille vertical, qui apparaît à gauche de la planche graphique, est utilisé pour les lignes, et la ligne horizontale, qui apparaît en haut, est utilisée pour les colonnes.

**Ornements de grille**

Un ornement de grille apparaît sous la forme d’un triangle auquel est rattachée une ligne verticale ou horizontale sur le quadrillage. Quand vous faites glisser un ornement de grille, les largeurs ou hauteurs des lignes ou colonnes adjacentes se mettent à jour au fur et à mesure que vous déplacez la souris.

Les ornements de grille permettent de contrôler la largeur et la hauteur des lignes et des colonnes d’une grille. Vous pouvez ajouter une nouvelle colonne ou ligne en cliquant sur le quadrillage. Quand vous ajoutez une nouvelle ligne ou ligne de colonne pour un panneau Grille qui comporte plusieurs colonnes ou lignes, une mini-barre d’outils apparaît en dehors du quadrillage pour vous permettre de définir la largeur et la hauteur explicitement. La mini-barre d’outils vous permet de définir des options de dimensionnement pour les lignes et les colonnes de grille.

![Ornement de grille dans le concepteur XAML](media/grid-adorner.png)

**Poignées de redimensionnement**

Des poignées de redimensionnement apparaissent sur les contrôles sélectionnés et vous permettent de redimensionner le contrôle. Quand vous redimensionnez un contrôle, les valeurs de largeur et de hauteur s'affichent généralement pour permettre de déterminer la taille du contrôle. Pour plus d’informations sur la manipulation des contrôles en mode **Création**, consultez [Utiliser des éléments dans le concepteur XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

**Marges**

Les marges représentent la quantité d'espace fixe entre le bord d'un contrôle et le bord du conteneur associé. Vous pouvez définir les marges d’un contrôle à l’aide des propriétés [Margin](xref:Windows.UI.Xaml.FrameworkElement.Margin) sous **Disposition** dans la fenêtre **Propriétés**.

**Ornements de marge**

Utilisez des ornements de marge pour modifier les marges d’un élément par rapport à son conteneur de disposition. Quand un ornement de marge est ouvert, une marge n'est pas définie et l'ornement de marge affiche une chaîne interrompue. Quand la marge n’est pas définie et que le conteneur de disposition est redimensionné au moment de l’exécution, les éléments restent en place. Quand un ornement de marge est fermé, un ornement de marge affiche une chaîne ininterrompue, et les éléments se déplacent avec la marge au fur et à mesure que le conteneur de disposition est redimensionné au moment de l’exécution (la marge reste fixe).

**Poignées d'élément**

Vous pouvez modifier un élément à l'aide des poignées d'élément qui apparaissent sur la planche graphique quand vous déplacez le pointeur sur les angles de la zone bleue qui entoure un élément. Ces poignées permettent de faire pivoter un élément, de le redimensionner, retourner, déplacer ou d'y ajouter un rayon d'angle. Le symbole d’une poignée d’élément varie selon les fonctions et selon l’emplacement exact du pointeur. Si les poignées d'élément ne s'affichent pas, vérifiez que l'élément est sélectionné.

En mode **Création**, des commandes supplémentaires de la planche graphique sont disponibles dans la partie inférieure gauche de la fenêtre, comme indiqué ci-après :

![Commandes du mode Design](media/xaml-design-view-controls.png)

Les commandes suivantes sont disponibles dans cette barre d'outils :

**Zoom**

Le zoom vous permet de dimensionner l'aire de conception. Vous pouvez effectuer un zoom de 12,5% à 800 %, ou sélectionner des options comme **Ajuster la sélection** ou **Ajuster tout**.

**Afficher/Masquer la grille d'accrochage**

Affiche ou masque la grille d'accrochage qui indique le quadrillage. Le quadrillage est utilisé quand vous activez l’**alignement sur le quadrillage** ou l’**alignement sur les lignes d’alignement**.

**Activer/Désactiver l'alignement sur le quadrillage**

Si l' **alignement sur le quadrillage** est activé, un élément tend à s’aligner sur les lignes de quadrillage horizontales et verticales les plus proches quand vous le faites glisser sur la planche graphique.

**Activer/Désactiver l’arrière-plan de la planche graphique**

Permet de basculer entre un arrière-plan clair et un arrière-plan sombre.

**Activer/Désactiver l'alignement sur les lignes d'alignement**

Les lignes d'alignement vous aident à aligner les contrôles les uns par rapport aux autres. Si l' **alignement sur les lignes d'alignement** est activé, quand vous faites glisser un contrôle par rapport à d'autres contrôles, des limites d'alignement apparaissent quand les bords et le texte de certains contrôles sont alignés horizontalement ou verticalement. Une limite d'alignement apparaît sous la forme d'une ligne en pointillés rouge.

**Désactiver le code de projet**

Désactive le [code de projet](debugging-or-disabling-project-code-in-xaml-designer.md) (par exemple, les contrôles personnalisés ou les convertisseurs de valeurs), puis recharge le concepteur.

### <a name="xaml-view"></a>Mode XAML

En mode **XAML**, la fenêtre de l’éditeur XAML est la fenêtre active, et l’éditeur XAML est votre principal outil de création. Le langage XAML (Extensible Application Markup Language) fournit un vocabulaire XML déclaratif permettant de spécifier l'interface utilisateur d'une application. Le mode XAML inclut IntelliSense, la mise en forme automatique, la mise en surbrillance de la syntaxe et la navigation de balises. L’image suivante montre le mode XAML avec le menu IntelliSense ouvert :

![Mode XAML](media/xaml-editor.png)

## <a name="document-outline-window"></a>Fenêtre Structure du document

Dans Visual Studio, la fenêtre Structure du document est similaire à la fenêtre [Objets et chronologie](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) de Blend pour Visual Studio. La fenêtre Structure du document vous permet d’effectuer les tâches suivantes :

- Afficher la structure hiérarchique de tous les éléments de la planche graphique.

- Sélectionnez les éléments afin de pouvoir les modifier. Par exemple, vous pouvez les déplacer dans la hiérarchie ou définir leurs propriétés dans la Fenêtre Propriétés. Pour plus d’informations, consultez [Utiliser des éléments dans le concepteur XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Créer et modifier les modèles des éléments qui sont des contrôles.

- [Créer des animations](animate-objects-in-xaml-designer.md) (Blend pour Visual Studio uniquement).

Pour afficher la fenêtre structure du document dans Visual Studio, dans la barre de menus, sélectionnez **Afficher** le plan du  >    >  **document** Windows.
Pour afficher la fenêtre de objets et chronologie dans Blend pour Visual Studio, dans la barre de menus, sélectionnez **Afficher** la  >  **structure du document**.

![Fenêtre Structure du document dans Visual Studio](media/document-outline-window.png)

Dans la fenêtre Structure du document/Objets et chronologie, la vue principale montre le niveau hiérarchique d’un document dans une arborescence. Vous pouvez utiliser la nature hiérarchique de la structure du document pour consulter le document à des niveaux de détail différents, ainsi que pour verrouiller et masquer des éléments séparément ou par groupes. Les options suivantes sont disponibles dans la fenêtre structure du document/Objets et chronologie :

**Afficher/Masquer**

Affiche ou masque les éléments de la planche graphique. Un symbole représentant un œil s’affiche lorsque l’option est activée. Vous pouvez également appuyer sur **CTRL** + **h** pour masquer un élément et **MAJ** + **CTRL** + **h** pour l’afficher.

**Verrouiller/Déverrouiller**

Verrouille ou déverrouille les éléments de la planche graphique. Les éléments verrouillés ne peuvent pas être modifiés. Un symbole de cadenas s’affiche lorsque les éléments sont verrouillés. Vous pouvez également appuyer sur **CTRL** + **l** pour verrouiller un élément et **déplacer** + **CTRL** + **l** pour le déverrouiller.

**Rétablir l'étendue à pageRoot**

L’option en haut de la fenêtre Structure du document/Objets et chronologie, qui est représentée par un symbole de flèche vers le haut, permet de passer à la portée précédente. La portée supérieure n'est applicable que quand vous êtes dans la portée d'un style ou d'un modèle.

## <a name="properties-window"></a>Fenêtre Propriétés

La fenêtre **Propriétés** vous permet de définir des valeurs de propriété sur les contrôles. Voici à quoi il ressemble :

![Fenêtre Propriétés](media/xaml-designer-properties-window.png)

Plusieurs options apparaissent en haut de la fenêtre **Propriétés** :

- Modifiez le nom de l’élément actuellement sélectionné dans la zone **Nom**.
- Dans le coin supérieur gauche, il existe une icône qui représente l'élément actuellement sélectionné.
- Pour réorganiser les propriétés par catégorie ou par ordre alphabétique, cliquez sur **Catégorie**, **Nom** ou **Source** dans la liste **Réorganiser par** .
- Pour afficher la liste des événements d’un contrôle, cliquez sur le bouton **Événements**, qui est représenté par un éclair.
- Pour rechercher une propriété, commencez à taper son nom dans la zone de recherche. La fenêtre **Propriétés** affiche les propriétés correspondant aux termes de recherche en cours de frappe.

Certaines propriétés vous permettent de définir des propriétés avancées en sélectionnant un bouton de flèche vers le bas.

À droite de chaque valeur de propriété figure un *marqueur de propriété* qui apparaît comme un symbole de zone. L'apparence du marqueur de propriété indique s'il y a une liaison de données ou une ressource appliquée à la propriété. Par exemple, un symbole de zone vide indique une valeur par défaut, un symbole de zone noire indique généralement qu'une ressource locale a été appliquée, et enfin une zone orange indique généralement qu'une liaison de données a été appliquée. Quand vous cliquez sur le marqueur de propriété, vous pouvez accéder à la définition d'un style, ouvrir le générateur de liaisons de données ou ouvrir le sélecteur de ressources.

Pour plus d’informations sur l’utilisation des propriétés et la gestion des événements, consultez [Présentation des contrôles et des modèles](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Voir aussi

- [Travailler avec des éléments dans le concepteur XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Guide pratique pour créer et appliquer une ressource](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [Procédure pas à pas : effectuer une liaison de données dans le Concepteur XAML](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
