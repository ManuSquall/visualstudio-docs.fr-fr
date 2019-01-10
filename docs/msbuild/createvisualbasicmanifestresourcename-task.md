---
title: CreateVisualBasicManifestResourceName, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 948b27aa9e2b800929d9f507535aee1395d45344
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871224"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName (tâche)
Crée un nom de manifeste de style [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] à partir d’un nom de fichier *.resx* donné ou d’une autre ressource.  

## <a name="parameters"></a>Paramètres  
 Le tableau suivant décrit les paramètres de la [tâche CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md).  


| Paramètre | Description |
| - | - |
| `ManifestResourceNames` | Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> `[]` en lecture seule.<br /><br /> Noms des manifestes résultants. |
| `ResourceFiles` | Paramètre `String` requis.<br /><br /> Nom du fichier de ressources à partir duquel créer le nom du manifeste [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. |
| `RootNamespace` | Paramètre `String` facultatif.<br /><br /> Espace de noms racine du fichier de ressources, qui provient généralement du fichier projet. Peut avoir la valeur `null`. |
| `PrependCultureAsDirectory` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, le nom de culture est ajouté comme nom de répertoire juste avant le nom de ressource de manifeste. La valeur par défaut est `true`. |
| `ResourceFilesWithManifestResourceNames` | Paramètre de sortie `String` en lecture seule facultatif.<br /><br /> Retourne le nom du fichier de ressources qui inclut maintenant le nom de ressource de manifeste. |

## <a name="remarks"></a>Notes  
 La [tâche CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) détermine le nom de ressource de manifeste approprié à assigner à un fichier *.resx* ou autre fichier de ressources donné. La tâche fournit un nom logique à un fichier de ressources, puis l’attache à un paramètre de sortie en tant que métadonnées.  

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).  

## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)