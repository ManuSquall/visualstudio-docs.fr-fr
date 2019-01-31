---
title: GenerateTrustInfo, tâche | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a476027333b648d175dbe54c487dd2081aecae7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978098"
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
 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)