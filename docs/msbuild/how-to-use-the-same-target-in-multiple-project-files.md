---
title: Guide pratique pour utiliser la même cible dans plusieurs fichiers projet | Microsoft Docs
description: Découvrez comment enregistrer une cible dans un fichier projet MSBuild et l’importer dans un autre projet qui doit utiliser la cible.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d81328ecf17117500a5f686a45f934e451bb5809
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436058"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Guide pratique pour utiliser la même cible dans plusieurs fichiers projet

Si vous avez créé plusieurs fichiers projet MSBuild, vous avez peut-être découvert que vous devez utiliser les mêmes tâches et cibles dans différents fichiers projet. Au lieu d’inclure la description complète de ces tâches ou de ces cibles dans chaque fichier projet, vous pouvez enregistrer une cible dans un fichier projet distinct et importer ensuite ce projet dans un autre projet qui doit utiliser la cible.

## <a name="use-the-import-element"></a>Utiliser l’élément Import

L’élément `Import` est utilisé pour insérer un fichier projet dans un autre fichier projet. Le fichier projet en cours d’importation doit être un fichier projet MSBuild valide et contenir du code XML correct. L’attribut `Project` spécifie le chemin du fichier projet importé. Pour plus d’informations sur l' `Import` élément, consultez [import, élément (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Pour importer un projet

1. Dans le fichier projet importateur, définissez toutes les propriétés et les éléments qui sont utilisés comme paramètres des propriétés et des éléments dans le projet importé.

2. Utilisez l’élément `Import` pour importer le projet. Par exemple :

     `<Import Project="MyCommon.targets"/>`

3. Après l’élément `Import`, définissez toutes les propriétés et tous les éléments qui doivent remplacer les définitions par défaut des propriétés et des éléments dans le projet importé.

## <a name="order-of-evaluation"></a>Ordre d’évaluation

 Quand MSBuild atteint un `Import` élément, le projet importé est effectivement inséré dans le projet d’importation à l’emplacement de l' `Import` élément. Par conséquent, l’emplacement de l’élément `Import` peut affecter les valeurs des propriétés et des éléments. Il est important de comprendre les propriétés et les éléments qui sont définis par le projet importé, ainsi que les propriétés et les éléments utilisés par le projet importé.

 Quand le projet est généré, toutes les propriétés sont évaluées en premier, suivies par les éléments. Par exemple, le code XML suivant définit le fichier projet importé *MyCommon. targets*:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyCommon</Name>
    </PropertyGroup>

    <Target Name="Go">
        <Message Text="Name=$(Name)"/>
    </Target>
</Project>
```

 Le code XML suivant définit *MyApp. proj*, qui importe *MyCommon. targets*:

```xml
<Project
    DefaultTargets="Go"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyApp</Name>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

 Quand le projet est généré, le message suivant est affiché :

 `Name="MyCommon"`

 Étant donné que le projet est importé après que la propriété `Name` a été définie dans *MyApp. proj*, la définition de `Name` dans *MyCommon. targets* se substitue à la définition dans *MyApp. proj*. Si le projet est importé avant la définition de la propriété Name, la génération affiche le message suivant :

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Utilisez l’approche suivante lors de l’importation de projets

1. Dans le fichier projet, définissez toutes les propriétés et les éléments qui sont utilisés comme paramètres des propriétés et des éléments dans le projet importé.

2. Importez le projet.

3. Définissez dans le fichier projet toutes les propriétés et tous les éléments qui doivent remplacer les définitions par défaut des propriétés et des éléments dans le projet importé.

## <a name="example-1"></a>Exemple 1

 L’exemple de code suivant montre le fichier *MyCommon. targets* que le deuxième exemple de code importe. Le fichier *. targets* évalue les propriétés du projet importateur pour configurer la Build.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>
        <appname>$(MSBuildProjectName)</appname>
    <PropertyGroup>
    <Target Name="Build">
        <Csc Sources="hello.cs"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe"/>
    </Target>
</Project>
```

## <a name="example-2"></a>Exemple 2

 L’exemple de code suivant importe le fichier *MyCommon. targets* .

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor>RETAIL</Flavor>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Import, élément (MSBuild)](../msbuild/import-element-msbuild.md)
- [Cibles](../msbuild/msbuild-targets.md)
