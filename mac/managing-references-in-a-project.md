---
title: Gestion des références dans un projet
description: Cet article décrit comment gérer les références d’un projet dans Visual Studio pour Mac
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.topic: overview
ms.openlocfilehash: 41d49fe6b23818f3cb9de8dec72462d4b2029bb6
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493515"
---
# <a name="managing-references-in-a-project"></a>Gestion des références dans un projet

Visual Studio pour Mac fournit deux moyens d’ajouter des références supplémentaires à votre projet :

![Références de projets](media/projects-and-solutions-image10.png)

Celles-ci sont les suivantes :

* Références
* Packages NuGet (ajoutés via le dossier Packages)

Des références web et des références natives peuvent également être ajoutées à tout projet.

## <a name="assembly-references"></a>Références d’assembly

Chaque framework dans Xamarin est fourni avec plus d’une dizaine d’assemblys. Certains de ces packages d’assemblys ne sont pas référencés dans votre projet par défaut.

Pour modifier les packages référencés dans votre projet, utilisez la boîte de dialogue **Modifier les références** , que vous pouvez afficher en double-cliquant sur le dossier Références, ou en sélectionnant **Modifier les références** dans les actions de son menu contextuel :

![Boîte de dialogue Références d’assembly](media/projects-and-solutions-image11.png)

Pour plus d’informations sur les assemblys disponibles pour chaque framework de Xamarin, reportez-vous au guide [Available Assemblies](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet est le gestionnaire de packages le plus répandu pour le développement .NET. La prise en charge de NuGet par Visual Studio pour Mac vous permet de rechercher des packages à ajouter à votre projet.

Pour ce faire, cliquez avec le bouton droit sur le dossier du **package** dans la fenêtre de la solution, puis sélectionnez Ajouter des packages.

Vous trouverez plus d’informations sur l’utilisation d’un package NuGet dans la procédure pas à pas [Inclusion d’un package NuGet dans votre projet](nuget-walkthrough.md).

## <a name="see-also"></a>Voir aussi

- [Gérer les références (Visual Studio sur Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Ajout de références avec NuGet ou un kit SDK d’extension (Visual Studio sur Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)