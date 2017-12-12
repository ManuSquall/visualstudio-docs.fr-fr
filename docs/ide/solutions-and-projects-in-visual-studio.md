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
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- projects [Visual Studio], setting up
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca3094b3bfe35381236798164fa18e58304bae3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="solutions-and-projects-in-visual-studio"></a>Solutions et projets dans Visual Studio
Quand vous créez une application, un site web, un plug-in, etc. dans Visual Studio, vous démarrez avec un *projet*. Au sens logique, un projet contient tous les fichiers de code source, toutes les icônes, toutes les images, tous les fichiers de données et tous les autres éléments qui seront compilés en un programme exécutable ou en un site web, ou ce qui est nécessaire pour effectuer la compilation. Un projet contient également tous les paramètres de compilateur et les autres fichiers de configuration qui peuvent être nécessaires aux différents services ou composants avec lesquels votre programme communiquera.  

> [!NOTE]
>  Vous n’êtes pas obligé d’utiliser des solutions ou des projets. Vous pouvez simplement ouvrir les fichiers dans Visual Studio et commencer à modifier votre code. Consultez [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) pour obtenir plus d’informations.  

Un fichier projet (.vbproj, .csproj, .vcxproj) est un fichier XML qui définit une hiérarchie de dossiers virtuels ainsi que les chemins de tous les éléments contenus dans le projet. Il contient également les paramètres de génération. Pour afficher le contenu d’un fichier projet, sélectionnez le nom du projet dans l’Explorateur de solutions, puis choisissez **Décharger le projet** dans le menu contextuel (clic droit). Ensuite, rouvrez le menu contextuel et choisissez **Modifier \<nom_projet\>**.  

Dans Visual Studio, le fichier projet est utilisé par l'Explorateur de solutions pour afficher le contenu et les paramètres du projet. Quand vous compilez votre projet, le moteur MSBuild utilise le fichier projet pour créer l'exécutable. Vous pouvez également personnaliser des projets pour produire d’autres types de sorties.  

Au sens logique et relativement au système de fichiers, un projet est contenu dans une *solution*, qui peut elle-même contenir un ou plusieurs projets associés, ainsi que des informations de génération, des paramètres de la fenêtre Visual Studio et des fichiers divers qui ne sont pas associés à un projet spécifique. Une solution est décrite par un fichier texte (.sln) qui a son propre format unique. Elle n’est généralement pas destinée à être modifiée manuellement.  

Une solution a un fichier *.suo* associé qui stocke les paramètres, les préférences et les informations de configuration pour chaque utilisateur qui a travaillé sur le projet.  

 Le diagramme suivant montre la relation entre les projets et les solutions, ainsi que les éléments qu'ils contiennent au sens logique.  

 ![Projets et solutions Visual Studio](../ide/media/vside-project-diagram.png)  

## <a name="creating-new-projects"></a>Création de nouveaux projets  
 Le moyen le plus simple de créer un projet consiste à démarrer à partir d’un modèle de projet. Un modèle de projet est constitué d’un ensemble de base de fichiers de code prégénérés, de fichiers config, de ressources et de paramètres que vous pouvez utiliser pour commencer à créer un type particulier d’application ou de site web dans un langage de programmation spécifique. Les modèles disponibles s’affichent dans la boîte de dialogue **Nouveau projet** ou **Nouveau site web** quand vous choisissez **Fichier**, **Nouveau**, **Projet** ou **Fichier**, **Nouveau**, **Site web**. Pour plus d’informations, consultez [Création de solutions et de projets](../ide/creating-solutions-and-projects.md).  

Vous pouvez aussi créer des modèles de projets et d'éléments personnalisés. Pour plus d’informations, consultez [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).  

## <a name="managing-projects-in-solution-explorer"></a>Gestion de projets dans l'Explorateur de solutions  
 Après avoir créé un nouveau projet, vous utilisez **l'Explorateur de solutions** pour afficher et gérer des projets et des solutions, ainsi que leurs éléments associés. L’illustration suivante montre l’Explorateur de solutions avec une solution C# qui contient deux projets.  

 ![Explorateur de solutions](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>Dans cette section  

-   [Création de solutions et de projets](../ide/creating-solutions-and-projects.md)  

-   [Ajout et suppression d’éléments de projet](../ide/adding-and-removing-project-items.md)  

-   [Gestion des propriétés des projets et des solutions](../ide/managing-project-and-solution-properties.md)  

-   [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)  

-   [Propriétés des applications](../ide/application-properties.md)  

-   [Gestion d’assembly et signature de manifeste](../ide/managing-assembly-and-manifest-signing.md)  

-   [Guide pratique pour spécifier une icône d’application (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [Cibler une version spécifique du .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>Voir aussi  
 [IDE Visual Studio](../ide/visual-studio-ide.md)
