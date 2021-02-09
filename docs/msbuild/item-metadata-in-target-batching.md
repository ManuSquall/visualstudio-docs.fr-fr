---
title: Métadonnées d’éléments dans le traitement par lots des cibles | Microsoft Docs
description: Découvrez comment MSBuild utilise les métadonnées d’élément dans le traitement par lots de cibles pour effectuer une analyse des dépendances sur les entrées et les sorties d’une cible de génération.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d3389d24ded805c7b1f8bbb8d31daef0cbef1a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913899"
---
# <a name="item-metadata-in-target-batching"></a>Métadonnées d’élément dans le traitement par lots des cibles

MSBuild a la possibilité d’effectuer une analyse des dépendances sur les entrées et les sorties d’une cible de génération. S’il est déterminé que les entrées ou les sorties de la cible sont à jour, la cible est ignorée et la génération a lieu. Les éléments `Target` utilisent les attributs `Inputs` et `Outputs` pour spécifier les éléments à inspecter pendant l’analyse des dépendances.

Si une cible contient une tâche qui utilise des éléments traités par lot en tant qu’entrées ou sorties, l' `Target` élément de la cible doit utiliser le traitement par lot dans ses `Inputs` `Outputs` attributs ou pour permettre à MSBuild d’ignorer les lots d’éléments qui sont déjà à jour.

## <a name="batch-targets"></a>Traiter des cibles par lots

L’exemple suivant contient une liste d’éléments nommée `Res` qui est divisée en deux lots, selon les métadonnées de l’élément `Culture`. Chacun de ces lots est passé à la tâche `AL`, qui crée un assembly de sortie pour chaque lot. En utilisant le traitement par lot sur l' `Outputs` attribut de l' `Target` élément, MSBuild peut déterminer si chacun des lots individuels est à jour avant d’exécuter la cible. Si vous n’utilisez pas le traitement par lot des cibles, les deux lots d’éléments sont exécutés par la tâche chaque fois que la cible est exécutée.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Res Include="Strings.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Strings.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.jp.resources">
            <Culture>jp</Culture>
        </Res>
    </ItemGroup>

    <Target Name="Build"
        Inputs="@(Res)"
        Outputs="%(Culture)\MyApp.resources.dll">

        <AL Resources="@(Res)"
            TargetType="library"
            OutputAssembly="%(Culture)\MyApp.resources.dll">

    </Target>

</Project>
```

## <a name="see-also"></a>Voir aussi

- [Comment : générer de façon incrémentielle](../msbuild/how-to-build-incrementally.md)
- [Traitement par lot](../msbuild/msbuild-batching.md)
- [Target, élément (MSBuild)](../msbuild/target-element-msbuild.md)
- [Métadonnées d’élément dans le traitement par lots des tâches](../msbuild/item-metadata-in-task-batching.md)
