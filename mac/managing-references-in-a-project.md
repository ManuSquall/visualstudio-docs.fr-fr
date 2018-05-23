---
title: Gestion des références dans un projet
description: Cet article décrit comment gérer les références d’un projet dans Visual Studio pour Mac
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: 82875955e861ec25e1444874afaa8b7f2e807fa7
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2018
---
# <a name="managing-references-in-a-project"></a>Gestion des références dans un projet

Visual Studio pour Mac fournit deux moyens d’ajouter des références supplémentaires à votre projet :

![Références de projets](media/projects-and-solutions-image10.png)

Ces équivalents sont :

* Références
* NuGets (ajouté via le dossier Packages)

Des références web et des références natives peuvent également être ajoutées à tout projet.

## <a name="assembly-references"></a>Références d’assembly

Chaque framework dans Xamarin est fourni avec plus d’une dizaine d’assemblys. Certains de ces packages d’assemblys ne sont pas référencés dans votre projet par défaut. 

Pour modifier les packages qui sont référencés dans votre projet, utilisez la boîte de dialogue _Modifier les références_, que vous pouvez afficher en double-cliquant sur le dossier Références ou en sélectionnant Modifier les références dans les actions de son menu contextuel :

![Boîte de dialogue Références d’assembly](media/projects-and-solutions-image11.png)

Pour plus d’informations sur les assemblys disponibles pour chaque framework de Xamarin, reportez-vous au guide [Available Assemblies](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet est le gestionnaire de packages le plus répandu pour le développement .NET. La prise en charge de NuGet par Visual Studio pour Mac vous permet de rechercher des packages à ajouter à votre projet.

Pour cela, cliquez avec le bouton droit sur le dossier **Package** dans le panneau Solution et sélectionnez Ajouter des Packages.

Vous trouverez plus d’informations sur l’utilisation d’un package NuGet dans la procédure pas à pas [Inclusion d’un package NuGet dans votre projet](nuget-walkthrough.md).
