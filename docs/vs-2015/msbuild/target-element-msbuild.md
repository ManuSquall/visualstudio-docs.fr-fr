---
title: Élément Target (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Target
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Target element [MSBuild]
- <Target> element [MSBuild]
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc4224930782e24b20d3e9720c517304b0153f2d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173405"
---
# <a name="target-element-msbuild"></a>Target, élément (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Contient un ensemble de tâches que [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] doit exécuter séquentiellement.  
  
 \<Project>  
 \<Target>  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Attribut requis.<br /><br /> Nom de la cible.|  
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer. Si la condition a la valeur `false`, la cible n’exécute pas le corps de la cible ni les cibles définies dans l’attribut `DependsOnTargets`. Pour plus d’informations sur les conditions, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|  
|`Inputs`|Attribut facultatif.<br /><br /> Fichiers qui constituent les entrées dans cette cible. Plusieurs fichiers sont séparés par des points-virgules. Les horodateurs des fichiers doivent être comparés à ceux des fichiers dans `Outputs` pour déterminer si la `Target` est à jour. Pour plus d’informations, consultez les articles [Incremental Builds (Générations incrémentielles)](../msbuild/incremental-builds.md), [How to: Build Incrementally (Comment : effectuer des générations incrémentielles)](../msbuild/how-to-build-incrementally.md) et [Transforms (Transformations MSBuild)](../msbuild/msbuild-transforms.md).|  
|`Outputs`|Attribut facultatif.<br /><br /> Fichiers qui constituent les sorties dans cette cible. Plusieurs fichiers sont séparés par des points-virgules. Les horodateurs des fichiers doivent être comparés à ceux des fichiers dans `Inputs` pour déterminer si la `Target` est à jour. Pour plus d’informations, consultez les articles [Incremental Builds (Générations incrémentielles)](../msbuild/incremental-builds.md), [How to: Build Incrementally (Comment : effectuer des générations incrémentielles)](../msbuild/how-to-build-incrementally.md) et [Transforms (Transformations MSBuild)](../msbuild/msbuild-transforms.md).|  
|`Returns`|Attribut facultatif.<br /><br /> Ensemble des éléments qui seront disponibles pour les tâches qui appellent cette cible, par exemple, les tâches MSBuild. Plusieurs cibles sont séparées par des points-virgules. Si les cibles du fichier sont dépourvues d’attributs `Returns`, les attributs Output sont utilisés à la place à cet effet.|  
|`KeepDuplicateOutputs`|Attribut booléen facultatif.<br /><br /> Si `true`, plusieurs références au même élément dans l’attribut Returns de la cible sont enregistrées.  Par défaut, cet attribut est défini sur `false`.|  
|`BeforeTargets`|Attribut facultatif.<br /><br /> Liste de noms de cibles séparés par des points-virgules.  Si spécifié, indique que cette cible doit être exécutée avant la ou les cibles spécifiées. L’auteur du projet peut alors étendre un ensemble existant de cibles sans les modifier directement. Pour plus d’informations, consultez l’article [Ordre de génération des cibles](../msbuild/target-build-order.md).|  
|`AfterTargets`|Attribut facultatif.<br /><br /> Liste de noms de cibles séparés par des points-virgules. Si spécifié, indique que cette cible doit être exécutée après la ou les cibles spécifiées. L’auteur du projet peut alors étendre un ensemble existant de cibles sans les modifier directement. Pour plus d’informations, consultez l’article [Ordre de génération des cibles](../msbuild/target-build-order.md).|  
|`DependsOnTargets`|Attribut facultatif.<br /><br /> Les cibles qui doivent être exécutées avant cette cible peuvent l’être, ou l’analyse des dépendances de niveau supérieur peut être effectuée. Plusieurs cibles sont séparées par des points-virgules.|  
|`Label`|Attribut facultatif.<br /><br /> Identificateur permettant d’identifier ou de classer les éléments système et utilisateur.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Task](../msbuild/task-element-msbuild.md)|Crée et exécute une instance d’une tâche [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Une cible peut ne contenir aucune tâche ou en contenir plusieurs.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Contient un ensemble d’éléments `Property` définis par l’utilisateur. Depuis .NET Framework 3.5, un élément `Target` peut contenir des éléments `PropertyGroup`.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Contient un ensemble d’éléments `Item` définis par l’utilisateur. Depuis .NET Framework 3.5, un élément `Target` peut contenir des éléments `ItemGroup`. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).|  
|[OnError](../msbuild/onerror-element-msbuild.md)|Provoque l’exécution d’une ou de plusieurs cibles si l’attribut `ContinueOnError` est défini sur ErrorAndStop (ou `false`) pour une tâche en échec. Une cible peut ne contenir aucun élément `OnError` ou en contenir plusieurs. Si des éléments `OnError` sont présents, il doit s’agir des derniers éléments de l’élément `Target`.<br /><br /> Pour plus d’informations sur l’attribut `ContinueOnError`, consultez l’article [Task Element (MSBuild) (Élément Task [MSBuild])](../msbuild/task-element-msbuild.md).|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
  
## <a name="remarks"></a>Notes  
 La première cible à exécuter est spécifiée au moment de l’exécution. Les cibles peuvent avoir des relations de dépendance avec d’autres cibles. Par exemple, une cible de déploiement dépend d’une cible de compilation. Le moteur [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] exécute des dépendances dans l’ordre dans lequel elles apparaissent dans l’attribut `DependsOnTargets`, de gauche à droite. Pour plus d’informations, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md).  
  
 Une cible est exécutée une seule fois pendant une génération, même si plusieurs cibles possèdent une relation de dépendance avec elle.  
  
 Si une cible est ignorée parce que son attribut `Condition` a la valeur `false`, elle peut toujours être exécutée si elle est appelée ultérieurement dans la génération et si son attribut `Condition` a la valeur `true` à ce moment-là.  
  
 Avant MSBuild 4, `Target` retournait tous les éléments qui étaient spécifiés dans l’attribut `Outputs`.  Pour ce faire, MSBuild devait enregistrer ces éléments dans le cas où les tâches ultérieures de la génération les demandaient. Comme aucun moyen ne permettait d’indiquer quelles cibles possédaient des sorties nécessaires aux appelants, MSBuild cumulait tous les éléments de toutes les `Outputs` sur toutes les `Target`s appelées. Cela engendrait des problèmes de mise à l’échelle des générations qui comportaient un grand nombre d’éléments de sortie.  
  
 Si l’utilisateur spécifie un attribut `Returns` sur un élément `Target` d’un projet, alors seules les `Target`s qui possèdent un attribut `Returns` enregistrent ces éléments.  
  
 Une `Target` peut contenir à la fois un attribut `Outputs` et un attribut `Returns`.  L’attribut `Outputs` est utilisé avec `Inputs` pour déterminer si la cible est à jour. Si l’attribut `Returns` est présent, il remplace la valeur de `Outputs` pour déterminer les éléments retournés aux appelants.  Si l’attribut `Returns` n’est pas présent, alors l’attribut `Outputs` est disponible pour les appelants, sauf dans le cas décrit précédemment.  
  
 Avant MSBuild 4, chaque fois qu’une `Target` contenait plusieurs références au même élément dans son attribut `Outputs`, ces éléments en double étaient enregistrés. Dans les générations très volumineuses pourvues d’un grand nombre de sorties et de nombreuses interdépendances de projets, cela provoquait la perte d’une grande quantité de mémoire, car les éléments en double n’étaient d’aucune utilité. Si l’attribut `KeepDuplicateOutputs` est défini sur `true`, ces doublons sont enregistrés.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant présente un élément `Target` qui exécute la tâche `Csc`.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md)   
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)



