---
title: AssignTargetPath, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a711c20198b117b53536f9b0fe043a468eb8a0b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930659"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath, tâche
Cette tâche accepte une liste de fichiers et ajoute des attributs `<TargetPath>` s’ils ne sont pas déjà spécifiés.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `AssignTargetPath` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`RootFolder`|Paramètre d’entrée `string` facultatif.<br /><br /> Contient le chemin du dossier qui contient les liens de cible.|  
|`Files`|Paramètre d’entrée <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste de fichiers entrante.|  
|`AssignedFiles`|Facultatif<br /><br /> Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Contient la liste de fichiers résultante.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant exécute la tâche `AssignTargetPath` pour configurer un projet.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)