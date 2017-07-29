---
title: "RegisterAssembly, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 16
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: e1e6b68c59aa10204bd985b9bf8d17e8256936d5
ms.contentlocale: fr-fr
ms.lasthandoff: 05/30/2017

---
# <a name="registerassembly-task"></a>RegisterAssembly, tâche
Lit les métadonnées dans l’assembly spécifié et ajoute les entrées nécessaires au Registre, ce qui permet aux clients COM de créer des classes [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en toute transparence. Le comportement de cette tâche est similaire, mais pas identique, à celui de [Regasm.exe (outil Assembly Registration Tool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `RegisterAssembly`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Assemblies`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les assemblys à inscrire auprès de COM.|  
|`AssemblyListFile`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Contient des informations sur l’état entre la tâche `RegisterAssembly` et la tâche [UnregisterAssembly](../msbuild/unregisterassembly-task.md). Cela empêche la tâche `UnregisterAssembly` d’annuler l’inscription d’un assembly qui n’a pas pu s’inscrire dans la tâche `RegisterAssembly`.|  
|`CreateCodeBase`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, crée une entrée Codebase dans le Registre, qui spécifie le chemin de fichier d’un assembly qui n’est pas installé dans le Global Assembly Cache. Vous ne devez pas spécifier cette option si vous devez installer par la suite l'assembly que vous inscrivez dans le Global Assembly Cache.|  
|`TypeLibFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie la bibliothèque de types à générer à partir de l’assembly spécifié. La bibliothèque de types générée contient des définitions des types accessibles définis dans l’assembly. La bibliothèque de types est générée uniquement si l’une des conditions suivantes est remplie :<br /><br /> -   Il n’existe pas de bibliothèque de types de ce nom à cet emplacement.<br />-   Il existe une bibliothèque de types, mais elle est plus ancienne que l’assembly passé.<br /><br /> Si la bibliothèque de types est plus récente que l’assembly passé, une nouvelle bibliothèque n’est pas créée, mais l’assembly est quand même inscrit.<br /><br /> Si ce paramètre est spécifié, il doit avoir le même nombre d’éléments que le paramètre `Assemblies`, sinon la tâche échoue. Si aucune entrée n’est spécifiée, la tâche utilise par défaut le nom de l’assembly et remplace l’extension de l’élément par .tlb.|  
  
## <a name="remarks"></a>Remarques  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche `RegisterAssembly` pour inscrire l’assembly spécifié par la collection d’éléments `MyAssemblies`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches MSBuild](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
