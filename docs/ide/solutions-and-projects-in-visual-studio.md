---
title: Solutions et projets dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 06/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.savedeferredsaveprojectonclose
- vs.untrustedtemplateopeningdocuments
- Project Properties.FullPath
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.getopenfilename
- vs.addnewitem
- vs.encoding
- vs.addexistingitem
- Project Properties.URL
- VS.SolutionExplorer
- Project Properties.FileName
- SolutionProperties.Name
- VS.SaveChangesDlg
- vs.newproject
- VS.SolutionExplorer.Selection
- SolutionProperties.Path
- vs.getdirectoryname
- vs.addexistingsolutionitem
- SolutionProperties.Description
- vs.environment.solutions
- vs.saveordiscarddeferredsaveproject
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- vs.solutionpropertypages
- vs.solutionpropertypages.startupproject
- vs.solutionpropertypages.configurationsettings
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- workspaces
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- vs.solutionpropertypages.projectdependencies
- applications [Visual Studio]
- projects [Visual Studio], setting up
- miscellaneous files
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 35
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 28dfbb85790cfda2c3d840ce2d57468b5421bee0
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---
# <a name="solutions-and-projects-in-visual-studio"></a>Solutions et projets dans Visual Studio
Quand vous créez une application pour mobile, une application, un site web, une application web, un script, un plug-in, etc. dans Visual Studio, vous démarrez avec un *projet*. Au sens logique, un projet contient tous les fichiers de code source, toutes les icônes, toutes les images, tous les fichiers de données et tous les autres éléments qui seront compilés en un programme exécutable ou en un site web, ou ce qui est nécessaire pour effectuer la compilation.  Un projet contient également tous les paramètres de compilateur et les autres fichiers de configuration qui peuvent être nécessaires aux différents services ou composants avec lesquels votre programme communiquera.

> [!NOTE]
>  Vous n’êtes pas obligé d’utiliser des solutions ou des projets. Vous pouvez simplement ouvrir les fichiers dans Visual Studio et commencer à modifier votre code. Pour plus d’informations, consultez [Ouvrir un dossier quelconque avec Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/).


 Concrètement, un projet est un fichier XML (*.vbproj, \*.csproj, \*.vcxproj) qui définit une hiérarchie de dossiers virtuels ainsi que les chemins d’accès à tous les éléments qu’il « contient » et tous les paramètres de build. Dans Visual Studio, le fichier projet est utilisé par l'Explorateur de solutions pour afficher le contenu et les paramètres du projet. Quand vous compilez votre projet, le moteur MSBuild utilise le fichier projet pour créer l'exécutable. Vous pouvez également personnaliser des projets pour produire d'autres types de sorties.  

 Au sens logique et relativement au système de fichiers, un projet est contenu dans une *solution*, qui peut contenir un ou plusieurs projets, ainsi que les informations de build, les paramètres de la fenêtre Visual Studio et les différents fichiers qui ne sont associés à aucun projet. Concrètement, la solution est un fichier texte qui a son format propre ; il n'est généralement pas destiné à être modifié manuellement.  

 Une solution a un fichier *.suo* associé qui stocke les paramètres, les préférences et les informations de configuration pour chaque utilisateur qui a travaillé sur le projet.  

 Le diagramme suivant montre la relation entre les projets et les solutions, ainsi que les éléments qu'ils contiennent au sens logique.  

 ![Projets et solutions Visual Studio](~/ide/media/vside-project-diagram.png)  

 Vous pouvez aussi créer des modèles de projets et d'éléments personnalisés. Pour plus d’informations, consultez [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).  

## <a name="creating-new-projects"></a>Création de nouveaux projets  
 Le moyen le plus simple pour créer un nouveau projet consiste à démarrer avec un modèle de projet prédéfini, qui se compose d'un ensemble de base de fichiers de code prégénérés, de fichiers de configuration, de ressources et de paramètres qui vous aideront à démarrer la création d'un type particulier d'application ou de site web dans un langage de programmation particulier. Ces modèles sont ce que vous voyez dans la boîte de dialogue **Nouveau projet** quand vous choisissez **Fichier &#124; Nouveau &#124; Projet** ou **Fichier &#124; Nouveau &#124; Site web** dans le menu principal, puis que vous naviguez. Pour plus d’informations, consultez [Création de solutions et de projets](../ide/creating-solutions-and-projects.md).  

## <a name="managing-projects-in-solution-explorer"></a>Gestion de projets dans l'Explorateur de solutions  
 Après avoir créé un nouveau projet, vous utilisez **l'Explorateur de solutions** pour afficher et gérer des projets et des solutions, ainsi que leurs éléments associés. L’illustration suivante montre l’Explorateur de solutions avec une solution C# qui contient deux projets.  

 ![Explorateur de solutions](~/ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>Dans cette section  

-   [Création de projets et de solutions](../ide/creating-solutions-and-projects.md)  

-   [Ajout et suppression d’éléments de projet](../ide/adding-and-removing-project-items.md)  

-   [Gestion des propriétés des projets et des solutions](../ide/managing-project-and-solution-properties.md)  

-   [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)  

-   [Propriétés d’une application](../ide/application-properties.md)  

-   [Gestion d’assembly et signature de manifeste](../ide/managing-assembly-and-manifest-signing.md)  

-   [Guide pratique pour spécifier une icône d’application (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [Cibler une version spécifique du .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>Voir aussi  
 [IDE Visual Studio](../ide/visual-studio-ide.md)

