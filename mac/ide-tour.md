---
title: Visite guidée de Visual Studio pour Mac
description: Visual Studio pour Mac fournit un environnement de développement intégré pour créer des applications .NET sur macOS, notamment des sites web ASP.NET Core, ainsi que des projets Xamarin pour iOS, Android, Mac et Xamarin.Forms.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/13/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: f7686efae903912b64d8692a823d6e82592cbec9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405820"
---
# <a name="visual-studio-2019-for-mac-tour"></a>Visite guidée de Visual Studio 2019 pour Mac

Visual Studio pour Mac est un _environnement de développement intégré_ .NET sur Mac qui permet de modifier, déboguer et générer du code, puis de publier une application. En plus des fonctionnalités attendues, comme l’éditeur et le débogueur standard, Visual Studio pour Mac comporte des compilateurs, des outils de saisie semi-automatique du code, des concepteurs graphiques et le contrôle de code source pour faciliter le développement de logiciels.

Visual Studio pour Mac prend en charge pratiquement les mêmes types de fichiers que son équivalent Windows, comme les fichiers `.csproj`, `.fsproj` ou `.sln`, ainsi que les fonctionnalités comme EditorConfig, ce qui signifie que vous pouvez utiliser l’IDE qui vous convient le mieux.
La création, l’ouverture et le développement d’une application sont autant d’expériences familières pour toute personne ayant déjà utilisé Visual Studio sur Windows. De plus, Visual Studio pour Mac utilise un grand nombre des outils puissants qui font de son équivalent Windows un IDE aussi avancé. La plateforme de compilateurs Roslyn est utilisée pour la refactorisation et pour IntelliSense. Son système de projet et moteur de construction utilisent MSBuild, et son éditeur source utilise la même base que Visual Studio sur Windows. Il utilise les mêmes moteurs de débogage pour les applications Xamarin et .NET Core, et les mêmes concepteurs pour Xamarin.iOS et Xamarin.Android.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Ce que je peux faire dans Visual Studio pour Mac

Visual Studio pour Mac prend en charge les types de développement suivants :

- ASP.NET applications Web de base avec C, F et prise en charge pour les pages Razor, JavaScript et TypeScript
- Application console .NET Core avec C# ou F#
- Applications et jeux Unity multiplateformes avec C#
- Applications Android, iOS, tvOS et watchOS dans Xamarin avec C# ou F# et XAML
- Applications de bureau Cocoa en C# ou F#

Cet article explore les différentes sections de Visual Studio pour Mac, en présentant certaines des fonctionnalités qui en font un outil puissant pour créer ces applications.

## <a name="ide-tour"></a>Visite guidée de l’environnement IDE

Visual Studio pour Mac est organisé en plusieurs sections permettant de gérer les fichiers et les paramètres d’une application, de créer le code de l’application et de déboguer.

## <a name="getting-started"></a>Prise en main

Si vous utilisez pour la première fois Visual Studio 2019 pour Mac, une fenêtre de connexion s’affiche. Connectez-vous avec votre compte Microsoft pour activer une licence payante (si vous en avez une) ou établir une liaison à un abonnement Azure. Vous pouvez appuyer sur je vais le faire plus tard et vous connecter plus tard via le **Studio visuel > Signez dans** **l’élément** de menu:

![Connexion à votre compte Microsoft](media/ide-tour-2019-start-signin.png)

Vous aurez alors la possibilité de personnaliser l’IDE en sélectionnant vos raccourcis clavier préférés : Visual Studio pour Mac, Visual Studio, Visual Studio, Visual Studio Code ou Xcode :

![Sélectionnez vos raccourcis clavier préférés](media/ide-tour-2019-keyboard-shortcut.png)

Les utilisateurs connectés accèdent à la nouvelle _fenêtre de démarrage_. Celle-ci affiche la liste des projets récents et contient des boutons permettant d’ouvrir un projet existant ou d’en créer un :

![Choisir un projet récent ou en créer un](media/ide-tour-2019-start-projects.png)

## <a name="solutions-and-projects"></a>Solutions et projets

L’image ci-dessous montre Visual Studio pour Mac avec une application chargée :

![Visual Studio pour Mac avec une application chargée](media/ide-tour-image17.png)

Les sections suivantes fournissent une vue d’ensemble des zones principales de Visual Studio pour Mac.

## <a name="solution-pad"></a>Panneau Solutions

Le panneau Solution organise le ou les projets dans une solution :

![Projets organisés dans le panneau Solution](media/ide-tour-image18.png)

C’est ici que le code source, les ressources, l’interface utilisateur et les dépendances sont organisés en projets spécifiques à une plateforme.

Pour plus d’informations sur l’utilisation de projets et de solutions dans Visual Studio pour Mac, consultez l’article [Projets et solutions](/visualstudio/mac/projects-and-solutions).

## <a name="assembly-references"></a>Références d’assembly

Les références d’assemblys pour chaque projet sont disponibles dans le dossier Références :

![Dossier Références dans le panneau Solution](media/ide-tour-image19.png)

Vous ajoutez des références en utilisant la boîte de dialogue **Modifier les références**, que vous pouvez afficher en double-cliquant sur le dossier Références ou en sélectionnant **Modifier les références** dans les actions de son menu contextuel :

![Boîte de dialogue Modifier les références](media/ide-tour-image20.png)

Pour plus d’informations sur l’utilisation de références dans Visual Studio pour Mac, consultez l’article [Gestion des références dans un projet](/visualstudio/mac/managing-references-in-a-project).

## <a name="dependencies--packages"></a>Dépendances/packages

Toutes les dépendances externes utilisées dans votre application sont stockées dans le dossier Dépendances ou Packages, selon que vous êtes dans un projet .NET Core ou Xamarin.iOS/Xamarin.Android. Ces éléments sont généralement fournis sous la forme d’un package NuGet.

NuGet est le gestionnaire de packages le plus répandu pour le développement .NET. Grâce à la prise en charge de NuGet par Visual Studio, vous pouvez facilement rechercher et ajouter des packages à votre projet d’application.

Pour ajouter une dépendance à votre application, cliquez avec le bouton droit sur le dossier Dépendances / Packages, puis sélectionnez **Ajouter des packages** :

![Ajouter un package NuGet](media/ide-tour-image21.png)

Vous trouverez des informations sur l’utilisation d’un package NuGet dans une application dans l’article [Inclusion d’un projet NuGet dans votre projet](/visualstudio/mac/nuget-walkthrough).

## <a name="source-editor"></a>Éditeur de code source

Indépendamment de si vous écrivez dans C, XAML, ou Javascript, l’éditeur de code partage les mêmes composants de base avec Visual Studio Windows, avec une interface utilisateur entièrement native.

Cela apporte quelques-unes des caractéristiques suivantes:

* Interface utilisateur native macOS (Cocoa) (info-bulles, surface de l’éditeur, ornements de marge, rendu de texte, IntelliSense)
* Filtrement de type IntelliSense et " articles d’importation d’exposition »
* Prise en charge des entrées de texte natives
* Prise en charge du langage RTL/BiDi
* Roslyn 3
* Prise en charge des signes insertion multiples
* Retour automatique à la ligne
* Mise à jour de l’interface utilisateur IntelliSense
* Amélioration de la recherche/remplacement
* Soutien d’extrait 
* Sélection du format
* Ampoules en ligne

Pour plus d’informations sur l’utilisation de l’éditeur source dans Visual Studio pour Mac, consultez la documentation [source Editor.](/visualstudio/mac/source-editor)

Pour garder les onglets visibles en tout temps, vous pouvez profiter de les épingler. Cela garantit que chaque fois que vous lancez un projet, l’onglet dont vous avez besoin apparaîtra toujours. Pour épingler un onglet, planez au-dessus de l’onglet et cliquez sur l’icône de la _broche_ :

![Épingler un onglet](media/ide-tour-tabpin.png)

## <a name="refactoring"></a>Refactorisation

Visual Studio pour Mac offre deux méthodes pratiques pour refactoriser votre code : Actions contextuelles et Analyse du code source. Pour plus d’informations sur ces méthodes, consultez l’article [Refactorisation](/visualstudio/mac/refactoring).

## <a name="debugging"></a>Débogage

Visual Studio for Mac a débogénaires qui soutiennent .NET Core, .NET Framework, Unity, et Xamarin projets. Visual Studio for Mac utilise le débbugger .NET Core et le Mono Soft Debugger, permettant à l’IDE de déboquer le code géré sur toutes les plates-formes. Pour plus d’informations sur le débogage, consultez l’article [Débogage](/visualstudio/mac/debugging).

Le débbuggeur contient de riches visualisateurs pour des types spéciaux tels que les cordes, les couleurs, les URL, ainsi que les tailles, coordonnées et courbes bézieres.

Pour plus d’informations sur les visualisations des données du débogueur, consultez l’article [Visualisations des données](/visualstudio/mac/data-visualizations).

## <a name="version-control"></a>Gestion de versions

Visual Studio pour Mac s’intègre aux systèmes de contrôle du code source Git et Subversion. Les projets soumis au contrôle du code source sont signalés par la branche figurant en regard du nom de la solution :

![Nom de la branche pour indiquer un projet soumis au contrôle du code source](media/ide-tour-image22.png)

Les fichiers comportant des modifications non validées sont indiqués par une annotation sur leur icône dans le Panneau Solution, comme l’illustre l’image suivante :

![Fichiers non validés dans le panneau Solution](media/ide-tour-image23.png)

Pour plus d’informations sur l’utilisation de la gestion de versions dans Visual Studio, consultez l’article [Gestion de versions](/visualstudio/mac/version-control).

## <a name="next-steps"></a>Étapes suivantes

- [Installer Visual Studio pour Mac](installation.md)
- [Consulter les charges de travail disponibles](workloads.md)

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Voir aussi

- [IDE Visual Studio (sur Windows)](/visualstudio/ide/visual-studio-ide)
