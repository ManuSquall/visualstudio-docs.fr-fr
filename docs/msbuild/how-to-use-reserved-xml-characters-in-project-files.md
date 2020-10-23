---
title: 'Comment : utiliser des caractères XML réservés dans les fichiers projet | Microsoft Docs'
description: Découvrez comment remplacer des caractères XML réservés par des entités nommées correspondantes dans les fichiers projet MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f98044378b717536c42f25f5033b072ac3680675
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436085"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Guide pratique pour utiliser des caractères XML réservés dans les fichiers projet

Lorsque vous créez des fichiers projet, vous devrez peut-être utiliser des caractères XML réservés, par exemple, dans les valeurs de propriétés ou dans les valeurs de paramètres de tâche. Toutefois, certains caractères réservés doivent être remplacés par une entité nommée afin que le fichier projet puisse être analysé.

## <a name="use-reserved-characters"></a>Utiliser des caractères réservés

 Le tableau suivant décrit les caractères XML réservés qui doivent être remplacés par l’entité nommée correspondante afin que le fichier projet puisse être analysé.

|Caractère réservé|Entité nommée|
|------------------------|------------------|
|\<|&amp;lt;|
|>|&amp;gt;|
|&|&amp;amp;|
|"|&amp;quot;|
|'|&amp;apos;|

#### <a name="to-use-double-quotes-in-a-project-file"></a>Pour utiliser des guillemets doubles dans un fichier projet

- Remplacez les guillemets doubles par l’entité nommée correspondante, &amp;quot;. Par exemple, pour placer des guillemets doubles autour de la liste d’éléments `EXEFile`, tapez :

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>Exemple

 Dans l’exemple de code suivant, des guillemets doubles sont utilisés pour mettre en surbrillance le nom de fichier dans le message qui est sorti par le fichier projet.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>"HelloWorldCS"</appname>
    </PropertyGroup>
    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs" />
    </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input
        files of type CSFile -->
        <Csc Sources = "@(CSFile)">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile"/>
        </Csc>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
