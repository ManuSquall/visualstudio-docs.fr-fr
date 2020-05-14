---
title: Métadonnées d’éléments dans le traitement par lots des cibles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a5d0c9dec280633d0a39573581c083e6ddd4d8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633666"
---
# <a name="item-metadata-in-target-batching"></a>Métadonnées d’élément dans le traitement par lots des cibles

MSBuild a la capacité d’effectuer une analyse de dépendance sur les intrants et les extrants d’une cible de construction. S’il est déterminé que les entrées ou les sorties de la cible sont à jour, la cible est ignorée et la génération a lieu. Les éléments `Target` utilisent les attributs `Inputs` et `Outputs` pour spécifier les éléments à inspecter pendant l’analyse des dépendances.

Si une cible contient une tâche qui utilise des éléments `Target` en lots sous forme d’entrées ou de sorties, l’élément de la cible doit utiliser le lotage dans son `Inputs` ou `Outputs` ses attributs pour permettre à MSBuild de sauter des lots d’articles qui sont déjà à jour.

## <a name="batch-targets"></a>Traiter des cibles par lots

L’exemple suivant contient une liste d’éléments nommée `Res` qui est divisée en deux lots, selon les métadonnées de l’élément `Culture`. Chacun de ces lots est passé à la tâche `AL`, qui crée un assembly de sortie pour chaque lot. En utilisant le `Outputs` lotage `Target` sur l’attribut de l’élément, MSBuild peut déterminer si chacun des lots individuels est à jour avant d’exécuter la cible. Si vous n’utilisez pas le traitement par lot des cibles, les deux lots d’éléments sont exécutés par la tâche chaque fois que la cible est exécutée.

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

- [Comment : Construire progressivement](../msbuild/how-to-build-incrementally.md)
- [Dosage](../msbuild/msbuild-batching.md)
- [Target, élément (MSBuild)](../msbuild/target-element-msbuild.md)
- [Métadonnées d’articles dans le lotage de tâches](../msbuild/item-metadata-in-task-batching.md)
