---
title: WriteLinesToFile, tâche | Microsoft Docs
description: Découvrez comment MSBuild utilise la tâche WriteLinesToFile pour écrire les chemins d’accès des éléments spécifiés dans le fichier texte spécifié.
ms.custom: SEO-VS-2020
ms.date: 09/20/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f4e2f98f25c43fbd467218ed8777ad5f4a2ecb9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887950"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile (tâche)

Écrit les chemins des éléments spécifiés dans le fichier texte spécifié.

## <a name="task-parameters"></a>Paramètres de tâche

 Le tableau ci-dessous décrit les paramètres de la tâche `WriteLinestoFile` .

|Paramètre|Description|
|---------------|-----------------|
|`File`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le fichier où écrire les éléments.|
|`Lines`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les éléments à écrire dans le fichier. La valeur par défaut est la liste vide.|
|`Overwrite`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, remplace le contenu existant dans le fichier. La valeur par défaut est `false`.|
|`Encoding`|Paramètre `String` facultatif.<br /><br /> Sélectionne l’encodage des caractères, par exemple « Unicode ». La valeur par défaut est UTF-8.  Voir aussi <xref:System.Text.Encoding>.|
|`WriteOnlyWhenDifferent`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, le fichier cible spécifié, existe, il sera lu en premier pour effectuer la comparaison avec ce que la tâche aurait écrit. Si les deux sont identiques, le fichier n’est pas enregistré sur le disque et l’horodatage est conservé. La valeur par défaut est `false`.|

## <a name="remarks"></a>Remarques

 Si `Overwrite` est `true`, crée un fichier, écrit le contenu dans ce fichier, puis le ferme. Si le fichier cible existe déjà, il est remplacé. Si `Overwrite` est `false`, ajoute le contenu au fichier, en créant le fichier cible s’il n’existe pas.

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple

 L’exemple suivant utilise la tâche `WriteLinesToFile` pour écrire les chemins des éléments de la collection d’éléments `MyItems` dans le fichier spécifié par la collection d’éléments `MyTextFile`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
        <MyItems Include="*.cs"/>
    </ItemGroup>

    <Target Name="WriteToFile">
        <WriteLinesToFile
            File="@(MyTextFile)"
            Lines="@(MyItems)"
            Overwrite="true"
            Encoding="Unicode"/>
    </Target>

</Project>
```

Dans cet exemple, nous utilisons une propriété avec des sauts de ligne incorporés pour écrire un fichier texte comportant plusieurs lignes. Si une entrée dans `Lines` comporte des caractères de saut de ligne incorporés, les nouvelles lignes figurent dans le fichier de sortie. De cette façon, vous pouvez référencer des propriétés multilignes.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <Target Name="WriteLaunchers" AfterTargets="CopyFilesToOutputDirectory">
      <PropertyGroup>
        <LauncherCmd>
@ECHO OFF
dotnet %~dp0$(AssemblyName).dll %*
        </LauncherCmd>
      </PropertyGroup>

      <WriteLinesToFile
        File="$(OutputPath)$(AssemblyName).cmd"
        Overwrite="true"
        Lines="$(LauncherCmd)" />
  </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
