---
title: Visite guidée de Visual Studio pour Mac
description: Visual Studio pour Mac fournit un environnement de développement intégré pour créer des applications .NET sur macOS, notamment des sites web ASP.NET Core, ainsi que des projets Xamarin pour iOS, Android, Mac et Xamarin.Forms.
author: conceptdev
ms.author: crdun
ms.date: 02/07/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: 0ab7293a7b7d956778d1dbab568d609e6bf3d644
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857255"
---
# <a name="visual-studio-2017-for-mac-tour"></a>Visite guidée de Visual Studio 2017 pour Mac

> [!NOTE]
> Visual Studio 2019 pour Mac est [désormais disponible](installation.md).

Visual Studio pour Mac est un _environnement de développement intégré_ .NET sur Mac qui permet de modifier, déboguer et générer du code, puis de publier une application. En plus des fonctionnalités attendues, comme l’éditeur et le débogueur standard, Visual Studio pour Mac comporte des compilateurs, des outils de complétion de code, des concepteurs graphiques et le contrôle de code source pour faciliter le développement de logiciels.

Visual Studio pour Mac prend en charge pratiquement les mêmes types de fichiers que son équivalent Windows, comme les fichiers `.csproj`, `.fsproj` ou `.sln`, ainsi que les fonctionnalités comme EditorConfig, ce qui signifie que vous pouvez utiliser l’IDE qui vous convient le mieux.
La création, l’ouverture et le développement d’une application sont autant d’expériences familières pour toute personne ayant déjà utilisé Visual Studio sur Windows. De plus, Visual Studio pour Mac utilise un grand nombre des outils puissants qui font de son équivalent Windows un IDE aussi avancé. La plateforme de compilateurs Roslyn est utilisée pour la refactorisation et pour IntelliSense. Son système de projets et son moteur de génération utilisent MSBuild, tandis que son éditeur de code source prend en charge les bundles TextMate. Il utilise les mêmes moteurs de débogage pour les applications Xamarin et .NET Core, et les mêmes concepteurs pour Xamarin.iOS et Xamarin.Android.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Ce que je peux faire dans Visual Studio pour Mac

Visual Studio pour Mac prend en charge les types de développement suivants :

- Applications web ASP.NET Core avec C#, F#, et prise en charge des pages Razor, de JavaScript et de TypeScript
- Application console .NET Core avec C# ou F#
- Applications et jeux Unity multiplateformes avec C#
- Applications Android, iOS, tvOS et watchOS dans Xamarin avec C# ou F# et XAML
- Applications de bureau Cocoa en C# ou F#

Cet article explore les différentes sections de Visual Studio pour Mac, en présentant certaines des fonctionnalités qui en font un outil puissant pour créer ces applications.

## <a name="ide-tour"></a>Visite guidée de l’IDE

Visual Studio pour Mac est organisé en plusieurs sections permettant de gérer les fichiers et les paramètres d’une application, de créer le code de l’application et de déboguer.

## <a name="welcome-screen"></a>Écran d'accueil

Une fois lancé, Visual Studio pour Mac affiche un *écran d’accueil* :

![Écran d'accueil](media/ide-tour-image1.png)

L’écran d’accueil comprend les sections suivantes :

- **Barre d’outils** : permet d’accéder rapidement à la barre de recherche. Quand une solution est chargée, la barre d’outils est utilisée pour la définition des configurations d’application, le débogage et l’affichage des erreurs.
- **Mise en route** : permet d’accéder rapidement à des rubriques utiles pour les développeurs qui commencent à utiliser Visual Studio pour Mac.
- **Solutions récentes** : permet d’accéder rapidement aux solutions récemment ouvertes et à des boutons pratiques pour ouvrir ou créer des projets.
- **Informations pour les développeurs** : flux RSS qui vous permet de découvrir les informations les plus récentes de Microsoft Developer.

## <a name="solutions-and-projects"></a>Projets et solutions

L’image ci-dessous montre Visual Studio pour Mac avec une application chargée :

![Visual Studio pour Mac avec une application chargée](media/ide-tour-image17.png)

Les sections suivantes fournissent une vue d’ensemble des zones principales de Visual Studio pour Mac.

## <a name="solution-pad"></a>Panneau Solution

Le panneau Solution organise le ou les projets dans une solution :

![Projets organisés dans le panneau Solution](media/ide-tour-image18.png)

C’est ici que le code source, les ressources, l’interface utilisateur et les dépendances sont organisés en projets spécifiques à une plateforme.

Pour plus d’informations sur l’utilisation de projets et de solutions dans Visual Studio pour Mac, consultez l’article [Projets et solutions](/visualstudio/mac/projects-and-solutions).

## <a name="assembly-references"></a>Références d'assembly

Les références d’assemblys pour chaque projet sont disponibles dans le dossier Références :

![Dossier Références dans le panneau Solution](media/ide-tour-image19.png)

Vous ajoutez des références en utilisant la boîte de dialogue **Modifier les références**, que vous pouvez afficher en double-cliquant sur le dossier Références ou en sélectionnant **Modifier les références** dans les actions de son menu contextuel :

![Boîte de dialogue Modifier les références](media/ide-tour-image20.png)

Pour plus d’informations sur l’utilisation de références dans Visual Studio pour Mac, consultez l’article [Gestion des références dans un projet](/visualstudio/mac/managing-references-in-a-project).

## <a name="dependencies--packages"></a>Dépendances / Packages

Toutes les dépendances externes utilisées dans votre application sont stockées dans le dossier Dépendances ou Packages, selon que vous êtes dans un projet .NET Core ou Xamarin.iOS/Xamarin.Android. Ces éléments sont généralement fournis sous la forme d’un package NuGet.

NuGet est le gestionnaire de packages le plus répandu pour le développement .NET. Grâce à la prise en charge de NuGet par Visual Studio, vous pouvez facilement rechercher et ajouter des packages à votre projet d’application.

Pour ajouter une dépendance à votre application, cliquez avec le bouton droit sur le dossier Dépendances / Packages, puis sélectionnez **Ajouter des packages** :

![Ajouter un package NuGet](media/ide-tour-image21.png)

Vous trouverez des informations sur l’utilisation d’un package NuGet dans une application dans l’article [Inclusion d’un projet NuGet dans votre projet](/visualstudio/mac/nuget-walkthrough).

## <a name="refactoring"></a>Refactorisation

Visual Studio pour Mac offre deux méthodes pratiques de refactorisation du code : les actions contextuelles et l’analyse du code source. Pour plus d’informations sur ces méthodes, consultez l’article [Refactorisation](/visualstudio/mac/refactoring).

## <a name="debugging"></a>Débogage

Visual Studio pour Mac a un débogueur natif qui prend en charge le débogage des applications Xamarin.iOS, Xamarin.Mac et Xamarin.Android. Visual Studio pour Mac utilise le débogueur Mono Soft, qui est implémenté dans le runtime Mono, ce qui permet à l’IDE de déboguer du code managé sur toutes les plateformes. Pour plus d’informations sur le débogage, consultez l’article [Débogage](/visualstudio/mac/debugging).

Le débogueur contient des visualiseurs puissants pour les types spéciaux, comme les chaînes, les couleurs, les URL, ainsi que les tailles, les coordonnées et les courbes de Bézier.

Pour plus d’informations sur les visualisations des données du débogueur, consultez l’article [Visualisations des données](/visualstudio/mac/data-visualizations).

## <a name="version-control"></a>Gestion de version

Visual Studio pour Mac s’intègre aux systèmes de contrôle du code source Git et Subversion. Les projets soumis au contrôle du code source sont signalés par la branche figurant en regard du nom de la solution :

![Nom de la branche pour indiquer un projet soumis au contrôle du code source](media/ide-tour-image22.png)

Les fichiers comportant des modifications non validées sont indiqués par une annotation sur leur icône dans le Panneau Solution, comme l’illustre l’image suivante :

![Fichiers non validés dans le panneau Solution](media/ide-tour-image23.png)

Pour plus d’informations sur l’utilisation de la gestion de versions dans Visual Studio, consultez l’article [Gestion de versions](/visualstudio/mac/version-control).

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]


## <a name="see-also"></a>Voir aussi

- [IDE Visual Studio (sur Windows)](/visualstudio/ide/visual-studio-ide)
