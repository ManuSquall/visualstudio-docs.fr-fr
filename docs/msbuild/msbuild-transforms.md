---
title: Transformations MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2fe127a98236c321db9d1e7450ab006e09badba
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627257"
---
# <a name="msbuild-transforms"></a>Transformations MSBuild
Une transformation est une conversion de type un-à-un d’une liste d’éléments en une autre. En plus de permettre à un projet de convertir des listes d’éléments, une transformation permet à une cible d’identifier un mappage direct entre ses entrées et ses sorties. Cette rubrique explique les transformations et comment [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] les utilise pour générer des projets plus efficacement.

## <a name="transform-modifiers"></a>Modificateurs de transformation
Les transformations ne sont pas arbitraires, mais elles sont limitées par une syntaxe spéciale dans laquelle tous les modificateurs de transformation doivent être au format %(\<ItemMetaDataName>). Toutes les métadonnées d’élément peuvent être utilisées comme modificateurs de transformation, y compris les métadonnées d’élément connues affectées à chaque élément lors de sa création. Pour obtenir la liste complète des métadonnées d’élément connues, consultez [Métadonnées d’élément connues](../msbuild/msbuild-well-known-item-metadata.md).

Dans l’exemple suivant, une liste de fichiers *.resx* est transformée en liste de fichiers *.resources*. Le modificateur de transformation %(filename) spécifie que chaque fichier *.resources* a le même nom de fichier que le fichier *.resx* correspondant.

```xml
@(RESXFile->'%(filename).resources')
```

Par exemple, si les éléments de la liste d’éléments @(RESXFile) sont *Form1.resx*, *Form2.resx* et *Form3.resx*, les sorties de la liste transformée sont *Form1.resources*, *Form2.resources* et *Form3.resources*.

> [!NOTE]
>  Vous pouvez spécifier un séparateur personnalisé pour une liste d’éléments transformée de la même façon que vous spécifiez un séparateur pour une liste d’éléments standard. Par exemple, pour séparer les éléments d’une liste transformée à l’aide de la virgule (,) au lieu du point-virgule (;) par défaut, utilisez le code XML suivant : `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`

## <a name="use-multiple-modifiers"></a>Utiliser plusieurs modificateurs
 Une expression de transformation peut contenir plusieurs modificateurs, qui peuvent être combinés dans n’importe quel ordre et peuvent être répétés. Dans l’exemple suivant, le nom du répertoire qui contient les fichiers change alors que les fichiers conservent le nom et l’extension de nom de fichier d’origine.

```xml
@(RESXFile->'Toolset\%(filename)%(extension)')
```

 Par exemple, si les éléments contenus dans la liste d’éléments `RESXFile` sont *Project1\Form1.resx*, *Project1\Form2.resx* et *Project1\Form3.text*, les sorties de la liste transformée sont *Toolset\Form1.resx*, *Toolset\Form2.resx* et *Toolset\Form3.text*.

## <a name="dependency-analysis"></a>Analyse des dépendances
 Les transformations garantissent un mappage de type un-à-un entre la liste d’éléments transformée et la liste d’éléments d’origine. Par conséquent, si une cible crée des sorties qui sont des transformations des entrées, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] peut analyser les horodatages des entrées et des sorties, et décider s’il faut ignorer, générer ou partiellement regénérer une cible.

 Dans la [tâche de copie](../msbuild/copy-task.md) de l’exemple suivant, chaque fichier de la liste d’éléments `BuiltAssemblies` est mappé à un fichier du dossier de destination de la tâche, spécifié en utilisant une transformation dans l’attribut `Outputs`. Si un fichier de la liste d’éléments `BuiltAssemblies` change, la tâche `Copy` s’exécute uniquement pour le fichier modifié. Tous les autres fichiers sont ignorés. Pour plus d’informations sur l’analyse des dépendances et sur la façon d’utiliser des transformations, consultez [Guide pratique pour effectuer des builds incrémentielles](../msbuild/how-to-build-incrementally.md).

```xml
<Target Name="CopyOutputs"
    Inputs="@(BuiltAssemblies)"
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">

    <Copy
        SourceFiles="@(BuiltAssemblies)"
        DestinationFolder="$(OutputPath)"/>

</Target>
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description
 L’exemple suivant montre un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] qui utilise des transformations. Cet exemple suppose qu’il n’y a qu’un seul fichier *.xsd* dans le répertoire *c:\sub0\sub1\sub2\sub3*, et que le répertoire de travail est *c:\sub0*.

### <a name="code"></a>Code

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Schema Include="sub1\**\*.xsd"/>
    </ItemGroup>

    <Target Name="Messages">
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>
        <Message Text="identity: @(Schema->'%(identity)')"/>
        <Message Text="filename: @(Schema->'%(filename)')"/>
        <Message Text="directory: @(Schema->'%(directory)')"/>
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>
        <Message Text="extension: @(Schema->'%(extension)')"/>
    </Target>
</Project>
```

### <a name="comments"></a>Commentaires
 Cet exemple génère la sortie suivante :

```
rootdir: C:\
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd
identity: sub1\sub2\sub3\myfile.xsd
filename: myfile
directory: xmake\sub1\sub2\sub3\
relativedir: sub1\sub2\sub3\
extension: .xsd
```

## <a name="see-also"></a>Voir aussi
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [Guide pratique pour effectuer des builds incrémentielles](../msbuild/how-to-build-incrementally.md)