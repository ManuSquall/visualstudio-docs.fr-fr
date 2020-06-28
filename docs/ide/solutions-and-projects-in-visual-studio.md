---
title: Solutions et projets
ms.date: 06/26/2020
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
- vs.addnewsolutionitem
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad0ee64afa78a962271d2b702ee525287c5b2457
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468728"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Solutions et projets dans Visual Studio

Cette page décrit le concept d’un *projet* et d’une *solution* dans Visual Studio. Elle aborde également brièvement la fenêtre outil Explorateur de solutions et explique comment créer un nouveau projet.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Projets et solutions dans Visual Studio pour Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projets

Lorsque vous créez une application ou un site Web dans Visual Studio, vous démarrez avec un *projet*. Dans un sens logique, un projet contient tous les fichiers qui sont compilés dans un fichier exécutable, une bibliothèque ou un site Web. Ces fichiers peuvent inclure du code source, des icônes, des images, des fichiers de données, etc. Un projet contient également des paramètres de compilateur et d’autres fichiers de configuration qui peuvent être nécessaires aux différents services ou composants avec lesquels votre programme communique.

### <a name="project-file"></a>Fichier projet

Visual Studio utilise [MSBuild](../msbuild/msbuild.md) pour générer chaque projet dans une solution, et chaque projet contient un fichier projet MSBuild. L’extension de fichier reflète le type de projet, par exemple, un projet C# (. csproj), un projet de Visual Basic (. vbproj) ou un projet de base de données (. dbproj). Le fichier projet est un document XML qui contient toutes les informations et les instructions dont MSBuild a besoin pour générer votre projet, y compris le contenu, la plateforme requise, les informations de versioning, les paramètres du serveur Web ou du serveur de base de données, ainsi que les tâches à effectuer.

Les fichiers projet sont basés sur le [schéma XML MSBuild](../msbuild/msbuild-project-file-schema-reference.md). Pour examiner le contenu des [fichiers projet de type SDK](../msbuild/how-to-use-project-sdk.md) plus récents dans Visual Studio, cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** puis sélectionnez **modifier \<projectname\> **. Pour examiner le contenu de .NET Framework et d’autres projets de ce style, déchargez tout d’abord le projet (cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** puis sélectionnez **décharger le projet**). Ensuite, cliquez avec le bouton droit sur le projet, puis choisissez **modifier \<projectname\> **.

> [!NOTE]
> Vous n’êtes pas obligé d’utiliser des solutions ou des projets dans Visual Studio pour modifier, générer et déboguer du code. Vous pouvez simplement ouvrir le dossier qui contient vos fichiers de code source dans Visual Studio et commencer à les modifier. Pour plus d’informations, consultez [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Solutions

Un projet est contenu dans une *solution*. Malgré son nom, une solution n’est pas une « réponse ». Il s’agit simplement d’un conteneur pour un ou plusieurs projets associés, ainsi que des informations de génération, des paramètres de la fenêtre Visual Studio et des fichiers divers qui ne sont pas associés à un projet spécifique. Une solution est décrite par un fichier texte (extension *.sln*) qui a son propre format unique. Il n’est pas destiné à être modifié manuellement.

Visual Studio utilise deux types de fichiers (*. sln* et *. suo*) pour stocker les paramètres des solutions :

|Extension|Nom|Description|
|---------------|----------|-----------------|
|.sln|Solution Visual Studio|Organise les projets, les éléments de projet et les éléments de solution dans la solution.|
|.suo|Options utilisateur de solution|Stocke les personnalisations et les paramètres au niveau de l’utilisateur, tels que les points d’arrêt.|

## <a name="create-new-projects"></a>Créer de nouveaux projets

Le moyen le plus simple pour créer un projet consiste à partir d’un modèle de projet pour un type particulier d’application ou de site web. Un modèle de projet se compose d’un ensemble de fichiers de code prégénérés, de fichiers de configuration, de ressources et de paramètres. Ces modèles sont disponibles dans la boîte de dialogue dans laquelle vous créez un nouveau projet (**fichier**  >  **nouveau**  >  **projet**). Pour plus d’informations, consultez [Créer un nouveau projet dans Visual Studio](create-new-project.md) et [Créer des solutions et projets](../ide/creating-solutions-and-projects.md).

Si vous personnalisez souvent vos projets d’une certaine manière, vous pouvez créer un modèle de projet personnalisé que vous pourrez ensuite utiliser pour créer de nouveaux projets à partir de. Pour plus d’informations, consultez [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).

Quand vous créez un projet, il est enregistré par défaut dans *%USERPROFILE%\source\repos*. Vous pouvez personnaliser cet emplacement dans le paramètre **Emplacement des projets** sous **Outils** > **Options** > **Projets et solutions** > **Emplacements**. Pour plus d’informations, consultez [Page Projets et solutions, boîte de dialogue Options](../ide/reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Explorateur de solutions

Après avoir créé un nouveau projet, vous pouvez utiliser **l’Explorateur de solutions** pour afficher et gérer le projet et la solution, ainsi que leurs éléments associés. L’illustration suivante montre **Explorateur de solutions** avec une solution C# qui contient deux projets :

![Explorateur de solutions](../ide/media/vs2015_solution_explorer.png)

De nombreuses commandes de menu sont disponibles dans le menu contextuel sur différents éléments de **l’Explorateur de solutions**. Ces commandes incluent la génération d’un projet, la gestion de packages NuGet, l’ajout d’une référence, l’affectation d’un nouveau nom de fichier et l’exécution de tests, entre autres. La barre d’outils en haut de **l’Explorateur de solutions** comprend des boutons pour basculer d’un affichage de solutions à un affichage de dossiers, afficher les fichiers cachés, réduire tous les nœuds et bien plus encore.

> [!TIP]
> Si vous avez fermé Explorateur de solutions et que vous souhaitez l’ouvrir à nouveau, choisissez **fenêtre**  >  **Réinitialiser la disposition de fenêtre** dans la barre de menus.

Pour les projets ASP.NET Core, vous pouvez personnaliser la façon dont les fichiers sont imbriqués dans **l’Explorateur de solutions**. Pour plus d’informations, consultez [Personnaliser l’imbrication de fichiers dans l’Explorateur de solutions](file-nesting-solution-explorer.md).

Pour afficher une liste de certaines des icônes qui apparaissent dans Explorateur de solutions, consultez [affichage de classes et icônes](class-view-and-object-browser-icons.md)de l’Explorateur d’objets.

## <a name="see-also"></a>Voir aussi

- [IDE Visual Studio](../get-started/visual-studio-ide.md)
- [Porter, migrer et mettre à niveau des projets](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Projets et solutions (Visual Studio pour Mac)](/visualstudio/mac/projects-and-solutions)
- [Ajouter et supprimer des éléments de projet (Visual Studio pour Mac)](/visualstudio/mac/add-and-remove-project-items)
