---
title: Métadonnées d’éléments dans le traitement par lots des cibles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a77c5b1c932785e1363934554789102d8e4bea1a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955334"
---
# <a name="item-metadata-in-target-batching"></a>Métadonnées d’élément dans le traitement par lots des cibles
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] a la capacité d’effectuer une analyse des dépendances sur les entrées et les sorties d’une cible de génération. S’il est déterminé que les entrées ou les sorties de la cible sont à jour, la cible est ignorée et la génération a lieu. Les éléments `Target` utilisent les attributs `Inputs` et `Outputs` pour spécifier les éléments à inspecter pendant l’analyse des dépendances.  
  
 Si une cible contient une tâche qui utilise des éléments traités par lots comme entrées ou sorties, l’élément `Target` de la cible doit utiliser le traitement par lots dans ses attributs `Inputs` ou `Outputs` pour permettre à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] d’ignorer les lots d’éléments qui sont déjà à jour.  
  
## <a name="batch-targets"></a>Traiter des cibles par lots  
 L’exemple suivant contient une liste d’éléments nommée `Res` qui est divisée en deux lots, selon les métadonnées de l’élément `Culture`. Chacun de ces lots est passé à la tâche `AL`, qui crée un assembly de sortie pour chaque lot. L’utilisation du traitement par lot sur l’attribut `Outputs` de l’élément `Target` permet à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de déterminer si chaque lot est à jour avant d’exécuter la cible. Si vous n’utilisez pas le traitement par lot des cibles, les deux lots d’éléments sont exécutés par la tâche chaque fois que la cible est exécutée.  
  
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
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour effectuer des builds incrémentielles](../msbuild/how-to-build-incrementally.md)   
 [Traitement par lot MSBuild](../msbuild/msbuild-batching.md)   
 [Target, élément (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Métadonnées d’élément dans le traitement par lots des tâches](../msbuild/item-metadata-in-task-batching.md)