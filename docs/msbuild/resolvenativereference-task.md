---
title: ResolveNativeReference, tâche | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f18549fece2db8a4a758dee17f6b4b1283d97e4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617754"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference (tâche)
Résout des références natives. Implémente la classe <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Cette classe prend en charge l’infrastructure .NET Framework et n’est pas destinée à être directement utilisée à partir de votre code.

## <a name="task-parameters"></a>Paramètres de tâche
 Le tableau ci-dessous décrit les paramètres de la tâche `ResolveNativeReference` .

|Paramètre|Description|
|---------------|-----------------|
|`AdditionalSearchPaths`|Paramètre <xref:System.String?displayProperty=fullName>`[]` obligatoire.<br /><br /> Obtient ou définit les chemins de recherche pour la résolution des identités d’assembly des références natives.|
|`ContainedComComponents`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les composants COM de l’assembly natif.|
|`ContainedLooseEtcFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les fichiers *Etc libres* répertoriés dans le manifeste natif.|
|`ContainedLooseTlbFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les fichiers *.tlb* libres de l’assembly natif.|
|`ContainedPrerequisiteAssemblies`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les assemblys qui doivent être présents pour permettre l’utilisation du manifeste.|
|`ContainedTypeLibraries`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les bibliothèques de types de l’assembly natif.|
|`ContainingReferenceFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les fichiers de référence.|
|`NativeReferences`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Obtient ou définit les références d’assemblys natifs Win32.|

## <a name="remarks"></a>Remarques
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Voir aussi
- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)