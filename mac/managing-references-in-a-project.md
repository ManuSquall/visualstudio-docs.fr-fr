---
title: "Gestion des références dans un projet"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: 30f6c99c6ac827b7da94fd228a7034e9ce0b0fac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="managing-references-in-a-project"></a>Gestion des références dans un projet

Visual Studio pour Mac fournit trois moyens d’ajouter des références supplémentaires à votre projet :

![Références de projets](media/projects-and-solutions-image10.png)

Ces équivalents sont :

* Références
* NuGets (ajouté via le dossier Packages)
* Composants

Des références web et des références natives peuvent également être ajoutées à tout projet.

## <a name="assembly-references"></a>Références d’assembly

Chaque framework dans Xamarin est fourni avec plus d’une dizaine d’assemblys. Certains de ces packages d’assemblys ne sont pas référencés dans votre projet par défaut. 

Pour modifier les packages qui sont référencés dans votre projet, utilisez la boîte de dialogue _Modifier les références_, que vous pouvez afficher en double-cliquant sur le dossier Références ou en sélectionnant Modifier les références dans les actions de son menu contextuel :

![Boîte de dialogue Références d’assembly](media/projects-and-solutions-image11.png)

Pour plus d’informations sur les assemblys disponibles pour chaque framework de Xamarin, reportez-vous au guide [Available Assemblies](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet est le gestionnaire de packages le plus répandu pour le développement .NET. La prise en charge de NuGet par Visual Studio pour Mac vous permet de rechercher des packages à ajouter à votre projet.

Pour cela, cliquez avec le bouton droit sur le dossier **Package** dans le panneau Solution et sélectionnez Ajouter des Packages.

Vous trouverez plus d’informations sur l’utilisation d’un package NuGet dans la procédure pas à pas [Inclusion d’un package NuGet dans votre projet](~/nuget-walkthrough.md).
