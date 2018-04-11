---
title: UnregisterAssembly, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
caps.latest.revision: 21
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1f859137722c2715f81276a02a311dcbb40ec06e
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2018
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly, tâche
Désinscrit les assemblys spécifiés dans le cadre de COM Interop. Exécute l’opération inverse de la [tâche RegisterAssembly](../msbuild/registerassembly-task.md).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `UnregisterAssembly` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Assemblies`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les assemblys à désinscrire.|  
|`AssemblyListFile`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Contient des informations relatives à l’état entre la tâche `RegisterAssembly` et la tâche `UnregisterAssembly`. La tâche ne peut donc pas tenter de désinscrire un assembly dont l’inscription dans la tâche `RegisterAssembly` a échoué.<br /><br /> Si ce paramètre est spécifié, les paramètres `Assemblies` et `TypeLibFiles` sont ignorés.|  
|`TypeLibFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Désinscrit la bibliothèque de types spécifiée de l’assembly indiqué. **Remarque :** Ce paramètre est nécessaire uniquement si le nom de fichier de la bibliothèque de types est différent de celui de l’assembly.|  
  
## <a name="remarks"></a>Notes  
 L’assembly ne doit pas forcément exister pour que cette tâche s’exécute correctement. Si vous tentez de désinscrire un assembly qui n’existe pas, la tâche réussit avec un avertissement. En effet, la tâche a pour but de supprimer l’inscription de l’assembly du Registre. Si l’assembly n’existe pas, il n’est pas dans le Registre, et par conséquent, la tâche réussit.  
  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension>, qui elle-même hérite de la classe <xref:System.MarshalByRefObject>. La classe `MarshalByRefObject` fournit la même fonctionnalité que la classe <xref:Microsoft.Build.Utilities.Task>, mais peut être instanciée dans son propre domaine d’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche `UnregisterAssembly` pour désinscrire l’assembly dans le chemin spécifié par les propriétés `OutputPath` et `FileName`, s’il existe.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <OutputPath>\Output\</OutputPath>  
        <FileName>MyFile.dll</FileName>  
    </PropertyGroup>  
    <Target Name="UnregisterAssemblies">  
        <UnregisterAssembly  
            Condition="Exists('$(OutputPath)$(FileName)')"  
            Assemblies="$(OutputPath)$(FileName)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [RegisterAssembly, tâche](../msbuild/registerassembly-task.md)   
 [Tâches MSBuild](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)