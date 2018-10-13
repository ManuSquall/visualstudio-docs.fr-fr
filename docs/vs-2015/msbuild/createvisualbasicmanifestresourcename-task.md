---
title: CreateVisualBasicManifestResourceName, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43cd2b3c4516479f7cf97182d2a66570066e891a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302820"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Crée un nom de manifeste de style [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] à partir d’un nom de fichier .resx donné ou d’une autre ressource.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau suivant décrit les paramètres de la [tâche CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md).  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`ManifestResourceNames`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> `[]` en lecture seule.<br /><br /> Noms des manifestes résultants.|  
|`ResourceFiles`|Paramètre `String` requis.<br /><br /> Nom du fichier de ressources à partir duquel créer le nom du manifeste [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].|  
|`RootNamespace`|Paramètre `String` facultatif.<br /><br /> Espace de noms racine du fichier de ressources, qui provient généralement du fichier projet. Peut avoir la valeur `null`.|  
|`PrependCultureAsDirectory`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, le nom de culture est ajouté comme nom de répertoire juste avant le nom de ressource de manifeste. La valeur par défaut est `true`.|  
|`ResourceFilesWithManifestResourceNames`|Paramètre de sortie `String` en lecture seule facultatif.<br /><br /> Retourne le nom du fichier de ressources qui inclut maintenant le nom de ressource de manifeste.|  
  
## <a name="remarks"></a>Notes  
 La [tâche CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) détermine le nom de ressource de manifeste approprié à assigner à un fichier .resx ou autre fichier de ressources donné. La tâche fournit un nom logique à un fichier de ressources, puis l’attache à un paramètre de sortie en tant que métadonnées.  
  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)



