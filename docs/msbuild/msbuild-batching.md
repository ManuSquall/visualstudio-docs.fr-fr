---
title: Traitement par lots de MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78aeef8ea651aac1fe2a780207474399f4bbcf09
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633432"
---
# <a name="msbuild-batching"></a>Traitement par lots MSBuild

MSBuild a la possibilité de diviser les listes d’éléments en différentes catégories, ou lots, en fonction des métadonnées d’articles, et d’exécuter une cible ou une tâche une fois avec chaque lot.

## <a name="task-batching"></a>Traitement par lots des tâches

Le traitement de tâches par lots vous permet de simplifier vos fichiers projet en fournissant un moyen de diviser les listes d’éléments en différents lots et de passer chacun de ces lots dans une tâche séparément. Cela signifie qu’une tâche et ses attributs ne doivent être déclarés qu’une seule fois dans un fichier projet, même si elle peut être exécutée plusieurs fois.

Vous spécifiez que vous souhaitez que MSBuild\<effectue le lot avec une tâche en utilisant la notation %(ItemMetaDataName>) dans l’un des attributs de tâche. L’exemple suivant fractionne la liste d’éléments `Example` en lots en fonction de la valeur des métadonnées de l’élément `Color` et passe séparément chacun des lots à la tâche `MyTask`.

> [!NOTE]
> Si vous ne référencez pas la liste d’éléments ailleurs dans les attributs de tâche, ou si le nom des métadonnées peut être ambigu, vous pouvez utiliser la notation %(\<ItemCollection.ItemMetaDataName>) pour qualifier complètement la valeur des métadonnées de l’élément à utiliser pour le traitement par lots.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Pour obtenir des exemples de traitement par lots plus spécifiques, consultez [Métadonnées d’élément dans le traitement par lots des tâches](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Traitement par lots des cibles

MSBuild vérifie si les entrées et les sorties d’une cible sont à jour avant qu’il n’exécute la cible. Si les entrées et les sorties sont à jour, la cible est ignorée. Si une tâche à l’intérieur d’une cible utilise le lotage, MSBuild doit déterminer si les entrées et les sorties pour chaque lot d’articles sont à jour. Sinon, la cible est exécutée chaque fois qu’elle est atteinte.

L’exemple suivant montre un élément `Target` contenant un attribut `Outputs` avec la notation %(\<ItemMetaDataName>). MSBuild divisera `Example` la liste d’éléments `Color` en lots en fonction des métadonnées de l’article et analysera les délais des fichiers de sortie pour chaque lot. Si les sorties d’un lot ne sont pas à jour, la cible est exécutée. Sinon, la cible est ignorée.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Pour obtenir un autre exemple de traitement par lots des cibles, consultez [Métadonnées d’élément dans le traitement par lots des cibles](../msbuild/item-metadata-in-target-batching.md).

## <a name="property-functions-using-metadata"></a>Fonctions de propriété utilisant des métadonnées

Le traitement par lots peut être contrôlé par des fonctions de propriété qui incluent des métadonnées. Par exemple,

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

utilise <xref:System.IO.Path.Combine%2A> pour combiner un chemin de dossier racine avec un chemin d’élément de compilation.

Les fonctions de propriété ne peuvent pas apparaître dans des valeurs de métadonnées. Par exemple,

`%(Compile.FullPath.Substring(0,3))`

n’est pas autorisé.

Pour plus d’informations sur les fonctions de propriété, consultez [Fonctions de propriété](../msbuild/property-functions.md).

## <a name="see-also"></a>Voir aussi

- [ItemMetadata, élément (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [Concepts avancés](../msbuild/msbuild-advanced-concepts.md)
