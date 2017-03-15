---
title: "MSBuild, t&#226;che | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#MSBuild"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild (tâche MSBuild)"
  - "MSBuild, tâche MSBuild"
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# MSBuild, t&#226;che
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Génère des projets [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] depuis un autre projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `MSBuild`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`BuildInParallel`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, les projets spécifiés dans le paramètre `Projects` sont générés en parallèle si possible.  La valeur par défaut est `false`.|  
|`Projects`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les fichiers projet à générer.|  
|`Properties`|Paramètre `String` facultatif.<br /><br /> Liste délimitée par des points\-virgules de paires nom\/valeur de propriété à appliquer en tant que propriétés globales au projet enfant.  Lorsque vous spécifiez ce paramètre, cela équivaut, d'un point de vue fonctionnel, à définir des propriétés possédant le commutateur **\/property** lorsque vous générez avec [MSBuild.exe](../msbuild/msbuild-command-line-reference.md).  Par exemple :<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Lorsque vous passez des propriétés au projet via le paramètre `Properties`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] crée une nouvelle instance du projet, même si le fichier projet a déjà été chargé.  Lorsqu'une nouvelle instance du projet est créée, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] traite cette instance comme un projet différent avec des propriétés globales différentes et qui peut être généré en parallèle avec d'autres instances du projet.  Par exemple, une configuration Release pourrait être générée en même temps qu'une configuration Debug.|  
|`RebaseOutputs`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, les chemins d'accès relatifs des éléments de sortie cibles des projets créés sont modifiés par rapport au projet appelant.  La valeur par défaut est `false`.|  
|`RemoveProperties`|Paramètre `String` facultatif.<br /><br /> Spécifie le jeu de propriétés globales à supprimer.|  
|`RunEachTargetSeparately`|Paramètre `Boolean` facultatif.<br /><br /> Si le paramètre a la valeur `true`, la tâche [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] appelle une par une chaque cible de la liste passée à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], plutôt que de les appeler en même temps.  Affecter à ce paramètre la valeur `true` garantit que les cibles sont toutes appelées même en cas d'échec de l'appel d'une des cibles.  Sinon, une erreur de build arrêterait l'appel de toutes les cibles consécutives.  La valeur par défaut est `false`.|  
|`SkipNonexistentProjects`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, les fichiers projet qui n'existent pas sur le disque seront ignorés.  Sinon, ces projets provoqueront une erreur.|  
|`StopOnFirstFailure`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, lorsque la génération de l'un des projets échoue, plus aucun projet n'est généré.  Actuellement, cela n'est pas pris en charge lors de la génération en parallèle \(avec plusieurs processeurs\).|  
|`TargetAndPropertyListSeparators`|Paramètre `String[]` facultatif.<br /><br /> Spécifie une liste de cibles et de propriétés comme des métadonnées d'élément de `Project`\).  Les séparateurs seront placés hors d'une séquence d'échappement avant le traitement.  par.. exemple %3B d'échappement \(« ; "\) est traité comme s'il s'agissait ONU\- d'échappement « ;  ».|  
|`TargetOutputs`|Paramètre de sortie en lecture seule <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Retourne les sorties des cibles générées à partir de tous les fichiers projet.  Seules les sorties provenant des cibles spécifiées sont retournées, pas les sorties qui peuvent exister sur les cibles sur lesquelles dépendent ces cibles.<br /><br /> Le paramètre `TargetOutputs` contient également les métadonnées suivantes :<br /><br /> -   `MSBuildSourceProjectFile` : le fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] qui contient la cible qui a défini les sorties ;<br />-   `MSBuildSourceTargetName` : la cible qui a défini les sorties. **Note:**  Si vous souhaitez distinguer les sorties de chaque fichier projet ou cible, exécutez la tâche `MSBuild` séparément pour chaque fichier projet ou cible.  Si vous exécutez une seule fois la tâche `MSBuild` pour générer tous les fichiers projet, les sorties de toutes les cibles sont collectées dans un seul tableau.|  
|`Targets`|Paramètre `String` facultatif.<br /><br /> Spécifie la ou les cibles à générer dans les fichiers projet.  Utilisez un point\-virgule pour séparer une liste de noms cibles.  Si aucune cible n'est spécifiée dans la tâche `MSBuild`, cette dernière génère les cibles par défaut spécifiées dans les fichiers projet. **Note:**  Les cibles doivent exister dans tous les fichiers projet,  sans quoi une erreur de build se produit.|  
|`ToolsVersion`|Paramètre `String` facultatif.<br /><br /> Spécifie la `ToolsVersion` à utiliser lorsque des projets de génération sont passés à cette tâche.<br /><br /> Permet à une tâche [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de générer un projet qui vise une version différente du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de celle spécifiée dans le projet.  Les valeurs valides sont `2.0`, `3.0` et `3.5`.  La valeur par défaut est `3.5`|  
|`UnloadProjectsOnCompletion`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, le projet doit être déchargé une fois l'opération terminée.|  
|`UseResultsCache`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, le résultat mis en cache sera retourné, le cas échéant.  Si la tâche MSBuild est exécutée, son résultat est mis en cache dans une portée \(NomFichierProjet, PropriétésGlobales\)\[NomsCibles\]<br /><br /> comme une liste d'éléments de génération|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
 Contrairement à ce qui se passe lors de l'utilisation de la [Exec Task](../msbuild/exec-task.md) pour appeler MSBuild.exe, cette tâche utilise le même processus [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pour générer les projets enfants.  La liste de cibles déjà générées qu'il est possible d'ignorer est partagée entre les générations parentes et enfants.  Cette tâche est également plus rapide car aucun nouveau processus [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] n'est créé.  
  
 Cette tâche peut traiter non seulement les fichiers projet, mais aussi les fichiers solution.  
  
 Toute configuration requise par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pour permettre à des projets d'être générés en même temps, même si la configuration implique une infrastructure distante \(par exemple : ports, protocoles, délais d'attente, tentatives, etc.\), doit être configurable via un fichier de configuration.  Lorsque cela est possible, les éléments de configuration doivent être en mesure d'être spécifiés comme paramètres de tâche de la tâche `MSBuild`.  
  
 Depuis [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, les projets Solution font maintenant ressurgir TargetOutputs parmi tous les sous\-projets qu'ils génèrent.  
  
## Passage de propriétés aux projets  
 Dans les versions de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] antérieures à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, le passage de différents jeux de propriétés aux différents projets répertoriés dans l'élément [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] présentait quelques difficultés.  Si vous utilisiez l'attribut Properties de [MSBuild Task](../msbuild/msbuild-task.md), cette configuration était alors appliquée à tous les projets construits à moins que vous n'ayez regroupé la [MSBuild Task](../msbuild/msbuild-task.md) et attribué, de manière conditionnelle, différentes propriétés à chaque projet de la liste d'éléments.  
  
 Toutefois, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 fournit deux nouveaux éléments de métadonnées réservés, Properties et AdditionalProperties, qui vous offrent une méthode flexible pour passer des propriétés différentes à différents projets construits à l'aide de la [MSBuild Task](../msbuild/msbuild-task.md).  
  
> [!NOTE]
>  Ces nouveaux éléments de métadonnées sont uniquement applicables aux éléments passés dans l'attribut Projects de la [MSBuild Task](../msbuild/msbuild-task.md).  
  
## Avantages de la génération multiprocesseur  
 L'un des avantages majeurs de l'utilisation de ces nouvelles métadonnées est flagrant lorsque vous générés vos projets en parallèle sur un système multiprocesseur.  Les métadonnées vous permettent de consolider tous les projets en un appel de [MSBuild Task](../msbuild/msbuild-task.md) sans devoir effectuer de traitement par lot ou définir des tâches [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] conditionnelles.  Et lorsque vous appelez uniquement une [MSBuild Task](../msbuild/msbuild-task.md)unique, tous les projets répertoriés dans l'attribut Projects seront générés en parallèle.  \(Toutefois, uniquement si l'attribut `BuildInParallel=true` est présent dans la [MSBuild Task](../msbuild/msbuild-task.md).\) Pour plus d'informations, consultez [Building Multiple Projects in Parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## Métadonnées Properties  
 Un scénario courant est lorsque vous générez plusieurs fichiers solution à l'aide de la [MSBuild Task](../msbuild/msbuild-task.md) avec différentes configurations de build.  Vous voulez peut\-être générer la solution a1 en configuration Debug et la solution a2 en configuration Release.  Dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, le fichier projet ressemblerait à ceci :  
  
> [!NOTE]
>  Dans l'exemple suivant, "…" représente des fichiers solution supplémentaires.  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 En utilisant les métadonnées Properties, vous pouvez pourtant simplifier ceci en une [MSBuild Task](../msbuild/msbuild-task.md) unique, comme indiqué ci\-après :  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  
  
 \- ou \-  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…"/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  
  
## Métadonnées AdditionalProperties  
 Considérez le scénario suivant où vous générez deux fichiers solution à l'aide de la [MSBuild Task](../msbuild/msbuild-task.md), tous deux en configuration Release, mais un sur l'architecture x86 et l'autre sur l'architecture ia64.  Dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, vous devriez créer plusieurs instances de la [MSBuild Task](../msbuild/msbuild-task.md) : une pour générer le projet en configuration Release avec l'architecture x86, l'autre en configuration Release avec l'architecture ia64.  Votre fichier projet ressemblerait à ceci :  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln…" Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 En utilisant les métadonnées AdditionalProperties, vous pouvez simplifier ceci pour n'utiliser qu'une [MSBuild Task](../msbuild/msbuild-task.md) unique, de la manière suivante :  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
## Exemple  
 L'exemple suivant utilise la tâche `MSBuild` pour générer les projets spécifiés par la collection d'éléments `ProjectReferences`.  Les sorties cibles résultantes sont stockées dans la collection d'éléments `AssembliesBuiltByChildProjects`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  
  
    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  
  
</Project>  
```  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)