---
title: AssignCulture, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c35d949f2d3cf3924a63ce6db0e596af1fccddbd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235649"
---
# <a name="assignculture-task"></a>AssignCulture, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Cette tâche accepte une liste d’éléments dont le nom de fichier peut contenir une chaîne d’identificateur de culture .NET valide. De plus, cette tâche génère des éléments dont les métadonnées nommées `Culture` contiennent l’identificateur de culture correspondant. Par exemple, le nom de fichier Form1.fr-fr.resx comprend l’identificateur de culture incorporé « fr-fr ». Cette tâche génère donc un élément qui porte le même nom de fichier et dont les métadonnées `Culture` sont égales à `fr-fr`. La tâche génère également une liste de noms de fichiers desquels la culture a été supprimée.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `AssignCulture`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AssignedFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste des éléments reçus par le paramètre `Files`, avec une entrée de métadonnées `Culture` ajoutée à chaque élément.<br /><br /> Si l’élément reçu par le paramètre `Files` contient déjà une entrée de métadonnées `Culture`, l’entrée de métadonnées d’origine est utilisée.<br /><br /> La tâche attribue une entrée de métadonnées `Culture` uniquement si le nom de fichier contient un identificateur de culture valide. L’identificateur de culture doit être placé entre les deux derniers points du nom de fichier.|  
|`AssignedFilesWithCulture`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient le sous-ensemble d’éléments du paramètre `AssignedFiles` qui ont une entrée de métadonnées `Culture`.|  
|`AssignedFilesWithNoCulture`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient le sous-ensemble d’éléments du paramètre `AssignedFiles` qui n’ont pas d’entrée de métadonnées `Culture`.|  
|`CultureNeutralAssignedFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la même liste d’éléments que celle qui est produite dans le paramètre `AssignedFiles`, mais sans la culture dans le nom de fichier.<br /><br /> La tâche supprime la culture du nom de fichier uniquement si l’identificateur de culture est valide.|  
|`Files`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie la liste des fichiers avec des noms de culture incorporés auxquels affecter une culture.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant exécute la tâche `AssignCulture` avec la collection d’éléments `ResourceFiles`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 Le tableau suivant décrit la valeur des éléments de sortie après l’exécution de la tâche. Les métadonnées de l’élément sont affichées entre parenthèses après l’élément.  
  
|Collection d'éléments.|Sommaire|  
|---------------------|--------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` (aucune métadonnée supplémentaire)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` (aucune métadonnée supplémentaire)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (` (aucune métadonnée supplémentaire)|  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)



