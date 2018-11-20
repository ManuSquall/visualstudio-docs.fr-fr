---
title: Gestion des références dans un projet
description: Cet article décrit comment gérer les références d’un projet dans Visual Studio pour Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: 54e07d3c170859405ef584b884547dad335788f3
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295278"
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

Pour modifier les packages référencés dans votre projet, utilisez la boîte de dialogue **Modifier les références**, que vous pouvez afficher en double-cliquant sur le dossier Références, ou en sélectionnant **Modifier les références** dans les actions de son menu contextuel :

![Boîte de dialogue Références d’assembly](media/projects-and-solutions-image11.png)

Pour plus d’informations sur les assemblys disponibles pour chaque framework de Xamarin, reportez-vous au guide [Available Assemblies](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet est le gestionnaire de packages le plus répandu pour le développement .NET. La prise en charge de NuGet par Visual Studio pour Mac vous permet de rechercher des packages à ajouter à votre projet.

Pour cela, cliquez avec le bouton droit sur le dossier **Package** dans le panneau Solution et sélectionnez Ajouter des Packages.

Vous trouverez plus d’informations sur l’utilisation d’un package NuGet dans la procédure pas à pas [Inclusion d’un package NuGet dans votre projet](nuget-walkthrough.md).

## <a name="see-also"></a>Voir aussi

- [Gérer les références (Visual Studio sur Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Ajout de références avec NuGet ou un kit SDK d’extension (Visual Studio sur Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)