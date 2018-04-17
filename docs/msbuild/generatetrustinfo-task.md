---
title: GenerateTrustInfo, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 4
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 35b31cbf81f1f740ca66a05b05e384adbddf397b
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2018
---
# <a name="generatetrustinfo-task"></a>Tâche GenerateTrustInfo
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
 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)