---
title: "Item Metadata in Target Batching | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "batching [MSBuild]"
  - "MSBuild, target batching"
  - "target batching [MSBuild]"
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Item Metadata in Target Batching
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] a la capacité d'exécuter une analyse de dépendance sur les entrées et les sorties d'une cible de génération.  S'il est déterminé que les entrées ou les sorties de la cible sont à jour, la cible sera ignorée et la génération aura lieu.  Les éléments `Target` utilisent les attributs `Inputs` et `Outputs` pour spécifier les éléments à inspecter pendant l'analyse de dépendance.  
  
 Si une cible contient une tâche qui utilise des éléments traités par lots comme entrées ou sorties, l'élément `Target` de la cible doit utiliser le traitement par lots dans ses attributs `Inputs` ou `Outputs` pour permettre à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] d'ignorer les lots d'éléments qui sont déjà à jour.  
  
## Traitement par lots de cibles  
 L'exemple suivant contient une liste d'éléments nommée `Res` qui est divisée en deux lots basés sur les métadonnées d'élément `Culture`.  Chacun de ces lots est passé dans la tâche `AL`, qui crée un assembly de sortie pour chaque lot.  En utilisant le traitement par lot sur l'attribut `Outputs` de l'élément `Target`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] peut déterminer si chacun des lots individuels est à jour avant d'exécuter la cible.  Sans utiliser le traitement par lots des cibles, les deux lots d'éléments seraient exécutés tâche par tâche chaque fois que la cible est exécutée.  
  
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
  
## Voir aussi  
 [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md)   
 [Batching](../msbuild/msbuild-batching.md)   
 [Target, élément \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Item Metadata in Task Batching](../msbuild/item-metadata-in-task-batching.md)