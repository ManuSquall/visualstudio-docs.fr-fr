---
title: Tâche MSBuild | Microsoft Docs
description: Découvrez comment la tâche MSBuild utilise le même processus MSBuild pour générer des projets enfants à partir d’un autre projet MSBuild.
ms.custom: SEO-VS-2020
ms.date: 07/30/2019
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4d1f9fe79ae5092992ff66ddaf5e10729e8b19a
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049063"
---
# <a name="msbuild-task"></a>MSBuild (tâche)

Génère des projets MSBuild à partir d’un autre projet MSBuild.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `MSBuild` .

| Paramètre | Description |
|-----------------------------------| - |
| `BuildInParallel` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, les projets spécifiés dans le paramètre `Projects` sont générés en parallèle dans la mesure du possible. La valeur par défaut est `false`. |
| `Projects` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les fichiers projet à générer. |
| `Properties` | Paramètre `String` facultatif.<br /><br /> Liste délimitée par des points-virgules de paires nom/valeur de propriété à appliquer en tant que propriétés globales au projet enfant. Lorsque vous spécifiez ce paramètre, il est fonctionnellement équivalent à la définition des propriétés qui ont le commutateur **-Property** quand vous générez avec [*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Par exemple :<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Lorsque vous transmettez des propriétés au projet via le `Properties` paramètre, MSBuild peut créer une nouvelle instance du projet même si le fichier projet a déjà été chargé. MSBuild crée une instance de projet unique pour un chemin d’accès de projet donné et un ensemble unique de propriétés globales. Par exemple, ce comportement vous permet de créer plusieurs tâches MSBuild qui appellent *myproject.proj* avec Configuration=Release, et vous obtenez une seule instance de *myproject.proj* (si aucune propriété unique n’est spécifiée dans la tâche). Si vous spécifiez une propriété qui n’a pas encore été vue par MSBuild, MSBuild crée une nouvelle instance du projet, qui peut être générée en parallèle avec d’autres instances du projet. Par exemple, une configuration Release peut être générée en même temps qu’une configuration Debug.|
| `RebaseOutputs` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, les chemins d’accès relatifs des éléments de sortie cibles des projets générés sont modifiés par rapport au projet appelant. La valeur par défaut est `false`. |
| `RemoveProperties` | Paramètre `String` facultatif.<br /><br /> Spécifie l’ensemble des propriétés globales à supprimer. |
| `RunEachTargetSeparately` | Paramètre `Boolean` facultatif.<br /><br /> Si `true` la valeur est, la tâche MSBuild appelle une par une chaque cible de la liste passée à MSBuild, plutôt qu’en même temps. Définir ce paramètre sur `true` garantit que les cibles ultérieures seront appelées même en cas d’échec des cibles précédemment appelées. Dans le cas contraire, une erreur de génération arrêterait l’appel de toutes les cibles suivantes. La valeur par défaut est `false`. |
| `SkipNonexistentProjects` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, les fichiers projet qui n’existent pas sur le disque sont ignorés. Dans le cas contraire, ces projets provoquent une erreur. |
|`SkipNonexistentTargets`|Paramètre `Boolean` facultatif.<br /><br /> Si `true` la, les fichiers projet qui existent mais qui ne contiennent pas le nommé `Targets` seront ignorés. Dans le cas contraire, ces projets provoquent une erreur. Introduit dans MSBuild 15,5.|
| `StopOnFirstFailure` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, en cas d’échec de génération de l’un des projets, aucun autre projet n’est généré. Pour le moment, cela n’est pas pris en charge lors de la génération en parallèle (avec plusieurs processeurs). |
| `TargetAndPropertyListSeparators` | Paramètre `String[]` facultatif.<br /><br /> Spécifie une liste de cibles et de propriétés en tant que métadonnées d’élément `Project`. Avant le traitement, les séparateurs sont retirés de la séquence d’échappement. Par exemple, %3B (caractère « ; » inséré dans une séquence d’échappement) est traité comme s’il s’agissait du caractère « ; » sans séquence d’échappement. |
| `TargetOutputs` | Paramètre de sortie en lecture seule <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Retourne les sorties des cibles générées à partir de tous les fichiers projet. Seules les sorties des cibles spécifiées sont retournées. Les sorties qui peuvent exister sur les cibles dont dépendent ces cibles ne sont pas retournées.<br /><br /> Le paramètre `TargetOutputs` contient également les métadonnées suivantes :<br /><br /> -   `MSBuildSourceProjectFile`: Fichier projet MSBuild qui contient la cible qui a défini les sorties.<br />-   `MSBuildSourceTargetName` : cible qui a défini les sorties. **Remarque :** si vous souhaitez identifier les sorties de chaque fichier projet ou de chaque cible séparément, exécutez la tâche `MSBuild` séparément pour chaque fichier projet ou cible. Si vous exécutez la tâche `MSBuild` une seule fois pour générer tous les fichiers projet, les sorties de toutes les cibles sont collectées dans un seul tableau. |
| `Targets` | Paramètre `String` facultatif.<br /><br /> Spécifie la ou les cibles à générer dans les fichiers projet. Utilisez un point-virgule pour séparer les noms de cibles dans la liste. Si aucune cible n’est spécifiée dans la tâche `MSBuild`, les cibles par défaut spécifiées dans les fichiers projet sont créées. **Remarque :** les cibles doivent exister dans tous les fichiers projet. Si tel n’est pas le cas, une erreur de génération se produit. |
| `ToolsVersion` | Paramètre `String` facultatif.<br /><br /> Spécifie la `ToolsVersion` à utiliser lors de la génération des projets transmis à cette tâche.<br /><br /> Permet à une tâche MSBuild de générer un projet qui cible une autre version du .NET Framework que celle spécifiée dans le projet. Les valeurs valides sont `2.0`, `3.0` et `3.5`. La valeur par défaut est `3.5`. |

## <a name="remarks"></a>Remarques

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

 Contrairement à l’utilisation de la [tâche exec](../msbuild/exec-task.md) pour démarrer *MSBuild.exe* , cette tâche utilise le même processus MSBuild pour générer les projets enfants. La liste des cibles déjà générées qui peuvent être ignorées est partagée entre la génération parente et les générations enfants. Cette tâche est également plus rapide, car aucun nouveau processus MSBuild n’est créé.

 Cette tâche peut traiter non seulement les fichiers projet, mais également les fichiers solution.

 Toute configuration requise par MSBuild pour permettre la génération de projets en même temps, même si la configuration implique une infrastructure à distance (par exemple, les ports, les protocoles, les délais d’attente, les nouvelles tentatives, etc.), doit être rendue configurable à l’aide d’un fichier de configuration. Dans la mesure du possible, il convient de spécifier les éléments de configuration comme paramètres de tâche dans la tâche `MSBuild`.

 À compter de MSBuild 3,5, les projets de solution sont maintenant en surface TargetOutputs à partir de tous les sous-projets qu’il génère.

## <a name="pass-properties-to-projects"></a>Transmettre des propriétés aux projets

 Dans les versions de MSBuild antérieures à MSBuild 3,5, le passage de différents ensembles de propriétés à différents projets listés dans l’élément MSBuild était délicat. Si vous avez utilisé l’attribut Properties de la [tâche MSBuild](../msbuild/msbuild-task.md), son paramètre a été appliqué à tous les projets en cours de génération, sauf si vous avez regroupé la [tâche MSBuild](../msbuild/msbuild-task.md) et fourni de manière conditionnelle des propriétés différentes pour chaque projet dans la liste d’éléments.

 MSBuild 3,5, toutefois, fournit deux nouveaux éléments de métadonnées réservés, Properties et AdditionalProperties, qui vous permettent de passer des propriétés différentes pour différents projets générés à l’aide de la [tâche MSBuild](../msbuild/msbuild-task.md).

> [!NOTE]
> Ces nouveaux éléments de métadonnées s’appliquent uniquement aux éléments passés dans l’attribut projects de la [tâche MSBuild](../msbuild/msbuild-task.md).

## <a name="multi-processor-build-benefits"></a>Avantages de la génération multiprocesseur

 L’un des principaux avantages liés à l’utilisation de ces nouvelles métadonnées se présente lorsque vous générez vos projets en parallèle sur un système multiprocesseur. Les métadonnées vous permettent de consolider tous les projets en un seul appel de [tâche MSBuild](../msbuild/msbuild-task.md) sans avoir à exécuter de tâches MSBuild conditionnelles ou de traitement par lot. Et lorsque vous appelez une seule [tâche MSBuild](../msbuild/msbuild-task.md), tous les projets listés dans l’attribut Projects sont générés en parallèle. (Toutefois, uniquement si l' `BuildInParallel=true` attribut est présent dans la [tâche MSBuild](../msbuild/msbuild-task.md).) Pour plus d’informations, consultez [générer plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Métadonnées Properties

 Quand elles sont spécifiées, les métadonnées Properties remplacent le paramètre Propriétés de la tâche, alors que les métadonnées [AdditionalProperties](#additionalproperties-metadata) sont ajoutées aux définitions du paramètre.

 Un scénario courant est lorsque vous générez plusieurs fichiers solution à l’aide de la [tâche MSBuild](../msbuild/msbuild-task.md), uniquement à l’aide de différentes configurations de Build. Vous souhaiterez peut-être générer la solution a1 à l’aide de la configuration Debug, et la solution a2 à l’aide de la configuration Release. Dans MSBuild 2,0, ce fichier projet ressemble à ce qui suit :

> [!NOTE]
> Dans l’exemple suivant, « ... » représente des fichiers solution supplémentaires.

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>
    </Target>
</Project>
```

 En utilisant les métadonnées des propriétés, toutefois, vous pouvez simplifier cela pour utiliser une seule [tâche MSBuild](../msbuild/msbuild-task.md), comme le montre l’exemple suivant :

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

 Considérez le scénario suivant dans lequel vous générez deux fichiers solution à l’aide de la [tâche MSBuild](../msbuild/msbuild-task.md), à la fois à l’aide de la configuration Release, mais avec l’architecture x86 et l’autre à l’aide de l’architecture ia64. Dans MSBuild 2,0, vous devez créer plusieurs instances de la [tâche MSBuild](../msbuild/msbuild-task.md): une pour générer le projet à l’aide de la configuration Release avec l’architecture x86, l’autre à l’aide de la configuration Release avec l’architecture ia64. Votre fichier projet ressemblerait à ce qui suit :

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

 En utilisant les métadonnées AdditionalProperties, vous pouvez simplifier cela pour utiliser une seule [tâche MSBuild](../msbuild/msbuild-task.md) à l’aide des éléments suivants :

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

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
