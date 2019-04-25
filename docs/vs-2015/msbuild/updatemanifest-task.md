---
title: UpdateManifest, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e2ec8a0cd854a04c338add22c3f90daf0bf14ba
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656997"
---
# <a name="updatemanifest-task"></a>UpdateManifest, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Met à jour les propriétés sélectionnées dans un manifeste et signe à nouveau.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `UpdateManifest` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`ApplicationManifest`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le manifeste d’application.|  
|`ApplicationPath`|Paramètre `String` requis.<br /><br /> Spécifie le chemin du manifeste d’application.|  
|`InputManifest`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le manifeste à mettre à jour.|  
|`OutputManifest`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le manifeste qui contient les propriétés mises à jour.|  
  
## <a name="remarks"></a>Remarques  
 En plus des paramètres répertoriés dans le tableau, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Task, classe de base](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
