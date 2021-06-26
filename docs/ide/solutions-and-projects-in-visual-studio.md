---
title: Que sont les solutions Visual Studio & les projets ?
description: Découvrez les projets et solutions Visual Studio, comment créer de nouveaux projets à partir d’un modèle et comment afficher & gérer des projets dans Explorateur de solutions.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/31/2020
ms.topic: conceptual
f1_keywords:
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a186c63cf695184b74780eeb6ab16b85c8aef5e
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924966"
---
# <a name="what-are-solutions-and-projects-in-visual-studio"></a>Que sont les solutions et les projets dans Visual Studio ?

Dans cet article, vous allez découvrir ce qu’est un *projet* et une *solution* dans Visual Studio. Elle aborde également brièvement la fenêtre outil Explorateur de solutions et explique comment créer un nouveau projet.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Projets et solutions dans Visual Studio pour Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projets

Lorsque vous créez une application ou un site Web dans Visual Studio, vous démarrez avec un *projet*. Dans un sens logique, un projet contient tous les fichiers qui sont compilés dans un fichier exécutable, une bibliothèque ou un site Web. Ces fichiers peuvent inclure du code source, des icônes, des images, des fichiers de données, etc. Un projet contient également des paramètres de compilateur et d’autres fichiers de configuration qui peuvent être nécessaires aux différents services ou composants avec lesquels votre programme communique.

### <a name="project-file"></a>Fichier projet

Visual Studio utilise [MSBuild](../msbuild/msbuild.md) pour générer chaque projet dans une solution, et chaque projet contient un fichier projet MSBuild. L’extension de fichier reflète le type de projet, par exemple, un projet C# (. csproj), un projet de Visual Basic (. vbproj) ou un projet de base de données (. dbproj). Le fichier projet est un document XML qui contient toutes les informations et les instructions dont MSBuild a besoin pour générer votre projet, y compris le contenu, la plateforme requise, les informations de versioning, les paramètres du serveur Web ou du serveur de base de données, ainsi que les tâches à effectuer.

Les fichiers projet sont basés sur le [schéma XML MSBuild](../msbuild/msbuild-project-file-schema-reference.md). Pour examiner le contenu des [fichiers projet de type SDK](../msbuild/how-to-use-project-sdk.md) plus récents dans Visual Studio, cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** puis sélectionnez **modifier \<projectname\>**. Pour examiner le contenu de .NET Framework et d’autres projets de ce style, déchargez tout d’abord le projet (cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** puis sélectionnez **décharger le projet**). Ensuite, cliquez avec le bouton droit sur le projet, puis choisissez **modifier \<projectname\>**.

> [!NOTE]
> Vous n’êtes pas obligé d’utiliser des solutions ou des projets dans Visual Studio pour modifier, générer et déboguer du code. Vous pouvez simplement ouvrir le dossier qui contient vos fichiers de code source dans Visual Studio et commencer à les modifier. Pour plus d’informations, consultez [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

### <a name="create-new-projects"></a>Créer de nouveaux projets

Le moyen le plus simple de créer un nouveau projet consiste à utiliser un modèle de projet pour le type de projet souhaité. Un modèle de projet comprend un ensemble de base de fichiers de code prégénérés, de fichiers de configuration, de ressources et de paramètres. Utilisez **fichier**  >  **nouveau**  >  **projet** pour sélectionner un modèle de projet. Pour plus d’informations, consultez [créer un nouveau projet](create-new-project.md).

Vous pouvez également créer un modèle de projet personnalisé que vous pouvez utiliser pour créer des projets à partir de. Pour plus d’informations, consultez [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).

Lorsque vous créez un projet, Visual Studio l’enregistre à son emplacement par défaut, *%UserProfile%\source\repos*. Pour modifier cet emplacement, accédez à **Outils**  >  **options**  >  **projets et solutions**  >  **emplacements**. Pour plus d’informations, consultez [boîte de dialogue Options : projets et Solutions > emplacements](./reference/projects-solutions-locations-options.md).

## <a name="solutions"></a>Solutions

Un projet est contenu dans une *solution*. Malgré son nom, une solution n’est pas une « réponse ». Il s’agit simplement d’un conteneur pour un ou plusieurs projets associés, ainsi que des informations de génération, des paramètres de la fenêtre Visual Studio et des fichiers divers qui ne sont pas associés à un projet spécifique.

### <a name="solution-file"></a>Fichier solution

Visual Studio utilise deux types de fichiers (*. sln* et *. suo*) pour stocker les paramètres des solutions :

|Extension|Nom|Description|
|---------------|----------|-----------------|
|.sln|Solution Visual Studio|Organise les projets, les éléments de projet et les éléments de solution dans la solution.|
|.suo|Options utilisateur de solution|Stocke les personnalisations et les paramètres au niveau de l’utilisateur, tels que les points d’arrêt.|

> [!IMPORTANT]
> Une solution est décrite par un fichier texte (extension *.sln*) qui a son propre format unique. Il n’est pas destiné à être modifié manuellement. Inversement, le fichier *. suo* est un fichier masqué qui n’est pas affiché sous les paramètres par défaut de l’Explorateur de fichiers. Pour afficher les fichiers masqués, dans le menu **Affichage** de l’Explorateur de fichiers, cochez la case **Éléments masqués**.

### <a name="solution-folder"></a>Dossier de solution

Un « dossier de solution » est un dossier virtuel qui se trouve uniquement dans **Explorateur de solutions**, où vous pouvez l’utiliser pour regrouper des projets dans une solution. Si vous souhaitez localiser un fichier solution sur un ordinateur, accédez à **Outils**  >  **options**  >  **projets et solutions**  >  **emplacements**. Pour plus d’informations, consultez [boîte de dialogue Options : projets et Solutions > emplacements](./reference/projects-solutions-locations-options.md).

> [!TIP]
> Pour obtenir un exemple de projet et de solution créés à partir de zéro, ainsi que des instructions pas à pas et des exemples de code, consultez [Présentation des projets et des solutions](../get-started/tutorial-projects-solutions.md).

## <a name="solution-explorer"></a>Explorateur de solutions

Après avoir créé un nouveau projet, vous pouvez utiliser **l’Explorateur de solutions** pour afficher et gérer le projet et la solution, ainsi que leurs éléments associés. L’illustration suivante montre **Explorateur de solutions** avec une solution C# qui contient deux projets :

::: moniker range="vs-2017"

![Capture d’écran de Explorateur de solutions avec deux projets.](../ide/media/vs2015_solution_explorer.png)

La barre d’outils en haut de **l’Explorateur de solutions** comprend des boutons pour basculer d’un affichage de solutions à un affichage de dossiers, afficher les fichiers cachés, réduire tous les nœuds et bien plus encore.

::: moniker-end

::: moniker range=">=vs-2019"

![Capture d’écran de Explorateur de solutions avec deux projets dans Visual Studio.](../ide/media/solution-explorer.png)

La barre d’outils en haut de **Explorateur de solutions** contient des boutons pour passer d’un affichage de solution à un affichage des dossiers, filtrer les modifications en attente, afficher tous les fichiers, réduire tous les nœuds, afficher les pages de [Propriétés](managing-project-and-solution-properties.md) , afficher un aperçu du code dans l' [éditeur de code](writing-code-in-the-code-and-text-editor.md), et bien plus encore.

::: moniker-end

De nombreuses commandes de menu sont disponibles dans le menu contextuel, accessible par un clic droit, sur les différents éléments de **Explorateur de solutions**. Ces commandes incluent la génération d’un projet, la gestion de packages NuGet, l’ajout d’une référence, l’affectation d’un nouveau nom de fichier et l’exécution de tests, entre autres.

Pour les projets ASP.NET Core, vous pouvez personnaliser la façon dont les fichiers sont imbriqués dans **l’Explorateur de solutions**. Pour plus d’informations, consultez [Personnaliser l’imbrication de fichiers dans l’Explorateur de solutions](file-nesting-solution-explorer.md).

> [!TIP]
> Si vous avez fermé Explorateur de solutions et que vous souhaitez l’ouvrir à nouveau, choisissez **Afficher** les  >  **Explorateur de solutions** dans la barre de menus ou appuyez sur **CTRL** + **ALT** + **L**. Et, si vous avez fermé les onglets latéraux et que vous souhaitez les restaurer à leurs emplacements par défaut, choisissez **fenêtre**  >  **Réinitialiser la disposition de fenêtre** dans la barre de menus.

> [!NOTE]
> Pour afficher les images d’application et les icônes qui apparaissent dans Visual Studio, téléchargez la [**bibliothèque d’images Visual Studio**](https://www.microsoft.com/download/details.aspx?id=35825).

## <a name="see-also"></a>Voir aussi

- [Présentation des projets et solutions](../get-started/tutorial-projects-solutions.md)
- [Gérer les propriétés des projets et des solutions](managing-project-and-solution-properties.md)
- [Solutions filtrées dans Visual Studio](filtered-solutions.md)
- [Porter, migrer et mettre à niveau des projets](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Ressources pour la résolution des erreurs de l’IDE Visual Studio](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
- [Projets et solutions (Visual Studio pour Mac)](/visualstudio/mac/projects-and-solutions)
