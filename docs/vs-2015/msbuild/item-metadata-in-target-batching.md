---
title: Métadonnées d’éléments dans le traitement par lots des cibles | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2d91e294165012bea3b1ac196011cf9908469a7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494129"
---
# <a name="item-metadata-in-target-batching"></a>Métadonnées d'éléments dans le traitement par lots de cibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [métadonnées d’éléments dans le traitement par lot cible](https://docs.microsoft.com/visualstudio/msbuild/item-metadata-in-target-batching).  
  
  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] a la capacité d’effectuer une analyse des dépendances sur les entrées et les sorties d’une cible de génération. S’il est déterminé que les entrées ou les sorties de la cible sont à jour, la cible est ignorée et la génération a lieu. Les éléments `Target` utilisent les attributs `Inputs` et `Outputs` pour spécifier les éléments à inspecter pendant l’analyse des dépendances.  
  
 Si une cible contient une tâche qui utilise des éléments traités par lots comme entrées ou sorties, l’élément `Target` de la cible doit utiliser le traitement par lots dans ses attributs `Inputs` ou `Outputs` pour permettre à [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] d’ignorer les lots d’éléments qui sont déjà à jour.  
  
## <a name="batching-targets"></a>Traitement par lots des cibles  
 L’exemple suivant contient une liste d’éléments nommée `Res` qui est divisée en deux lots, selon les métadonnées de l’élément `Culture`. Chacun de ces lots est passé à la tâche `AL`, qui crée un assembly de sortie pour chaque lot. L’utilisation du traitement par lot sur l’attribut `Outputs` de l’élément `Target` permet à [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] de déterminer si chaque lot est à jour avant d’exécuter la cible. Si vous n’utilisez pas le traitement par lot des cibles, les deux lots d’éléments sont exécutés par la tâche chaque fois que la cible est exécutée.  
  
```  
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
 [Guide pratique pour effectuer des générations incrémentielles](../msbuild/how-to-build-incrementally.md)   
 [Traitement par lot MSBuild](../msbuild/msbuild-batching.md)   
 [Target, élément (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Métadonnées d’éléments dans le traitement par lots de tâches](../msbuild/item-metadata-in-task-batching.md)



