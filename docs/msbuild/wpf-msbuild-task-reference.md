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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630845"
---
# <a name="wpf-msbuild-task-reference"></a>Informations de référence sur les tâches MSBuild WPF

Le processus de génération de Windows Presentation Foundation (WPF) étend Microsoft Build Engine (MSBuild) avec un ensemble de tâches de génération supplémentaires, notamment des tâches pour compiler le balisage et traiter les ressources.

## <a name="in-this-section"></a>Contenu de cette section

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Classifie un ensemble de ressources sources comme devant être incorporées dans un assembly. Si une ressource n’est pas localisable, elle est incorporée dans l’assembly principal de l’application ; autrement, elle est incorporée dans un assembly satellite.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Génère un assembly si au moins une page XAML d’un projet fait référence à un type déclaré localement dans ce projet. L’assembly généré est supprimé une fois le processus de génération terminé, ou en cas d’échec du processus de génération.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Retourne le répertoire du runtime d' .NET Framework actuel.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Convertit des fichiers projet XAML non localisables au format binaire compilé.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Effectue une deuxième passe de compilation du balisage sur des fichiers XAML qui référencent des types dans le même projet.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Fusionne les attributs de localisation et les commentaires d’un ou plusieurs fichiers de format binaire XAML dans un seul fichier pour l’assembly entier.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Incorpore une ou plusieurs ressources ( *. jpg*, *. ico*, *. bmp*, XAML au format binaire et d’autres types d’extensions) dans un fichier *. Resources* .

- [UidManager](../msbuild/uidmanager-task.md)

 Vérifie, met à jour ou supprime les identificateurs uniques (UID), afin de localiser tous les éléments XAML inclus dans les fichiers XAML source.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Ajoute l’élément **\<HostInBrowser/>** au manifeste d’application ( *\<ProjectName >. exe. manifest*) lors de la génération d’un projet d’application de navigateur XAML (XBAP).

## <a name="see-also"></a>Voir aussi

- [MSBuild](../msbuild/msbuild.md)