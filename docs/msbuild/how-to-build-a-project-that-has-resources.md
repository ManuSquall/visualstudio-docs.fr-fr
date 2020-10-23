---
title: 'Comment : générer un projet qui dispose de ressources | Microsoft Docs'
description: Découvrez comment créer un projet qui a des ressources et comment compiler des ressources à l’aide de MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6a71a34b4ce208b093f7982ba3516b0229c8644
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436686"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Guide pratique pour générer un projet qui a des ressources

Si vous générez les versions localisées d’un projet, tous les éléments de l’interface utilisateur doivent être séparés dans des fichiers de ressources correspondant aux différentes langues. Si le projet utilise uniquement des chaînes, les fichiers de ressources peuvent utiliser des fichiers texte. Vous pouvez également utiliser des fichiers *.resx* comme fichiers de ressources.

## <a name="compile-resources-with-msbuild"></a>Compiler des ressources avec MSBuild

La bibliothèque de tâches courantes qui est fournie avec MSBuild comprend une `GenerateResource` tâche que vous pouvez utiliser pour compiler des ressources dans des fichiers *. resx* ou texte. Cette tâche inclut le paramètre `Sources` pour spécifier les fichiers de ressources à compiler et le paramètre `OutputResources` pour spécifier les noms des fichiers de ressources de sortie. Pour plus d’informations sur la tâche `GenerateResource`, consultez [GenerateResource, tâche](../msbuild/generateresource-task.md).

#### <a name="to-compile-resources-with-msbuild"></a>Pour compiler des ressources avec MSBuild

1. Identifiez les fichiers de ressources du projet et transmettez-les à la tâche `GenerateResource`, en tant que listes d’éléments ou noms de fichiers.

2. Spécifiez le paramètre `OutputResources` de la tâche `GenerateResource`, qui vous permet de définir les noms des fichiers de ressources de sortie.

3. Utilisez l’élément `Output` de la tâche pour stocker la valeur du paramètre `OutputResources` dans un élément.

4. Utilisez l’élément créé à partir de l’élément `Output` en tant qu’entrée d’une autre tâche.

## <a name="example-1"></a>Exemple 1

L’exemple de code suivant montre comment l’élément `Output` spécifie que l’attribut `OutputResources` de la tâche `GenerateResource` contient les fichiers de ressources compilés *alpha.resources* et *beta.resources* et que ces deux fichiers sont placés dans la liste d’éléments `Resources`. En identifiant ces fichiers *.resources* comme collection d’éléments du même nom, vous pouvez les utiliser facilement comme entrées d’une autre tâche, par exemple la tâche [Csc](../msbuild/csc-task.md).

Cette tâche revient à utiliser le commutateur **/compiler** pour [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) :

`Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`

```xml
<GenerateResource
    Sources="alpha.resx; beta.txt"
    OutputResources="alpha.resources; beta.resources">
    <Output TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

## <a name="example-2"></a>Exemple 2

L’exemple de projet suivant contient deux tâches : la tâche `GenerateResource` permet de compiler les ressources, et la tâche `Csc` permet de compiler les fichiers de code source et les fichiers de ressources compilés. Les fichiers de ressources compilés par la tâche `GenerateResource` sont stockés dans l’élément `Resources` et transmis à la tâche `Csc`.

```xml
<Project DefaultTargets = "Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <Target Name="Resources">
        <GenerateResource
            Sources="alpha.resx; beta.txt"
            OutputResources="alpha.resources; beta.resources">
            <Output TaskParameter="OutputResources"
                ItemName="Resources"/>
        </GenerateResource>
    </Target>

    <Target Name="Build" DependsOnTargets="Resources">
        <Csc Sources="hello.cs"
                Resources="@(Resources)"
                OutputAssembly="hello.exe"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [MSBuild](../msbuild/msbuild.md)
- [GenerateResource (tâche)](../msbuild/generateresource-task.md)
- [Csc (tâche)](../msbuild/csc-task.md)
- [Resgen.exe (générateur de fichiers de ressources)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
