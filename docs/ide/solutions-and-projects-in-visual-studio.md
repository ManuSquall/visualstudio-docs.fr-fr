---
title: Solutions et projets
ms.date: 10/05/2017
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42a8dbc2fd9a6fc89b0be62271b048f8275a82b2
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432201"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Solutions et projets dans Visual Studio

Cet article décrit le concept d’un *projet* et d’une *solution* dans Visual Studio. Il décrit également brièvement comment créer un projet ainsi que la fenêtre Outil **Explorateur de solutions**.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Projets et solutions dans Visual Studio pour Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projets

Quand vous créez une application, un site web, un plug-in, etc. dans Visual Studio, vous démarrez avec un *projet*. Du point de vue logique, un projet contient tous les fichiers de code source, icônes, images, fichiers de données, et ainsi de suite, qui sont compilés dans un fichier exécutable, une bibliothèque ou un site web. Un projet contient également des paramètres de compilateur et d’autres fichiers de configuration qui peuvent être nécessaires aux différents services ou composants avec lesquels votre programme communique.

> [!NOTE]
> Vous n’êtes pas obligé d’utiliser des solutions et des projets dans Visual Studio pour modifier, générer et déboguer du code. Vous pouvez simplement ouvrir le dossier qui contient vos fichiers de code source dans Visual Studio et commencer à les modifier. Pour plus d’informations, consultez [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

Un projet est défini dans un fichier XML avec une extension comme *.vbproj*, *.csproj* ou *.vcxproj*. Ce fichier contient une hiérarchie de dossiers virtuels et des chemins vers tous les éléments du projet. Il contient également les paramètres de génération.

> [!TIP]
> Pour consulter le contenu d’un fichier projet dans Visual Studio, déchargez tout d’abord le projet en sélectionnant le nom du projet dans **l’Explorateur de solutions**, puis choisissez **Décharger le projet** dans le menu contextuel. Ensuite, rouvrez le menu contextuel et choisissez **Modifier \<nom_projet\>** .

Dans Visual Studio, le fichier projet est utilisé par **l’Explorateur de solutions** pour afficher le contenu et les paramètres du projet. Quand vous compilez votre projet, le moteur MSBuild utilise le fichier projet pour créer l'exécutable. Vous pouvez également personnaliser des projets pour produire d’autres types de sorties.

## <a name="solutions"></a>Solutions

Un projet est contenu dans une *solution*. Malgré son nom, une solution n’est pas une « réponse ». Il s’agit simplement d’un conteneur pour un ou plusieurs projets associés, ainsi que des informations de génération, des paramètres de la fenêtre Visual Studio et des fichiers divers qui ne sont pas associés à un projet spécifique. Une solution est décrite par un fichier texte (extension *.sln*) qui a son propre format unique. Il n’est pas destiné à être modifié manuellement.

Visual Studio utilise deux types de fichiers ( *.sln* et *.suo*) pour stocker les paramètres des solutions :

|Extension|Name|Description|
|---------------|----------|-----------------|
|.sln|Solution Visual Studio|Organise les projets, les éléments de projet et les éléments de solution dans la solution.|
|.suo|Options utilisateur de solution|Stocke les personnalisations et les paramètres au niveau de l’utilisateur, tels que les points d’arrêt.|

## <a name="create-new-projects"></a>Créer de nouveaux projets

Le moyen le plus simple pour créer un projet consiste à partir d’un modèle de projet pour un type particulier d’application ou de site web. Un modèle de projet se compose d’un ensemble de fichiers de code prégénérés, de fichiers de configuration, de ressources et de paramètres. Ces modèles sont disponibles dans la boîte de dialogue où vous créez un projet (**Fichier** > **Nouveau** > **Projet**). Pour plus d’informations, consultez [Créer un nouveau projet dans Visual Studio](create-new-project.md) et [Créer des solutions et projets](../ide/creating-solutions-and-projects.md).

Si vous personnalisez souvent vos projets d’une certaine manière, vous pouvez créer un modèle de projet personnalisé que vous pouvez ensuite utiliser pour la création de nouveaux projets. Pour plus d’informations, consultez [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).

Quand vous créez un projet, il est enregistré par défaut dans *%USERPROFILE%\source\repos*. Vous pouvez personnaliser cet emplacement dans le paramètre **Emplacement des projets** sous **Outils** > **Options** > **Projets et solutions** > **Emplacements**. Pour plus d’informations, consultez [Page Projets et solutions, boîte de dialogue Options](../ide/reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Explorateur de solutions

Après avoir créé un nouveau projet, vous pouvez utiliser **l’Explorateur de solutions** pour afficher et gérer le projet et la solution, ainsi que leurs éléments associés. L’illustration suivante montre l’**Explorateur de solutions** avec une solution C# qui contient deux projets :

![Explorateur de solutions](../ide/media/vs2015_solution_explorer.png)

De nombreuses commandes de menu sont disponibles dans le menu contextuel sur différents éléments de **l’Explorateur de solutions**. Ces commandes incluent la génération d’un projet, la gestion de packages NuGet, l’ajout d’une référence, l’affectation d’un nouveau nom de fichier et l’exécution de tests, entre autres. La barre d’outils en haut de **l’Explorateur de solutions** comprend des boutons pour basculer d’un affichage de solutions à un affichage de dossiers, afficher les fichiers cachés, réduire tous les nœuds et bien plus encore.

Pour les projets ASP.NET Core, vous pouvez personnaliser la façon dont les fichiers sont imbriqués dans **l’Explorateur de solutions**. Pour plus d’informations, consultez [Personnaliser l’imbrication de fichiers dans l’Explorateur de solutions](file-nesting-solution-explorer.md).

## <a name="see-also"></a>Voir aussi

- [IDE Visual Studio](../get-started/visual-studio-ide.md)
- [Projets et solutions (Visual Studio pour Mac)](/visualstudio/mac/projects-and-solutions)
- [Ajouter et supprimer des éléments de projet (Visual Studio pour Mac)](/visualstudio/mac/add-and-remove-project-items)
