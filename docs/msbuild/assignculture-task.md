---
title: "AssignCulture Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, AssignCulture task"
  - "AssignCulture task [MSBuild]"
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# AssignCulture Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette tâche accepte une liste d'éléments qui peuvent contenir une chaîne d'identificateur de culture .NET valide dans leur nom de fichier et génère des éléments possédant une entrée de métadonnées appelée `Culture` qui contient l'identificateur de culture correspondant.  Par exemple, le nom de fichier Form1.fr\-fr.resx possède un identificateur de culture incorporé, « fr\-fr ». Cette tâche crée dès lors un élément portant le même nom de fichier avec l'entrée de métadonnées `Culture` correspondant à `fr-fr`.  La tâche génère également une liste de noms de fichiers dont la culture a été supprimée du nom.  
  
## Paramètres de la tâche  
 Le tableau suivant décrit les paramètres de la tâche `AssignCulture`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AssignedFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste des éléments reçus dans le paramètre `Files`, avec une entrée de métadonnées `Culture` ajoutée à chaque élément.<br /><br /> Si l'élément entrant du paramètre `Files` contient déjà une entrée de métadonnées `Culture`, l'entrée de métadonnées d'origine est utilisée.<br /><br /> La tâche assigne uniquement une entrée de métadonnées `Culture` si le nom de fichier contient un identificateur de culture valide.  L'identificateur de culture doit être spécifié entre les deux derniers points du nom de fichier.|  
|`AssignedFilesWithCulture`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient le sous\-ensemble d'éléments du paramètre `AssignedFiles` qui possèdent une entrée de métadonnées `Culture`.|  
|`AssignedFilesWithNoCulture`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient le sous\-ensemble d'éléments du paramètre `AssignedFiles` qui ne possèdent pas d'entrée de métadonnées `Culture`.|  
|`CultureNeutralAssignedFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la même liste d'éléments créés dans le paramètre `AssignedFiles`, mais dont la culture a été supprimée du nom de fichier.<br /><br /> La tâche supprime uniquement la culture du nom de fichier s'il s'agit d'un identificateur de culture valide.|  
|`Files`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie la liste des fichiers avec des noms de cultures incorporés auxquels assigner une culture.|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant exécute la tâche `AssignCulture` avec la collection d'éléments `ResourceFiles`.  
  
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
  
 Le tableau suivant décrit la valeur des éléments de sortie après l'exécution de la tâche.  Les métadonnées de l'élément sont affichées entre parenthèses après l'élément.  
  
|Collection d'éléments|Sommaire|  
|---------------------------|--------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` \(aucune métadonnée supplémentaire\)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` \(aucune métadonnée supplémentaire\)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (` \(aucune métadonnée supplémentaire\)|  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)