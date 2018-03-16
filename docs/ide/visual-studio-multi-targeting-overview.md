---
title: Ciblage du .NET Framework dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 02/06/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e78f77993c510a223056696c0beac27147d18d5a
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="visual-studio-multi-targeting-overview"></a>Vue d’ensemble du multiciblage Visual Studio

Dans Visual Studio, vous pouvez spécifier la version ou le profil du .NET Framework que votre projet doit cibler. Pour qu'une application s'exécute sur un autre ordinateur, la version du Framework ciblée par l'application doit être compatible avec la version du Framework qui est installée sur l'ordinateur.

Vous pouvez également créer une solution contenant des projets qui ciblent différentes versions du Framework. Le ciblage du Framework permet de s’assurer que l’application utilise uniquement les fonctionnalités disponibles dans la version spécifiée du Framework.

> [!TIP]
> Vous pouvez également cibler des applications pour différentes plateformes. Pour plus d’informations, consultez l’article [Multiciblage de MSBuild](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Fonctionnalités du ciblage du Framework

Le ciblage du Framework inclut les fonctionnalités suivantes :

- Quand vous ouvrez un projet qui cible une version antérieure du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio peut automatiquement le mettre à niveau ou laisser la cible telle quelle.

- Quand vous créez un projet, vous pouvez spécifier la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que vous voulez cibler.

- Vous pouvez modifier la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que cible un projet existant.

- Vous pouvez cibler une version différente du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dans chacun des différents projets de la même solution.

- Quand vous modifiez la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ciblée par un projet, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] applique les modifications obligatoires aux références et aux fichiers de configuration.

Quand vous travaillez sur un projet qui cible une version antérieure du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio change dynamiquement l’environnement de développement, de la façon suivante :

- Il filtre les éléments des boîtes de dialogue **Ajouter un nouvel élément**, **Ajouter une nouvelle référence** et **Ajouter une référence de service** de façon à omettre les choix qui ne sont pas disponibles dans la version ciblée.

- Il filtre les contrôles personnalisés de la **boîte à outils** pour supprimer ceux qui ne sont pas disponibles dans la version ciblée et pour afficher la version la plus récente quand plusieurs contrôles sont disponibles.

- Il filtre IntelliSense de façon à omettre les fonctionnalités de langage qui ne sont pas disponibles dans la version ciblée.

- Il filtre les propriétés de la fenêtre **Propriétés** de façon à omettre celles qui ne sont pas disponibles dans la version ciblée.

- Il filtre les options de menu de façon à omettre celles qui ne sont pas disponibles dans la version ciblée.

- Pour les builds, il utilise la version du compilateur et les options de compilateur appropriées pour la version ciblée.

> [!NOTE]
> Le ciblage du Framework ne garantit pas que votre application s’exécutera correctement. Vous devez tester votre application pour vous assurer qu’elle s’exécute sur la version ciblée. Vous ne pouvez pas cibler des versions du Framework antérieures à .NET Framework 2.0.

## <a name="selecting-a-target-framework-version"></a>Sélection d’une version du Framework cible

Quand vous créez un projet, sélectionnez la version du .NET Framework cible dans la boîte de dialogue **Nouveau projet**. La liste des frameworks disponibles inclut les versions de framework installées applicables au type de modèle sélectionné. Pour les types de modèles qui n’ont pas besoin de .NET Framework, par exemple des modèles .NET Core, la liste déroulante **Framework** est masquée.

![Liste déroulante Framework dans la boîte de dialogue Nouveau projet](media/vside-newproject-framework.png)

Dans un projet existant, vous pouvez modifier la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] cible dans la boîte de dialogue Propriétés du projet. Pour plus d’informations, consultez [Guide pratique pour cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolving-system-and-user-assembly-references"></a>Résolution des références système et d’assembly utilisateur

Pour cibler une version du .Net Framework, vous devez d’abord installer les références d’assembly appropriées. Vous pouvez télécharger des packs du développeur pour différentes versions du .NET Framework à partir de la page de [Téléchargements .NET](https://www.microsoft.com/net/download/windows).

La boîte de dialogue **Ajouter une référence** désactive les assemblys système qui ne se rapportent pas à la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] cible afin qu’ils ne puissent pas être ajoutés à un projet par inadvertance. (Les assemblys système sont des fichiers .dll inclus dans une version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].) Les références qui appartiennent à une version du Framework ultérieure à la version ciblée ne seront pas résolues, et les contrôles qui dépendent d’une telle référence ne peuvent pas être ajoutés. Si vous voulez activer une telle référence, réinitialisez la cible du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] du projet sur une cible qui inclut la référence.  Pour plus d’informations, consultez [Guide pratique pour cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Pour plus d’informations sur les références d’assembly, consultez [Résolution d’assemblys au moment du design](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enabling-linq"></a>Activation de LINQ

Quand vous ciblez .NET Framework 3.5 ou une version ultérieure, une référence à System.Core et une importation au niveau du projet pour System.Linq (en Visual Basic uniquement) sont automatiquement ajoutées. Si vous voulez utiliser les fonctionnalités LINQ, vous devez également activer Option Infer (en Visual Basic uniquement). La référence et l’importation sont automatiquement supprimées si vous faites passer la version du .NET Framework à une version antérieure. Pour plus d’informations, consultez [Utilisation de LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Voir aussi

[Multiciblage (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)  
[Guide pratique pour modifier le framework cible et l’ensemble d’outils de plateforme (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)  
[Compatibilité de la plateforme et configuration requise](http://www.microsoft.com/visualstudio/eng/products/compatibility)
