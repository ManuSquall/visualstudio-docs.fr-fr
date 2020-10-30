---
title: ResolveNativeReference, tâche | Microsoft Docs
description: Découvrez comment MSBuild utilise la tâche ResolveNativeReference, pour résoudre les références natives en implémentant la classe Microsoft. Build. Tasks. ResolveNativeReference,.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad9f5c85a3a295971a5f80fcb994c382346d9af3
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048547"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference (tâche)

Résout des références natives. Implémente la classe <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Cette classe prend en charge l’infrastructure .NET Framework et n’est pas destinée à être directement utilisée à partir de votre code.

## <a name="task-parameters"></a>Paramètres de tâche

 Le tableau ci-dessous décrit les paramètres de la tâche `ResolveNativeReference` .

|Paramètre|Description|
|---------------|-----------------|
|`AdditionalSearchPaths`|Paramètre <xref:System.String?displayProperty=fullName>`[]` obligatoire.<br /><br /> Obtient ou définit les chemins de recherche pour la résolution des identités d’assembly des références natives.|
|`ContainedComComponents`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les composants COM de l’assembly natif.|
|`ContainedLooseEtcFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les fichiers *etc* libres listés dans le manifeste natif.|
|`ContainedLooseTlbFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les fichiers *. tlb* libres de l’assembly natif.|
|`ContainedPrerequisiteAssemblies`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les assemblys qui doivent être présents pour permettre l’utilisation du manifeste.|
|`ContainedTypeLibraries`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les bibliothèques de types de l’assembly natif.|
|`ContainingReferenceFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les fichiers de référence.|
|`NativeReferences`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Obtient ou définit les références d’assemblys natifs Win32.|

## <a name="remarks"></a>Remarques

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
