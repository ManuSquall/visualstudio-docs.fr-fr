---
title: GenerateTrustInfo, tâche | Microsoft Docs
description: Utilisez la tâche MSBuild GenerateTrustInfo pour générer l’approbation d’application à partir du manifeste de base et des paramètres TargetZone et ExcludedPermissions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 831f6fa76ba3d6cfdebbb6b850862155ad280641
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914726"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo (tâche)

Génère le niveau de confiance de l’application à partir du manifeste de base, ainsi que des paramètres `TargetZone` et `ExcludedPermissions`.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `GenerateTrustInfo` .

|Paramètre|Description|
|---------------|-----------------|
|`ApplicationDependencies`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les assemblys dépendants.|
|`BaseManifest`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le manifeste de base à partir duquel l’approbation d’application doit être générée.|
|`ExcludedPermissions`|Paramètre `String` facultatif.<br /><br /> Spécifie la ou les valeurs d’autorisation (séparées par un point-virgule) à exclure du jeu d’autorisations par défaut de la zone.|
|`TargetZone`|Paramètre `String` facultatif.<br /><br /> Spécifie un jeu d’autorisations de zone par défaut, obtenu à partir de la stratégie de l’ordinateur.|
|`TrustInfoFile`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> obligatoire.<br /><br /> Spécifie le fichier qui contient les informations d’approbation de sécurité de l’application.|

## <a name="remarks"></a>Notes

 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)