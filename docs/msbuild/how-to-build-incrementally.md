---
title: "How to: Build Incrementally | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, incremental builds"
  - "incremental builds"
  - "MSBuild, building incrementally"
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# How to: Build Incrementally
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous générez un gros projet, il importe que les composants déjà générés et qui demeurent à jour ne soient pas générés à nouveau.  Si toutes les cibles sont générées à chaque fois, chaque génération nécessitera un temps plus long.  Pour activer les générations incrémentielles \(générations dans lesquelles seules les cibles obsolètes ou n'ayant pas été déjà générées sont régénérées\), [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\) peut comparer les horodatages des fichiers d'entrée avec les horodatages des fichiers de sortie et déterminer si la cible doit être ignorée, générée intégralement ou régénérée partiellement.  Toutefois, il doit exister un mappage un\-à\-un entre les entrées et les sorties.  Vous pouvez utiliser des transformations pour permettre aux cibles d'identifier ce mappage direct.  Pour plus d'informations sur les transformations, consultez [Transforms](../msbuild/msbuild-transforms.md).  
  
## Spécification des entrées et des sorties  
 Une cible peut être générée de façon incrémentielle si les entrées et les sorties sont spécifiées dans le fichier projet.  
  
#### Pour spécifier les entrées et les sorties d'une cible  
  
-   Utilisez les attributs `Inputs` et `Outputs` de l'élément `Target`.  Par exemple :  
  
    ```  
    <Target Name="Build"  
        Inputs="@(CSFile)"  
        Outputs="hello.exe">  
    ```  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] peut comparer les horodatages des fichiers d'entrée avec ceux des fichiers de sortie et déterminer s'il faut ignorer, générer ou régénérer partiellement la cible.  Dans l'exemple suivant, si un fichier de la liste d'éléments `@(CSFile)` est plus récent que le fichier hello.exe, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] exécute la cible, sinon, il l'ignore :  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Lorsque les entrées et sorties sont spécifiées dans une cible, chaque sortie est mappée avec une seule entrée ou il n'existe pas de mappage direct entre les sorties et entrées.  Dans la tâche [Csc Task](../msbuild/csc-task.md) précédente, par exemple, la sortie hello.exe ne peut pas être mappée avec une entrée unique – elle dépend de fait de toutes les entrées.  
  
> [!NOTE]
>  Une cible dans laquelle il n'existe pas de mappage direct entre les entrées et les sorties sera toujours générée plus fréquemment qu'une cible dans laquelle chaque sortie ne peut être mappée qu'avec une seule entrée, parce que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ne peut pas déterminer les sorties qui doivent être régénérées si certaines des entrées ont changé.  
  
 Les tâches dans lesquelles vous pouvez identifier un mappage direct entre les sorties et les entrées, comme [LC Task](../msbuild/lc-task.md), sont mieux adaptées aux générations incrémentielles, à l'inverse des tâches telles que `Csc` et [Vbc](../msbuild/vbc-task.md), qui produisent un seul assembly de sortie à partir de plusieurs entrées.  
  
## Exemple  
 L'exemple suivant utilise un projet qui génère des fichiers d'aide pour un système d'aide éventuel.  Le projet fonctionne en convertissant les fichiers source .txt en fichiers .content intermédiaires, qui sont ensuite combinés avec les fichiers de métadonnées XML pour produire le dernier fichier .help utilisé par le système d'aide.  Le projet utilise les tâches hypothétiques suivantes :  
  
-   `GenerateContentFiles` : convertit des fichiers .txt en fichiers .content.  
  
-   `BuildHelp` : combine des fichiers .content et des fichiers de métadonnées XML pour générer le dernier fichier .help.  
  
 Le projet utilise les transformations pour créer un mappage univoque entre les entrées et les sorties de la tâche `GenerateContentFiles`.  Pour plus d’informations, consultez [Transforms](../msbuild/msbuild-transforms.md).  De même, l'élément `Output` est défini de façon à utiliser automatiquement les sorties de la tâche `GenerateContentFiles` comme entrées de la tâche `BuildHelp`.  
  
 Ce fichier projet contient à la fois les cibles `Convert` et `Build`.  Les tâches `GenerateContentFiles` et `BuildHelp` sont placées respectivement dans les cibles `Convert` et `Build` afin que chaque cible puisse être générée de façon incrémentielle.  En utilisant l'élément `Output`, les sorties de la tâche `GenerateContentFiles` sont placées dans la liste d'éléments `ContentFile`, où elles peuvent être utilisées comme entrées pour la tâche `BuildHelp`.  En utilisant l'élément `Output` de cette façon, vous pouvez utiliser automatiquement les sorties d'une tâche comme entrées d'une autre tâche – vous n'avez pas à répertorier manuellement les éléments ou les listes d'éléments dans chaque tâche.  
  
> [!NOTE]
>  Bien que la cible `GenerateContentFiles` puisse être générée de façon incrémentielle, toutes les sorties de cette cible sont toujours requises comme entrées de la cible `BuildHelp`.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fournit automatiquement toutes les sorties d'une cible comme entrées d'une autre cible lorsque vous utilisez l'élément `Output`.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFile Include="\metadata\*.xml"/>  
    </ItemGroup>  
  
    <Target Name = "Convert"  
        Inputs="@(TXTFile)"  
        Outputs="@(TXTFile->'%(Filename).content')">  
  
        <GenerateContentFiles  
            Sources = "@(TXTFile)">  
            <Output TaskParameter = "OutputContentFiles"  
                ItemName = "ContentFiles"/>  
        </GenerateContentFiles>  
    </Target>  
  
    <Target Name = "Build" DependsOnTargets = "Convert"  
        Inputs="@(ContentFiles);@(XMLFiles)"  
        Outputs="$(MSBuildProjectName).help">  
  
        <BuildHelp  
            ContentFiles = "@(ContentFiles)"  
            MetadataFiles = "@(XMLFile)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## Voir aussi  
 [Targets](../msbuild/msbuild-targets.md)   
 [Target, élément \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Transforms](../msbuild/msbuild-transforms.md)   
 [Csc Task](../msbuild/csc-task.md)   
 [Vbc Task](../msbuild/vbc-task.md)