---
title: "MSBuild Targets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, targets"
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# MSBuild Targets
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les cibles groupent les tâches dans un ordre particulier et permettent au processus de génération d'être pris en charge en unités plus petites.  Par exemple, une cible peut supprimer tous les fichiers dans le répertoire de sortie pour préparer la génération, pendant qu'une autre compile les entrées pour le projet et les place dans le répertoire vide.  Pour plus d'informations sur les tâches, consultez [Tasks](../msbuild/msbuild-tasks.md).  
  
## Déclaration des cibles dans le fichier projet  
 Les cibles sont déclarées dans un fichier projet avec l'élément [Target](../msbuild/target-element-msbuild.md).  Par exemple, le code XML suivant crée une cible nommée Construct, qui appelle ensuite la tâche Csc avec le type d'élément Compile.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Comme les propriétés MSBuild, les cibles peuvent être redéfinies.  Par exemple :  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Si AfterBuild s'exécute, il affiche uniquement « Second occurrence ».  
  
## Ordre de génération des cibles  
 Les cibles doivent être classées si l'entrée d'une cible dépend de la sortie d'une autre cible.  Il existe plusieurs méthodes pour spécifier l'ordre d'exécution des cibles.  
  
-   Cibles initiales  
  
-   Cibles par défaut  
  
-   Première cible  
  
-   Dépendances cible  
  
-   `BeforeTargets` et `AfterTargets` \(MSBuild 4.0\)  
  
 Une cible ne s'exécute jamais deux fois pendant une même build, même si une cible suivante dépend d'elle dans la génération.  Une fois qu'une cible s'est exécutée, sa contribution à la génération est terminée.  
  
 Pour plus d'informations sur l'ordre de génération des cibles, consultez [Ordre de génération des cibles](../msbuild/target-build-order.md).  
  
## Traitement par lots de cible  
 Un élément cible peut avoir un attribut `Outputs` qui spécifie des métadonnées sous la forme %\(Métadonnées\).  Si tel est le cas, MSBuild exécute la cible une fois pour chaque valeur de métadonnées unique, en regroupant ou en « traitant par lot » les éléments qui ont cette valeur de métadonnées.  Par exemple :  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 traite par lot les éléments Reference par leurs métadonnées RequiredTargetFramework.  La sortie de la cible se présente comme suit :  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
  
```  
  
 Le traitement par lots des cibles est rarement utilisé dans les générations réelles.  Le traitement par lots de tâches est plus courant.  Pour plus d’informations, consultez [Batching](../msbuild/msbuild-batching.md).  
  
## Builds incrémentielles  
 Les builds incrémentielles sont des builds optimisées afin que les cibles possédant des fichiers de sortie à jour par rapport à leurs fichiers d'entrée correspondants ne soient pas exécutées.  Un élément cible peut avoir les deux attributs `Inputs` et `Outputs`, indiquant les éléments que la cible attend comme entrée et les éléments produits comme sortie.  
  
 Si tous les éléments de sortie sont à jour, MSBuild ignore la cible, ce qui améliore considérablement la vitesse de génération.  C'est ce qu'on appelle une génération incrémentielle de la cible.  Si seuls certains fichiers sont à jour, MSBuild exécute la cible sans les éléments à jour.  C'est ce qu'on appelle une génération incrémentielle partielle de la cible.  Pour plus d’informations, consultez [Incremental Builds](../msbuild/incremental-builds.md).  
  
## Voir aussi  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [How to: Use the Same Target in Multiple Project Files](../Topic/How%20to:%20Use%20the%20Same%20Target%20in%20Multiple%20Project%20Files.md)