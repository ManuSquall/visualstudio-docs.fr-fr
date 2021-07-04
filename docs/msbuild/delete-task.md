---
title: Delete, tâche | Microsoft Docs
description: en savoir plus sur les paramètres et les considérations relatives à l’utilisation de la tâche de suppression MSBuild pour supprimer les fichiers spécifiés.
ms.custom: SEO-VS-2020
ms.date: 06/11/2020
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09945306a2260bed5b264d380dcea745ff3f7c07
ms.sourcegitcommit: 8fb1500acb7e6314fbb6b78eada78ef5d61d39bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2021
ms.locfileid: "113280430"
---
# <a name="delete-task"></a>Delete (tâche)

Supprime les fichiers spécifiés.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche `Delete` .

|Paramètre|Description|
|---------------|-----------------|
|`DeletedFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les fichiers qui ont été supprimés.|
|`Files`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les fichiers à supprimer.|
|`TreatErrorsAsWarnings`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, les erreurs sont consignées en tant qu’avertissements. La valeur par défaut est `false`.|

## <a name="remarks"></a>Remarques

En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Soyez prudent lorsque vous utilisez des caractères génériques avec la `Delete` tâche. Vous pouvez facilement supprimer les fichiers incorrects avec des expressions telles que `$(SomeProperty)\**\*.*` ou `$(SomeProperty)/**/*.*` , en particulier si la propriété a la valeur d’une chaîne vide, auquel cas le `Files` paramètre peut correspondre à la racine de votre lecteur et supprimer bien plus que vous souhaitez supprimer.

## <a name="example"></a>Exemple

L’exemple suivant supprime le fichier *ConsoleApp1. pdb* lorsque vous générez la `DeleteDebugSymbolFile` cible.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

    <PropertyGroup>
        <AppName>ConsoleApp1</AppName>
    </PropertyGroup>

    <Target Name="DeleteDebugSymbolFile">
        <Message Text="Deleting $(OutDir)$(AppName).pdb"/>
        <Delete Files="$(OutDir)$(AppName).pdb" />
    </Target>
  
</Project>

```

Si vous devez effectuer le suivi des fichiers supprimés, affectez `TaskParameter` la valeur à `DeletedFiles` avec le nom de l’élément, comme suit :

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

Au lieu d’utiliser directement des caractères génériques dans la `Delete` tâche, créez un `ItemGroup` des fichiers à supprimer et exécutez la `Delete` tâche sur celle-ci. Mais n’hésitez pas à la placer `ItemGroup` soigneusement. Si vous placez une `ItemGroup` au niveau supérieur d’un fichier projet, elle est évaluée au début, avant le démarrage de la génération, de sorte qu’elle n’inclut pas les fichiers qui ont été générés dans le cadre du processus de génération. Par conséquent, placez le `ItemGroup` qui crée la liste des éléments à supprimer dans une cible proche de la `Delete` tâche. Vous pouvez également spécifier une condition pour vérifier que la propriété n’est pas vide, afin que vous ne puissiez pas créer une liste d’éléments avec un chemin d’accès qui commence à la racine du lecteur.

La `Delete` tâche est destinée à supprimer des fichiers. Si vous souhaitez supprimer un répertoire, utilisez [RemoveDir,](removedir-task.md).

La `Delete` tâche ne fournit pas d’option permettant de supprimer les fichiers en lecture seule. Pour supprimer des fichiers en lecture seule, vous pouvez utiliser la `Exec` tâche pour exécuter la `del` commande ou l’équivalent, avec l’option appropriée pour activer la suppression des fichiers en lecture seule. Vous devez faire attention à la longueur de la liste d’éléments d’entrée, étant donné qu’il y a une limite de longueur sur la ligne de commande, et que vous veillez à gérer les noms de fichiers avec des espaces, comme dans cet exemple :

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

En général, lors de l’écriture de scripts de génération, déterminez si votre suppression fait logiquement partie d’une `Clean` opération. Si vous devez définir des fichiers à nettoyer dans le cadre d’une opération normale `Clean` , vous pouvez les ajouter à la `@(FileWrites)` liste et les supprimer à la suite `Clean` . Si un traitement personnalisé est nécessaire, définissez une cible et spécifiez-la pour qu’elle s’exécute en définissant l’attribut `BeforeTargets="Clean"` ou `AfterTargets="Clean"` , ou définissez votre version personnalisée des `BeforeClean` `AfterClean` cibles ou. Consultez [personnaliser votre Build](customize-your-build.md).

## <a name="see-also"></a>Voir aussi

- [RemoveDir (tâche)](removedir-task.md)
- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
