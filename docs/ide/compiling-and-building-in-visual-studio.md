---
title: Compilation et génération
description: Découvrez comment utiliser la méthode de génération de l’IDE Visual Studio, la méthode de génération des outils en ligne de commande MSBuild, ou Azure Pipelines méthode de génération pour générer une application.
ms.custom: SEO-VS-2020
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac65fa9eaaf8e318e99e134957b335141f07577c
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136587"
---
# <a name="compile-and-build-in-visual-studio"></a>Compiler et générer dans Visual Studio

Pour une première présentation de la génération dans l’IDE, consultez [procédure pas à pas : génération d’une application](walkthrough-building-an-application.md).

Il existe plusieurs méthodes permettant de générer une application : l’environnement IDE Visual Studio, les outils en ligne de commande de MSBuild et Azure Pipelines :

| Méthode de génération | Avantages |
| --- |--- | --- |
| IDE |- Créer des builds immédiatement et les tester dans un débogueur.<br />- Exécuter des builds multiprocesseurs pour des projets C++ et C#.<br />- Personnaliser différents aspects du système de génération. |
| CMake | -Générer des projets à l’aide de l’outil CMake<br />-Utilisez le même système de génération sur les plateformes Linux et Windows. |
| Ligne de commande MSBuild| - Générer des projets sans installer Visual Studio.<br />- Exécuter des builds multiprocesseurs pour tous les types de projets.<br />- Personnaliser la plupart des éléments du système de génération.|
| Azure Pipelines | - Automatiser votre processus de génération dans un pipeline d’intégration continue/de livraison continue.<br />- Appliquer des tests automatisés avec chaque build.<br />- Utiliser des ressources cloud virtuellement illimitées pour les processus de génération.<br />- Modifier le flux de travail de la génération et créer des activités de génération pour effectuer des tâches fortement personnalisées.|

La documentation de cette section contient plus de détails sur le processus de génération avec l’IDE. Pour plus d’informations sur les autres méthodes, consultez [MSBuild](../msbuild/msbuild.md) et [Pipelines Azure](/azure/devops/pipelines/index?view=vsts&preserve-view=true), respectivement.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Compiler et générer dans Visual Studio pour Mac](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>Vue d’ensemble de la génération à partir de l’IDE

Quand vous créez un projet, Visual Studio crée des configurations de build par défaut pour le projet et la solution qui contient le projet.  Ces configurations définissent comment les solutions et les projets sont générés et déployés. En particulier, les configurations de projet sont uniques pour une plateforme cible (comme Windows ou Linux) et un type de build (comme Debug ou Release) donnés. Vous pouvez modifier ces configurations comme vous le souhaitez et aussi créer vos propres configurations selon vos besoins.

Pour une première présentation de la génération dans l’IDE, consultez [procédure pas à pas : génération d’une application](walkthrough-building-an-application.md).

Consultez ensuite [Génération et nettoyage des solutions et de projets dans Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) pour en savoir plus sur les personnalisations des différents aspects que vous pouvez apporter au processus. Les personnalisations portent notamment sur le [changement des répertoires de sortie](how-to-change-the-build-output-directory.md), la [spécification d’événements de build personnalisés](specifying-custom-build-events-in-visual-studio.md), la [gestion des dépendances du projet](how-to-create-and-remove-project-dependencies.md), la [gestion des fichiers journaux de génération](how-to-view-save-and-configure-build-log-files.md) et la [suppression des avertissements du compilateur](how-to-suppress-compiler-warnings.md).

À partir de là, vous pouvez explorer différentes autres tâches :
- [Présentation des configurations de build](understanding-build-configurations.md)
- [Présentation des plateformes de build](understanding-build-platforms.md)
- [Gérer les propriétés de projet et de solution](managing-project-and-solution-properties.md).
- Spécification des événements de build dans [C#](how-to-specify-build-events-csharp.md) et [Visual Basic](how-to-specify-build-events-visual-basic.md).
- [Définition des options de génération](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Générez plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="see-also"></a>Voir aussi

- [Génération (compilation) de projets de site web](/previous-versions/hwxa5aha(v=vs.140))
- [Compiler et générer (Visual Studio pour Mac)](/visualstudio/mac/compiling-and-building)
- [Projets CMake dans Visual Studio](/cpp/build/cmake-projects-in-visual-studio)