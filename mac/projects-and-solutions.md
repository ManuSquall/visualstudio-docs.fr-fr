---
title: Projets et solutions
description: Ce document fournit une vue d’ensemble des projets et des solutions dans Visual Studio pour Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: b66a1dfbe0569c501d05b34425e198f1501438ca
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691275"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Projets et solutions dans Visual Studio pour Mac

Cet article offre une vue d’ensemble des concepts de *projet* et de *solution* dans Visual Studio pour Mac.

> [!NOTE] 
> Cette rubrique s’applique à Visual Studio pour Mac. Pour Visual Studio sur Windows, consultez [Projets et solutions dans Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Projets

Quand vous créez une application, un site web, etc. dans Visual Studio pour Mac, vous commencez avec un projet. Le projet contient tous les fichiers (code source, images, fichiers de données, etc.) nécessaires à la compilation du fichier exécutable, de la bibliothèque ou du site web.

Un projet est défini par un fichier (par exemple, `.csproj` pour les projets C#) contenant du code xml qui définit la hiérarchie des dossiers et fichiers, les chemins des fichiers et les paramètres propres au projet, tels que les paramètres de build.

Quand un projet est chargé par Visual Studio pour Mac, le Panneau Solutions utilise le fichier projet pour afficher les fichiers et les dossiers dans votre projet. Pendant la compilation, MSBuild lit les paramètres dans le fichier projet pour créer l’exécutable.

## <a name="solutions"></a>Solutions

Une *solution* est un conteneur qui regroupe un ou plusieurs projets connexes. Les solutions sont décrites par un fichier texte (extension `.sln`) qui a son propre format unique. Il n’est pas destiné à être modifié manuellement.

## <a name="managing-projects-in-the-solution-pad"></a>Gestion des projets dans le Panneau Solutions

Après avoir créé ou chargé un projet, vous pouvez utiliser le Panneau Solutions pour afficher et gérer le projet ou la solution et les fichiers qui s’y trouvent. L’illustration suivante montre le Panneau Solutions avec une solution .NET Core qui contient deux projets :

![Exemple de solution avec plusieurs projets](media/solution-example.png)

Vous pouvez gérer les propriétés des projets et des solutions en double-cliquant sur le nom du projet ou de la solution, ou en cliquant avec le bouton droit et choisissant **Options**.

Pour plus d’informations sur ces options, consultez l’article [Gestion des solutions et des propriétés des projets](managing-solutions-and-project-properties.md).

## <a name="see-also"></a>Voir aussi

- [Solutions et projets dans Visual Studio (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
