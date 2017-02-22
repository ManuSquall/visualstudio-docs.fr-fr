---
title: "Target, &#233;l&#233;ment (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Target"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Target (élément MSBuild)"
  - "<Target> (élément MSBuild)"
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Target, &#233;l&#233;ment (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contient un ensemble de tâches que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] doit exécuter de façon séquentielle.  
  
## Syntaxe  
  
```  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>… </PropertyGroup>  
    <ItemGroup>… </ItemGroup>  
    <OnError... />  
</Target>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Name`|Attribut requis.<br /><br /> Nom de la cible.|  
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer.  Si la condition a la valeur `false`, la cible n'exécutera pas le corps de la cible ou toute cible définie dans l'attribut `DependsOnTargets`.  Pour plus d'informations sur les conditions, consultez [Conditions](../msbuild/msbuild-conditions.md).|  
|`Inputs`|Attribut facultatif.<br /><br /> Les fichiers que le formulaire entre dans cette cible.  Plusieurs fichiers sont séparés par des points\-virgules.  Les horodatages des fichiers sont comparés les horodatages des fichiers dans `Outputs` pour déterminer si `Target` est à jour.  Pour plus d'informations, consultez [Incremental Builds](../msbuild/incremental-builds.md), [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md) et [Transforms](../msbuild/msbuild-transforms.md).|  
|`Outputs`|Attribut facultatif.<br /><br /> Les fichiers que la forme affiche dans cette cible.  Plusieurs fichiers sont séparés par des points\-virgules.  Les horodatages des fichiers sont comparés les horodatages des fichiers dans `Inputs` pour déterminer si `Target` est à jour.  Pour plus d'informations, consultez [Incremental Builds](../msbuild/incremental-builds.md), [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md) et [Transforms](../msbuild/msbuild-transforms.md).|  
|`Returns`|Attribut facultatif.<br /><br /> L'ensemble des éléments qui seront disponibles pour les tâches invoquant cette cible, par exemple, les tâches MSBuild.  Les différentes cibles sont séparées par des points\-virgules.  Si les cibles dans le fichier n'ont aucun attribut d' `Returns`, les attributs de sorties sont utilisés à la place à cet effet.|  
|`KeepDuplicateOutputs`|Attribut boléen facultatif.<br /><br /> Si `true`, plusieurs références au même élément dans les retours de la cible sont stockés.  Par défaut, cet attribut a la valeur `false`.|  
|`BeforeTargets`|Attribut facultatif.<br /><br /> Liste séparée par points\-virgules de noms cibles. Une fois spécifié, indique que cette cible doit s'exécuter avant la cible ou les cibles spécifiées.  Cela permet l'auteur du projet étendre un jeu existant de cibles sans les modifier directement.  Pour plus d'informations, consultez [Ordre de génération des cibles](../msbuild/target-build-order.md).|  
|`AfterTargets`|Attribut facultatif.<br /><br /> Liste séparée par points\-virgules de noms cibles.  Une fois spécifié, indique que cette cible doit fonctionner après la cible ou les cibles spécifiées.  Cela permet l'auteur du projet étendre un jeu existant de cibles sans les modifier directement.  Pour plus d'informations, consultez [Ordre de génération des cibles](../msbuild/target-build-order.md).|  
|`DependsOnTargets`|Attribut facultatif.<br /><br /> Cibles à exécuter avant que cette cible puisse s'exécuter ou que l'analyse des dépendances de niveau supérieur soit effectuée.  Les différentes cibles sont séparées par des points\-virgules.|  
|`Label`|Attribut facultatif.<br /><br /> Un identificateur qui peut identifier ou le classement des éléments du système et d'utilisateur.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Tâche](../msbuild/task-element-msbuild.md)|Crée et exécute une instance d'une tâche [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Une cible peut ne contenir aucune tâche ou en contenir plusieurs.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Contient un jeu d'éléments définis par l'utilisateur d' `Property` .  À compter de.NET Framework 3.5, un élément d' `Target` peut contenir des éléments d' `PropertyGroup` .|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Contient un jeu d'éléments définis par l'utilisateur d' `Item` .  À compter de.NET Framework 3.5, un élément d' `Target` peut contenir des éléments d' `ItemGroup` .  Pour plus d'informations, consultez [Items](../msbuild/msbuild-items.md).|  
|[OnError](../msbuild/onerror-element-msbuild.md)|Pour exécuter une ou plusieurs cibles si l'attribut d' `ContinueOnError` est ErrorAndStop \(ou `false`\) pour une tâche.  Une cible peut ne contenir aucun élément `OnError` ou en contenir plusieurs.  Ces éléments `OnError`, s'ils existent, doivent être les derniers éléments dans l'élément `Target`.<br /><br /> Pour plus d'informations sur l'attribut d' `ContinueOnError`, consultez [Task Element \(MSBuild\)](../msbuild/task-element-msbuild.md).|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Notes  
 La première cible à exécuter est spécifiée au moment de l'exécution.  Les cibles peuvent avoir des dépendances avec d'autres cibles.  Par exemple, une cible de déploiement peut dépendre d'une cible de compilation.  Le moteur [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] exécute des dépendances dans l'ordre dans lequel elles s'affichent dans l'attribut `DependsOnTargets` de gauche à droite.  Pour plus d'informations, consultez [Targets](../msbuild/msbuild-targets.md).  
  
 Une cible est exécutée une seule fois pendant une génération, même si plusieurs cibles dépendent d'elle.  
  
 Si une cible est ignorée parce que son attribut `Condition` a la valeur `false`, il est possible qu'elle soit néanmoins exécutée si elle est appelée ultérieurement dans la génération et que son attribut `Condition` a la valeur `true` à ce moment\-là.  
  
 Avant MSBuild 4, `Target` retournait tous les éléments spécifiés dans l'attribut `Outputs`.  Pour ce faire, MSBuild devait enregistrer ces éléments dans des tâches de cas ultérieurement dans la génération.  Dans la mesure où il n'y avait aucun moyen d'indiquer quels objectifs avaient des sorties dont les appelants pouvaient avoir besoin, MSBuild accumulait tous les éléments de toutes les `Outputs` sur toutes les `Target`s invoquées.  Cela a provoqué des problèmes de mise à l'échelle pour les builds qui avaient un grand nombre d'éléments de sortie.  
  
 Si l'utilisateur spécifie un `Returns` sur n'importe quel élément `Target` dans un projet, seules les `Target`s ayant un attribut `Returns` enregistrent ces éléments.  
  
 `Target` peut contenir à la fois un attribut `Outputs` et un attribut `Returns`.  `Outputs` est utilisé avec `Inputs` pour déterminer si la cible est à jour.  Le cas échéant, `Returns` remplace la valeur de `Outputs` pour déterminer les éléments retournés aux appelants.  Si `Returns` n'est pas présent, alors `Outputs` seront mises à disposition des appelants, sauf dans le cas décrit précédemment.  
  
 Avant MSBuild 4, lorsqu'une `Target` incluait des références multiples au même élément dans ses `Outputs`, ces éléments en double étaient enregistrés.  Dans les builds volumineuses avec un grand nombre de sorties et de nombreuses interdépendances de projet, cela entraînait le gaspillage d'une grande quantité de mémoire, car les éléments en double étaient totalement inutiles.  Lorsque l'attribut d' `KeepDuplicateOutputs` a la valeur `true`, ces doublons sont stockés.  
  
## Exemple  
 L'exemple de code suivant illustre un élément `Target` qui exécute la tâche `Csc`.  
  
```  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## Voir aussi  
 [Targets](../msbuild/msbuild-targets.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)