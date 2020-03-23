---
title: Guide pratique pour utiliser la même cible dans plusieurs fichiers projet | Microsoft Docs
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
ms.openlocfilehash: 1b7b36a829e2e406ecd3f10ba3a2b588c6f7df25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633757"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Guide pratique pour utiliser la même cible dans plusieurs fichiers projet

Si vous avez rédigé plusieurs fichiers de projets MSBuild, vous avez peut-être découvert que vous devez utiliser les mêmes tâches et cibles dans différents fichiers de projet. Au lieu d’inclure la description complète de ces tâches ou de ces cibles dans chaque fichier projet, vous pouvez enregistrer une cible dans un fichier projet distinct et importer ensuite ce projet dans un autre projet qui doit utiliser la cible.
## <a name="use-the-import-element"></a>Utiliser l’élément Import

 L’élément `Import` est utilisé pour insérer un fichier projet dans un autre fichier projet. Le dossier de projet importé doit être un fichier de projet MSBuild valide et contenir un XML bien formé. L’attribut `Project` spécifie le chemin du fichier projet importé. Pour plus d’informations sur l’élément, `Import` voir Élément [d’importation (MSBuild)](../msbuild/import-element-msbuild.md).
L’élément `Import` est utilisé pour insérer un fichier projet dans un autre fichier projet. Le dossier de projet importé doit être un fichier de projet MSBuild valide et contenir un XML bien formé. L’attribut `Project` spécifie le chemin du fichier projet importé. Pour plus d’informations sur l’élément, `Import` voir Élément [d’importation (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Pour importer un projet

1. Dans le fichier projet importateur, définissez toutes les propriétés et les éléments qui sont utilisés comme paramètres des propriétés et des éléments dans le projet importé.

2. Utilisez l’élément `Import` pour importer le projet. Par exemple :

     `<Import Project="MyCommon.targets"/>`

3. Après l’élément `Import`, définissez toutes les propriétés et tous les éléments qui doivent remplacer les définitions par défaut des propriétés et des éléments dans le projet importé.

## <a name="order-of-evaluation"></a>Ordre d’évaluation

 Lorsque MSBuild `Import` atteint un élément, le projet importé est effectivement inséré dans `Import` le projet d’importation à l’emplacement de l’élément. Par conséquent, l’emplacement de l’élément `Import` peut affecter les valeurs des propriétés et des éléments. Il est important de comprendre les propriétés et les éléments qui sont définis par le projet importé, ainsi que les propriétés et les éléments utilisés par le projet importé.

 Quand le projet est généré, toutes les propriétés sont évaluées en premier, suivies par les éléments. Par exemple, le XML suivant définit le fichier de projet importé *MyCommon.targets*:

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

 Le XML suivant définit *MyApp.proj*, qui importe *MyCommon.targets*:

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

 Parce que le projet est `Name` importé après que la propriété a `Name` été définie dans *MyApp.proj*, la définition de dans *MyCommon.targets* remplace la définition dans *MyApp.proj*. Si le projet est importé avant la définition de la propriété Name, la génération affiche le message suivant :

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Utilisez l’approche suivante lors de l’importation de projets

1. Dans le fichier projet, définissez toutes les propriétés et les éléments qui sont utilisés comme paramètres des propriétés et des éléments dans le projet importé.

2. Importez le projet.

3. Définissez dans le fichier projet toutes les propriétés et tous les éléments qui doivent remplacer les définitions par défaut des propriétés et des éléments dans le projet importé.

## <a name="example"></a> Exemple

 L’exemple de code suivant montre le fichier *MyCommon.targets* que le deuxième exemple de code importe. Le fichier *.targets* évalue les propriétés du projet d’importation pour configurer la construction.

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

## <a name="example"></a> Exemple

 L’exemple de code suivant importe le fichier *MyCommon.targets.*

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
