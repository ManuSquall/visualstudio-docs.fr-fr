---
title: RegisterAssembly, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 488ae44a89c203b70e6c8e635d99eb699349156e
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747323"
---
# <a name="registerassembly-task"></a>RegisterAssembly (tâche)
Lit les métadonnées dans l’assembly spécifié et ajoute les entrées nécessaires au Registre, ce qui permet aux clients COM de créer des classes .NET Framework de façon transparente. Le comportement de cette tâche est similaire, mais pas identique, à celui de [Regasm.exe (outil d’inscription d’assemblys)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool).

## <a name="parameters"></a>Paramètres
 Le tableau ci-dessous décrit les paramètres de la tâche `RegisterAssembly` .

|Paramètre|Description|
|---------------|-----------------|
|`Assemblies`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les assemblys à inscrire auprès de COM.|
|`AssemblyListFile`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Contient des informations sur l’état entre la tâche `RegisterAssembly` et la tâche [UnregisterAssembly](../msbuild/unregisterassembly-task.md). La tâche `UnregisterAssembly` ne peut donc pas tenter de désinscrire un assembly dont l’inscription dans la tâche `RegisterAssembly` a échoué.|
|`CreateCodeBase`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, crée une entrée Codebase dans le Registre, qui spécifie le chemin de fichier d’un assembly qui n’est pas installé dans le Global Assembly Cache. Vous ne devez pas spécifier cette option si vous devez installer par la suite l'assembly que vous inscrivez dans le Global Assembly Cache.|
|`TypeLibFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie la bibliothèque de types à générer à partir de l’assembly spécifié. La bibliothèque de types générée contient des définitions des types accessibles définis dans l’assembly. La bibliothèque de types n’est générée que si l’une des conditions suivantes est remplie :<br /><br /> -   Il n’existe pas de bibliothèque de types de ce nom à cet emplacement.<br />-   Il existe une bibliothèque de types, mais elle est plus ancienne que l’assembly passé.<br /><br /> Si la bibliothèque de types est plus récente que l’assembly passé, il n’en est pas créé de nouvelle, mais l’assembly est quand même inscrit.<br /><br /> Si ce paramètre est spécifié, il doit avoir le même nombre d’éléments que le paramètre `Assemblies`, sinon la tâche échoue. Si aucune entrée n’est spécifiée, la tâche utilise par défaut le nom de l’assembly et remplace l’extension de l’élément par *.tlb*.|

## <a name="remarks"></a>Remarques
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).

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
- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)