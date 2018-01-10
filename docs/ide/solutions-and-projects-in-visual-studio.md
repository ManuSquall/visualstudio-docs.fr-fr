---
title: Solutions et projets dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 10/5/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.newproject
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items [Visual Studio]
- solutions [Visual Studio]
- project items [Visual Studio]
- solutions [Visual Studio], designing
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4d242a74bd1eaef86e3465d53aa148429af42f7e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="solutions-and-projects-in-visual-studio"></a>Solutions et projets dans Visual Studio

## <a name="projects"></a>Projets

Quand vous créez une application, un site web, un plug-in, etc. dans Visual Studio, vous démarrez avec un *projet*. Du point de vue logique, un projet contient tous les fichiers de code source, icônes, images, fichiers de données, et ainsi de suite, qui sont compilés dans un fichier exécutable, une bibliothèque ou un site web. Un projet contient également des paramètres de compilateur et d’autres fichiers de configuration qui peuvent être nécessaires aux différents services ou composants avec lesquels votre programme communique.

> [!NOTE]
> Vous n’êtes pas obligé d’utiliser des solutions et des projets dans Visual Studio pour modifier, générer et déboguer du code. Vous pouvez simplement ouvrir le dossier qui contient vos fichiers de code source dans Visual Studio et commencer à les modifier. Consultez [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) pour obtenir plus d’informations.

Un projet est défini dans un fichier XML avec une extension comme .vcxproj, .csproj ou .vbproj. Ce fichier contient une hiérarchie de dossiers virtuels et des chemins vers tous les éléments du projet. Il contient également les paramètres de génération.

> [!TIP]
> Pour consulter le contenu d’un fichier projet dans Visual Studio, déchargez tout d’abord le projet en sélectionnant le nom du projet dans l’Explorateur de solutions, puis choisissez **Décharger le projet** dans le menu contextuel. Ensuite, rouvrez le menu contextuel et choisissez **Modifier \<nom_projet\>**.

Dans Visual Studio, le fichier projet est utilisé par l'Explorateur de solutions pour afficher le contenu et les paramètres du projet. Quand vous compilez votre projet, le moteur MSBuild utilise le fichier projet pour créer l'exécutable. Vous pouvez également personnaliser des projets pour produire d’autres types de sorties.

## <a name="solutions"></a>Solutions

Un projet est contenu dans une *solution*. Une solution contient un ou plusieurs projets associés, ainsi que des informations de génération, des paramètres de la fenêtre Visual Studio et des fichiers divers qui ne sont pas associés à un projet spécifique. Une solution est décrite par un fichier texte (extension .sln) qui a son propre format unique. Il n’est généralement pas destiné à être modifié manuellement.

Une solution a un fichier *.suo* associé qui stocke les paramètres, les préférences et les informations de configuration pour chaque utilisateur qui a travaillé sur le projet.

## <a name="creating-new-projects"></a>Création de nouveaux projets

Le moyen le plus simple pour créer un projet consiste à partir d’un modèle de projet pour un type particulier d’application ou de site web. Un modèle de projet se compose d’un ensemble de fichiers de code prégénérés, de fichiers de configuration, de ressources et de paramètres. Les modèles disponibles s’affichent dans la boîte de dialogue **Nouveau projet** ou **Nouveau site web** quand vous choisissez **Fichier**, **Nouveau**, **Projet** ou **Fichier**, **Nouveau**, **Site web**. Pour plus d’informations, consultez [Création de solutions et de projets](../ide/creating-solutions-and-projects.md).

Vous pouvez aussi créer des modèles de projets et d'éléments personnalisés. Pour plus d’informations, consultez [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).

## <a name="managing-projects-in-solution-explorer"></a>Gestion de projets dans l'Explorateur de solutions

Après avoir créé un nouveau projet, vous pouvez utiliser **l’Explorateur de solutions** pour afficher et gérer le projet et la solution, ainsi que leurs éléments associés. L’illustration suivante montre l’Explorateur de solutions avec une solution C# qui contient deux projets.

![Explorateur de solutions](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")

## <a name="see-also"></a>Voir aussi

[IDE Visual Studio](../ide/visual-studio-ide.md)
