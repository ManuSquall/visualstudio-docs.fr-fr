---
title: "MSBuild Batching | Microsoft Docs"
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
  - "MSBuild, batching"
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# MSBuild Batching
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] a la capacité de diviser les listes d'éléments en différentes catégories, ou lots, suivant les métadonnées d'éléments, et d'exécuter une cible ou une tâche une fois avec chaque lot.  
  
## Traitement par lots de tâches  
 Le traitement par lots de tâches vous permet de simplifier vos fichiers projet en vous offrant la possibilité de diviser les listes d'éléments en différents lots et de passer chacun de ces lots dans une tâche.  Cela signifie que pour un fichier projet, la tâche et ses attributs n'ont besoin d'être déclarés qu'une seule fois, même s'il peut être exécuté plusieurs fois.  
  
 Vous spécifiez que vous souhaitez que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] exécute le traitement par lots avec une tâche à l'aide de la notation %\(*ItemMetaDataName*\) dans l'un des attributs de tâche.  L'exemple suivant fractionne la liste d'éléments `Example` en lots en fonction de la valeur des métadonnées de l'élément `Color`, et passe séparément chacun des lots à la tâche `MyTask`.  
  
> [!NOTE]
>  Si vous ne référencez pas la liste d'éléments ailleurs dans les attributs de tâche ou si le nom des métadonnées est ambigu, vous pouvez utiliser la notation %\(*ItemCollection.ItemMetaDataName*\) pour qualifier pleinement la valeur des métadonnées d'élément à utiliser pour le traitement par lots.  
  
```  
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
  
 Pour des exemples de traitement par lots plus spécifiques, consultez [Item Metadata in Task Batching](../msbuild/item-metadata-in-task-batching.md).  
  
## Traitement par lots de cible  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vérifie si les entrées et les sorties d'une cible sont à jour avant d'exécuter la cible.  Si les entrées et les sorties sont à jour, la cible est ignorée.  Si une tâche dans une cible utilise le traitement par lots, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] doit déterminer si les entrées et les sorties de chaque lot d'éléments sont à jour.  Sinon, la cible est exécutée chaque fois qu'elle est atteinte.  
  
 L'exemple suivant illustre un élément `Target` qui contient un attribut `Outputs` avec la notation % \(*ItemMetaDataName*\).  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] divise la liste d'éléments `Example` en lots en fonction des métadonnées de l'élément `Color` et analyse les horodatages des fichiers de sortie de chaque lot.  Si les sorties d'un lot ne sont pas à jour, la cible est exécutée.  Sinon, la cible est ignorée.  
  
```  
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
  
 Pour obtenir un autre exemple de traitement par lots des cibles, consultez [Item Metadata in Target Batching](../msbuild/item-metadata-in-target-batching.md).  
  
## Fonctions de propriété utilisant des métadonnées  
 Le traitement par lot peut être contrôlé par des fonctions de propriété qui incluent des métadonnées.  Par exemple :  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 utilise <xref:System.IO.Path.Combine%2A> pour combiner un chemin d'accès au dossier racine à un chemin d'accès à l'élément Compile.  
  
 Les fonctions de propriété peuvent ne pas s'afficher dans les valeurs de métadonnées.  Par exemple :  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 n'est pas autorisé.  
  
 Pour plus d'informations sur les fonctions de propriété, consultez [Property Functions](../msbuild/property-functions.md).  
  
## Voir aussi  
 [ItemMetadata Element \(MSBuild\)](../msbuild/itemmetadata-element-msbuild.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Advanced Concepts](../msbuild/msbuild-advanced-concepts.md)