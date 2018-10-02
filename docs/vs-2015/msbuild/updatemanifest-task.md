---
title: UpdateManifest, tâche | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 39bd26aacba67b8eb87fecdc46bc54f01e600dfe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501112"
---
# <a name="updatemanifest-task"></a>UpdateManifest, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [UpdateManifest, tâche](https://docs.microsoft.com/visualstudio/msbuild/updatemanifest-task).  
  
  
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



