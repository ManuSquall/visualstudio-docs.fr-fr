---
title: Frameworks .NET ciblés
ms.date: 03/31/2020
ms.topic: overview
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b7c3c2b6b81f8f7793bda35c6b220e43caee9b5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770448"
---
# <a name="framework-targeting-overview"></a>Vue d’ensemble du ciblage des frameworks

Dans Visual Studio, vous pouvez spécifier la version de .NET que votre projet doit cibler. Le ciblage de framework permet de garantir que l’application utilise seulement les fonctionnalités disponibles dans la version du framework spécifiée. Pour qu’une application .NET Framework s’exécute sur un autre ordinateur, la version du framework ciblée par l’application doit être compatible avec la version du framework qui est installée sur l’ordinateur.

Une solution Visual Studio peut contenir des projets qui ciblent différentes versions de .NET.  Toutefois, Notez que vous ne pouvez créer que sur une seule version de .NET à l’aide de conditions de référence pour une génération unique ou pour générer de manière récursive différents binaires pour chaque version.  Pour plus d’informations sur les frameworks cibles, consultez [Frameworks cibles](/dotnet/standard/frameworks).

> [!TIP]
> Vous pouvez également cibler des applications pour différentes plateformes. Pour plus d’informations, consultez l’article [Multiciblage de MSBuild](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Fonctionnalités du ciblage du Framework

Le ciblage du Framework inclut les fonctionnalités suivantes :

- Quand vous ouvrez un projet qui cible une version antérieure du framework, Visual Studio peut le mettre à niveau automatiquement ou laisser la cible telle quelle.

- Quand vous créez un projet .NET Framework, vous pouvez spécifier la version du .NET Framework que vous voulez cibler.

- Vous pouvez [cibler plusieurs frameworks](/dotnet/standard/frameworks#how-to-specify-target-frameworks) dans un même projet.

- Vous pouvez cibler une version différente de .NET dans chacun des différents projets de la même solution.

- Vous pouvez changer la version de .NET ciblée par un projet existant.

   Quand vous changez la version de .NET ciblée par un projet, Visual Studio apporte les modifications nécessaires aux références et aux fichiers de configuration.

Quand vous travaillez sur un projet qui cible une version antérieure du framework, Visual Studio change dynamiquement l’environnement de développement, comme suit :

- Il filtre les éléments des boîtes de dialogue **Ajouter un nouvel élément**, **Ajouter une nouvelle référence** et **Ajouter une référence de service** de façon à omettre les choix qui ne sont pas disponibles dans la version ciblée.

- Il filtre les contrôles personnalisés de la **boîte à outils** pour supprimer ceux qui ne sont pas disponibles dans la version ciblée et pour afficher la version la plus récente quand plusieurs contrôles sont disponibles.

- Il filtre **IntelliSense** de façon à omettre les fonctionnalités du langage qui ne sont pas disponibles dans la version ciblée.

- Il filtre les propriétés de la fenêtre **Propriétés** de façon à omettre celles qui ne sont pas disponibles dans la version ciblée.

- Il filtre les options de menu de façon à omettre celles qui ne sont pas disponibles dans la version ciblée.

- Pour les builds, il utilise la version du compilateur et les options de compilateur appropriées pour la version ciblée.

> [!NOTE]
> - Le ciblage du Framework ne garantit pas que votre application s’exécutera correctement. Vous devez tester votre application pour vous assurer qu’elle s’exécute sur la version ciblée.
> - Vous ne pouvez pas cibler des versions du framework antérieures à .NET Framework 2.0.

## <a name="select-a-target-framework-version"></a>Sélectionner une version du framework cible

Quand vous créez un projet .NET Framework, sélectionnez la version du .NET Framework cible après avoir sélectionné un modèle de projet. La liste des frameworks disponibles inclut les versions de framework installées applicables au type de modèle sélectionné. Pour les modèles de projet qui ne sont pas basés sur le .NET Framework, par exemple les modèles .NET Core, la liste déroulante **Framework** n’apparaît pas.

::: moniker range="vs-2017"

![Liste déroulante Framework dans Visual Studio 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Liste déroulante Framework dans Visual Studio 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="change-the-target-framework"></a>Changer la version cible du framework cible

Dans un projet Visual Basic, C# ou F# existant, vous pouvez changer la version de .NET cible dans la boîte de dialogue Propriétés du projet. Pour plus d’informations sur le changement de la version cible des projets C++, consultez [Guide pratique pour modifier le framework cible et l’ensemble d’outils de plateforme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset) à la place.

1. Dans l’**Explorateur de solutions**, ouvrez le menu du projet que vous souhaitez modifier avec un clic droit, puis choisissez **Propriétés**.

1. Dans la colonne de gauche de la fenêtre **Propriétés** , choisissez l’onglet **application** .

   ![Onglet Application des propriétés du projet](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > Après avoir créé une application UWP, vous ne pouvez pas changer la version ciblée de Windows ou de .NET.

1. Dans la liste **Framework cible**, choisissez la version que vous souhaitez.

1. Dans la boîte de dialogue de vérification qui apparaît, choisissez le bouton **Oui**.

   Le projet est alors déchargé. Quand il se recharge, il cible la version de .NET que vous venez de choisir.

> [!NOTE]
> Si votre code contient des références à une autre version de .NET que celle que vous avez ciblée, des messages d’erreur peuvent apparaître quand vous compilez ou que vous exécutez le code. Pour résoudre ces erreurs, modifiez les références. Consultez [Résoudre les problèmes liés aux erreurs de ciblage de .NET](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

> [!TIP]
> En fonction du framework cible, elle peut être représentée comme suit dans le fichier projet :
>
> - Pour une application .NET Core : `<TargetFramework>netcoreapp2.1</TargetFramework>`
> - Pour une application .NET Standard : `<TargetFramework>netstandard2.0</TargetFramework>`
> - Pour une application .NET Framework : `<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>Résoudre des références d’assembly système et utilisateur

Pour cibler une version de .NET, vous devez d’abord installer les références d’assembly appropriées. Vous pouvez télécharger des packs de développeur pour différentes versions de .NET à partir de la page de [Téléchargements .NET](https://www.microsoft.com/net/download/windows).

Pour les projets .NET Framework, la boîte de dialogue **Ajouter une référence** désactive les assemblys système qui n’appartiennent pas à la version du .NET Framework cible, de façon à ce qu’ils ne puissent pas être ajoutés à un projet par inadvertance. (Les assemblys système sont des fichiers *. dll* inclus dans une version .NET Framework.) Les références qui appartiennent à une version de Framework supérieure à la version ciblée ne seront pas résolues, et les contrôles qui dépendent d’une telle référence ne peuvent pas être ajoutés. Si vous voulez activer une telle référence, réinitialisez la cible du .NET Framework du projet sur une cible qui inclut la référence.

Pour plus d’informations sur les références d’assembly, consultez [Résoudre les assemblys au moment du design](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Activer LINQ

Quand vous ciblez .NET Framework 3.5 ou ultérieur, une référence à **System.Core** et une importation au niveau du projet pour <xref:System.Linq> (en Visual Basic uniquement) sont automatiquement ajoutées. Si vous voulez utiliser des fonctionnalités LINQ, vous devez également activer `Option Infer` (en Visual Basic uniquement). La référence et l’importation sont automatiquement supprimées si vous faites passer la version du .NET Framework à une version antérieure. Pour plus d’informations, consultez [Utiliser LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Voir aussi

- [Frameworks cibles](/dotnet/standard/frameworks)
- [Multiciblage (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Comment : modifier la version cible de .NET Framework et l’ensemble d’outils de plateforme (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
