---
title: FindAppConfigFile, tâche | Microsoft Docs
description: Apprenez à utiliser la tâche MSBuild FindAppConfigFile pour rechercher le fichier app.config, le cas échéant, dans les listes fournies.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ff26ee3505671d29df610278d701803b816d30f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877133"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile (tâche)

Recherche le fichier *app.config* , le cas échéant, dans les listes fournies.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `FindAppConfigFile` .

|Paramètre|Description|
|---------------|-----------------|
|`AppConfigFile`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie le premier élément correspondant trouvé dans la liste, le cas échéant.|
|`PrimaryList`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie la liste principale dans laquelle effectuer les recherches.|
|`SecondaryList`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie la liste secondaire dans laquelle effectuer les recherches.|
|`TargetPath`|Paramètre `String` requis.<br /><br /> Spécifie la valeur à ajouter en tant que métadonnées.|

## <a name="remarks"></a>Remarques

 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
