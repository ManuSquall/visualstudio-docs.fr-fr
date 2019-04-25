---
title: Informations de référence sur les tâches MSBuild WPF | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 121c3da6d3e2609c1a271177e089e0f38a0d89fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778292"
---
# <a name="wpf-msbuild-task-reference"></a>Informations de référence sur les tâches MSBuild WPF
Le processus de génération de Windows Presentation Foundation (WPF) étend Microsoft Build Engine (MSBuild) avec un ensemble de tâches de génération supplémentaires, notamment des tâches pour compiler le balisage et traiter les ressources.

## <a name="in-this-section"></a>Dans cette section
- [FileClassifier](../msbuild/fileclassifier-task.md)

 Classifie un ensemble de ressources sources comme devant être incorporées dans un assembly. Si une ressource n’est pas localisable, elle est incorporée dans l’assembly principal de l’application ; autrement, elle est incorporée dans un assembly satellite.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Génère un assembly si au moins une page [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] dans un projet référence un type déclaré localement dans ce projet. L’assembly généré est supprimé une fois le processus de génération terminé, ou en cas d’échec du processus de génération.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Retourne le répertoire du runtime [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] actif.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Convertit des fichiers projet [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] non localisables au format binaire compilé.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Effectue la première passe de compilation du balisage sur les fichiers [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] qui référencent des types dans le même projet.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Fusionne les attributs de localisation et les commentaires d’un ou plusieurs fichiers binaires [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] en un seul fichier pour tout l’assembly.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Incorpore une ou plusieurs ressources (*.jpg*, *.ico*, *.bmp*, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] au format binaire et d’autres types d’extensions) dans un fichier *.resources*.

- [UidManager](../msbuild/uidmanager-task.md)

 Vérifie, met à jour ou supprime les identificateurs uniques (UID) pour localiser tous les éléments [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] inclus dans les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sources.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Ajoute l’élément **\<hostInBrowser />** au manifeste de l’application (*\<nom_proket>.exe.manifest*) lors de la génération d’un projet [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].

## <a name="see-also"></a>Voir aussi
- [MSBuild](../msbuild/msbuild.md)