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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70d994e32b717ff566a2e38acee732c7525d1bb0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630845"
---
# <a name="wpf-msbuild-task-reference"></a>Informations de référence sur les tâches MSBuild WPF

Le processus de génération de Windows Presentation Foundation (WPF) étend Microsoft Build Engine (MSBuild) avec un ensemble de tâches de génération supplémentaires, notamment des tâches pour compiler le balisage et traiter les ressources.

## <a name="in-this-section"></a>Contenu de cette section

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Classifie un ensemble de ressources sources comme devant être incorporées dans un assembly. Si une ressource n’est pas localisable, elle est incorporée dans l’assembly principal de l’application ; autrement, elle est incorporée dans un assembly satellite.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Génère un assemblage si au moins une page XAML dans un projet fait référence à un type qui est déclaré localement dans ce projet. L’assembly généré est supprimé une fois le processus de génération terminé, ou en cas d’échec du processus de génération.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Retourne le répertoire de l’heure d’exécution actuelle .NET Framework.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Convertit les fichiers de projet XAML non localisables en format binaire compilé.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Effectue la compilation de balisage de deuxième passage sur les fichiers XAML qui font référence aux types dans le même projet.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Fusionne les attributs de localisation et les commentaires d’un ou plusieurs fichiers de format binaire XAML en un seul fichier pour l’ensemble de l’assemblage.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Embeds une ou plusieurs ressources (*.jpg*, *.ico*, *.bmp*, XAML en format binaire, et d’autres types d’extension) dans un fichier *.resources.*

- [UidManager](../msbuild/uidmanager-task.md)

 Vérifie, met à jour ou supprime des identifiants uniques (UIM), afin de localiser tous les éléments XAML qui sont inclus dans les fichiers source XAML.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Ajoute ** \<l’élément hostInBrowser />** au manifeste de l’application*\<(nom de projet>.exe.manifest*) lorsqu’un projet d’application de navigateur XAML (XBAP) est construit.

## <a name="see-also"></a>Voir aussi

- [MSBuild](../msbuild/msbuild.md)