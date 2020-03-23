---
title: 'Comment : référencer le nom ou l’emplacement du fichier projet | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b54a63b135f844ff20b45ffac430662c4df1f19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633835"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Guide pratique pour référencer le nom ou l’emplacement du fichier projet

Vous pouvez utiliser le nom ou l’emplacement du projet dans le fichier projet sans avoir à créer votre propre propriété. MSBuild fournit des propriétés réservées qui font référence au nom du fichier du projet et à d’autres propriétés liées au projet. Pour plus d’informations sur les propriétés réservées, consultez [MSBuild, propriétés réservées et connues](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="use-the-project-properties"></a>Utiliser les propriétés du projet

 MSBuild fournit certaines propriétés réservées que vous pouvez utiliser dans vos fichiers de projet sans les définir à chaque fois. Par exemple, la propriété réservée `MSBuildProjectName` fournit une référence au nom du fichier projet. La propriété réservée `MSBuildProjectDirectory` fournit une référence à l’emplacement du fichier projet.

#### <a name="to-use-the-project-properties"></a>Pour utiliser les propriétés du projet

- Référencez la propriété dans le fichier projet avec la notation $(), comme vous le feriez avec n’importe quelle propriété. Par exemple :

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  L’un des avantages liés à l’utilisation d’une propriété réservée est que les modifications apportées au nom du fichier projet sont incorporées automatiquement. À la prochaine génération du projet, le fichier de sortie dispose du nouveau nom sans aucune intervention supplémentaire de votre part.

  Pour plus d’informations sur l’utilisation de caractères spéciaux dans les références de fichiers ou de projet, voir [msBuild caractères spéciaux](../msbuild/msbuild-special-characters.md).

> [!NOTE]
> Les propriétés réservées ne peuvent pas être redéfinies dans le fichier projet.

## <a name="example"></a> Exemple

 L’exemple de fichier projet suivant référence le nom du projet en tant que propriété réservée pour spécifier le nom de la sortie.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    DefaultTargets = "Compile">

    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
     </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using
        input files of type CSFile -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(MSBuildProjectName).exe" >
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the project -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example"></a> Exemple

 L’exemple de fichier projet suivant utilise la propriété réservée `MSBuildProjectDirectory` pour créer le chemin complet à un fichier à l’emplacement du fichier projet.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

L’exemple utilise la syntaxe de fonction <xref:System.IO.Path.Combine*?displayProperty=fullName>de [propriété](property-functions.md) pour appeler la méthode statique .NET Framework .

## <a name="see-also"></a>Voir aussi

- [MSBuild](../msbuild/msbuild.md)
- [MSBuild, propriétés réservées et connues](../msbuild/msbuild-reserved-and-well-known-properties.md)
