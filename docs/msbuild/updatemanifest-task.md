---
title: UpdateManifest, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bc52232d8917835883c8390a24cb049b04fed94
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31572515"
---
# <a name="updatemanifest-task"></a>UpdateManifest, tâche
Met à jour les propriétés sélectionnées dans un manifeste et signe à nouveau.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `UpdateManifest` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`ApplicationManifest`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le manifeste d’application.|  
|`ApplicationPath`|Paramètre `String` requis.<br /><br /> Spécifie le chemin du manifeste d’application.|  
|`InputManifest`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le manifeste à mettre à jour.|  
|`OutputManifest`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le manifeste qui contient les propriétés mises à jour.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres répertoriés dans le tableau, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Task, classe de base](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)