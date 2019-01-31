---
title: Tâche MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aea567014e32930e25960b069d2b755e2c0212b2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923053"
---
# <a name="msbuild-task"></a>MSBuild (tâche)
Génère des projets [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] à partir d’un autre projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `MSBuild` .  


| Paramètre | Description |
|-----------------------------------| - |
| `BuildInParallel` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, les projets spécifiés dans le paramètre `Projects` sont générés en parallèle dans la mesure du possible. La valeur par défaut est `false`. |
| `Projects` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les fichiers projet à générer. |
| `Properties` | Paramètre `String` facultatif.<br /><br /> Liste délimitée par des points-virgules de paires nom/valeur de propriété à appliquer en tant que propriétés globales au projet enfant. Si vous spécifiez ce paramètre, son fonctionnement revient à définir des propriétés dotées du commutateur **-property** lors du build avec [*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Par exemple :<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Si vous transmettez des propriétés au projet via le paramètre `Properties`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] crée une instance du projet même si le fichier projet a déjà été chargé. Si une instance du projet a été créée, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] la considère comme un autre projet pourvu de propriétés globales différentes qui peut être généré en parallèle avec d’autres instances du projet. Par exemple, une configuration Release peut être générée en même temps qu’une configuration Debug. |
| `RebaseOutputs` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, les chemins d’accès relatifs des éléments de sortie cibles des projets générés sont modifiés par rapport au projet appelant. La valeur par défaut est `false`. |
| `RemoveProperties` | Paramètre `String` facultatif.<br /><br /> Spécifie l’ensemble des propriétés globales à supprimer. |
| `RunEachTargetSeparately` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, la tâche [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] appelle une à une chaque cible de la liste transmise à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], au lieu de les appeler toutes en même temps. Définir ce paramètre sur `true` garantit que les cibles ultérieures seront appelées même en cas d’échec des cibles précédemment appelées. Dans le cas contraire, une erreur de génération arrêterait l’appel de toutes les cibles suivantes. La valeur par défaut est `false`. |
| `SkipNonexistentProjects` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, les fichiers projet qui n’existent pas sur le disque sont ignorés. Dans le cas contraire, ces projets provoquent une erreur. |
| `StopOnFirstFailure` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, en cas d’échec de génération de l’un des projets, aucun autre projet n’est généré. Pour le moment, cela n’est pas pris en charge lors de la génération en parallèle (avec plusieurs processeurs). |
| `TargetAndPropertyListSeparators` | Paramètre `String[]` facultatif.<br /><br /> Spécifie une liste de cibles et de propriétés en tant que métadonnées d’élément `Project`. Avant le traitement, les séparateurs sont retirés de la séquence d’échappement. Par exemple, %3B (caractère « ; » inséré dans une séquence d’échappement) est traité comme s’il s’agissait du caractère « ; » sans séquence d’échappement. |
| `TargetOutputs` | Paramètre de sortie en lecture seule <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Retourne les sorties des cibles générées à partir de tous les fichiers projet. Seules les sorties des cibles spécifiées sont retournées. Les sorties qui peuvent exister sur les cibles dont dépendent ces cibles ne sont pas retournées.<br /><br /> Le paramètre `TargetOutputs` contient également les métadonnées suivantes :<br /><br /> -   `MSBuildSourceProjectFile` : fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] qui contient la cible qui a défini les sorties.<br />-   `MSBuildSourceTargetName` : cible qui a défini les sorties. **Remarque :**  Si vous souhaitez identifier les sorties de chaque fichier projet ou de chaque cible séparément, exécutez la tâche `MSBuild` séparément pour chaque fichier projet ou cible. Si vous exécutez la tâche `MSBuild` une seule fois pour générer tous les fichiers projet, les sorties de toutes les cibles sont collectées dans un seul tableau. |
| `Targets` | Paramètre `String` facultatif.<br /><br /> Spécifie la ou les cibles à générer dans les fichiers projet. Utilisez un point-virgule pour séparer les noms de cibles dans la liste. Si aucune cible n’est spécifiée dans la tâche `MSBuild`, les cibles par défaut spécifiées dans les fichiers projet sont créées. **Remarque :**  Les cibles doivent exister dans tous les fichiers projet. Si tel n’est pas le cas, une erreur de génération se produit. |
| `ToolsVersion` | Paramètre `String` facultatif.<br /><br /> Spécifie la `ToolsVersion` à utiliser lors de la génération des projets transmis à cette tâche.<br /><br /> Permet à une tâche [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de générer un projet qui cible une version différente de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de celle spécifiée dans le projet. Les valeurs valides sont `2.0`, `3.0` et `3.5`. La valeur par défaut est `3.5`. |
| `UnloadProjectsOnCompletion` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, le projet doit être déchargé une fois l’opération terminée. |
| `UseResultsCache` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, le résultat mis en cache est retourné, le cas échéant.<br /><br />  Si la tâche MSBuild est exécutée, son résultat est mis en cache dans une étendue. <br /><br /> (ProjectFileName, GlobalProperties)[TargetNames]<br /><br /> en tant que liste d’éléments de génération. |

## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).  

 Contrairement à l’utilisation de la [tâche Exec](../msbuild/exec-task.md) pour démarrer *MSBuild.exe*, cette tâche utilise le même processus [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pour générer les projets enfants. La liste des cibles déjà générées qui peuvent être ignorées est partagée entre la génération parente et les générations enfants. Cette tâche est également plus rapide, car aucun nouveau processus [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] n’est créé.  

 Cette tâche peut traiter non seulement les fichiers projet, mais également les fichiers solution.  

 Toute configuration requise par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pour permettre la génération simultanée des projets, même si la configuration implique une infrastructure distante (par exemple, des ports, protocoles, délais d’attente, tentatives, etc.) doit être rendue configurable à l’aide d’un fichier de configuration. Dans la mesure du possible, il convient de spécifier les éléments de configuration comme paramètres de tâche dans la tâche `MSBuild`.  

 Depuis [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, les projets solution surfacent TargetOutputs depuis tous les sous-projets générés.  

## <a name="pass-properties-to-projects"></a>Transmettre des propriétés aux projets  
 Dans les versions de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] antérieures à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, la transmission des différents ensembles de propriétés aux différents projets répertoriés dans l’élément [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] était difficile. Si vous utilisiez l’attribut Properties de la [tâche MSBuild](../msbuild/msbuild-task.md), son paramètre était appliqué à tous les projets générés à moins que vous n’ayez traité par lot la [tâche MSBuild](../msbuild/msbuild-task.md) et fourni de façon conditionnelle des propriétés différentes pour chaque projet de la liste d’éléments.  

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 propose néanmoins deux nouveaux éléments de métadonnées réservés, Properties et AdditionalProperties, qui vous permettent de passer de manière flexible les différentes propriétés de plusieurs projets en cours de génération à l’aide de la [tâche MSBuild](../msbuild/msbuild-task.md).  

> [!NOTE]
>  Ces nouveaux éléments de métadonnées s’appliquent uniquement aux éléments transmis dans l’attribut Projects de la [tâche MSBuild](../msbuild/msbuild-task.md).  

## <a name="multi-processor-build-benefits"></a>Avantages de la génération multiprocesseur  
 L’un des principaux avantages liés à l’utilisation de ces nouvelles métadonnées se présente lorsque vous générez vos projets en parallèle sur un système multiprocesseur. Les métadonnées vous permettent de consolider tous les projets dans un seul et même appel de [tâche MSBuild](../msbuild/msbuild-task.md) sans devoir effectuer de traitement par lot ou de tâches [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] conditionnelles. Si vous appelez une seule [tâche MSBuild](../msbuild/msbuild-task.md), tous les projets répertoriés dans l’attribut Projects sont générés en parallèle. (Toutefois cela se produit uniquement si l’attribut `BuildInParallel=true` est présent dans la [tâche MSBuild](../msbuild/msbuild-task.md).) Pour plus d’informations, consultez [Générer plusieurs projets parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  

## <a name="properties-metadata"></a>Métadonnées Properties  
 Lorsque vous générez plusieurs fichiers solution à l’aide de la [tâche MSBuild](../msbuild/msbuild-task.md), il est courant d’utiliser uniquement différentes configurations de build. Vous souhaiterez peut-être générer la solution a1 à l’aide de la configuration Debug, et la solution a2 à l’aide de la configuration Release. Dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, ce fichier projet ressemblerait à ce qui suit :  

> [!NOTE]
>  Dans l’exemple suivant, « ... » représente des fichiers solution supplémentaires.  

### <a name="aproj"></a>a.proj  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  

 En utilisant les métadonnées Properties, vous pouvez néanmoins simplifier cela pour utiliser une seule [tâche MSBuild](../msbuild/msbuild-task.md), comme indiqué ci-après :  

### <a name="aproj"></a>a.proj  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln...">  
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

 \- ou -  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln..."/>  
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

## <a name="additionalproperties-metadata"></a>Métadonnées AdditionalProperties  
 Considérez le scénario suivant où vous générez deux fichiers solution à l’aide de la [tâche MSBuild](../msbuild/msbuild-task.md), tous deux utilisant la configuration Release, mais l’un avec l’architecture x86 et l’autre avec l’architecture ia64. Dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, vous devriez créer plusieurs instances de la [tâche MSBuild](../msbuild/msbuild-task.md) : l’une pour générer le projet à l’aide de la configuration Release avec l’architecture x86, et l’autre à l’aide de la configuration Release avec l’architecture ia64. Votre fichier projet ressemblerait à ce qui suit :  

### <a name="aproj"></a>a.proj  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  

 En utilisant les métadonnées AdditionalProperties, vous pouvez simplifier cela pour utiliser une seule [tâche MSBuild](../msbuild/msbuild-task.md) de la manière suivante :  

### <a name="aproj"></a>a.proj  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln...">  
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

## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche `MSBuild` pour générer les projets spécifiés par la collection d’éléments `ProjectReferences`. Les sorties cibles obtenues sont stockées dans la collection d’éléments `AssembliesBuiltByChildProjects`.  

```xml  
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

## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)