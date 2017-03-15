---
title: "CreateVisualBasicManifestResourceName, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
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
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 5edc245c56e198b974f9f406c42a4e0340f266d8
ms.lasthandoff: 02/22/2017

---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName, tâche
Crée un nom de manifeste de style [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] à partir d’un nom de fichier .resx donné ou d’une autre ressource.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau suivant décrit les paramètres de la [tâche CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md).  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`ManifestResourceNames`|Paramètre de sortie en lecture seule `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Noms des manifestes résultants.|  
|`ResourceFiles`|Paramètre `String` requis.<br /><br /> Nom du fichier de ressources à partir duquel créer le nom du manifeste [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].|  
|`RootNamespace`|Paramètre `String` facultatif.<br /><br /> Espace de noms racine du fichier de ressources, qui provient généralement du fichier projet. Peut avoir la valeur `null`.|  
|`PrependCultureAsDirectory`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, le nom de culture est ajouté comme nom de répertoire juste avant le nom de ressource de manifeste. La valeur par défaut est `true`.|  
|`ResourceFilesWithManifestResourceNames`|Paramètre de sortie `String` en lecture seule facultatif.<br /><br /> Retourne le nom du fichier de ressources qui inclut maintenant le nom de ressource de manifeste.|  
  
## <a name="remarks"></a>Notes  
 La [tâche CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) détermine le nom de ressource de manifeste approprié à assigner à un fichier .resx ou autre fichier de ressources donné. La tâche fournit un nom logique à un fichier de ressources, puis l’attache à un paramètre de sortie en tant que métadonnées.  
  
 Outre les paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle-même de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez l’article [TaskExtension Base Class (Classe de base TaskExtension)](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches MSBuild](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
