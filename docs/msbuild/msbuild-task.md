---
title: Tâche MSBuild | Microsoft Docs
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
ms.openlocfilehash: 4a312bfe8c88b0ac523666779970cc28e3a7c798
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633172"
---
# <a name="msbuild-task"></a>MSBuild (tâche)

Construit des projets MSBuild à partir d’un autre projet MSBuild.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `MSBuild` .

| Paramètre | Description |
|-----------------------------------| - |
| `BuildInParallel` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, les projets spécifiés dans le paramètre `Projects` sont générés en parallèle dans la mesure du possible. La valeur par défaut est `false`. |
| `Projects` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les fichiers projet à générer. |
| `Properties` | Paramètre `String` facultatif.<br /><br /> Liste délimitée par des points-virgules de paires nom/valeur de propriété à appliquer en tant que propriétés globales au projet enfant. Lorsque vous spécifiez ce paramètre, il est fonctionnellement équivalent à définir des propriétés qui ont le commutateur **-propriété** lorsque vous construisez avec [*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Par exemple :<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Lorsque vous transmettez des propriétés au projet par le biais du `Properties` paramètre, MSBuild peut créer une nouvelle instance du projet même si le fichier du projet a déjà été chargé. MSBuild crée une seule instance de projet pour un parcours de projet donné et un ensemble unique de propriétés mondiales. Par exemple, ce comportement vous permet de créer plusieurs tâches MSBuild qui appellent *myproject.proj* avec Configuration=Release, et vous obtenez une seule instance de *myproject.proj* (si aucune propriété unique n’est spécifiée dans la tâche). Si vous spécifiez une propriété qui n’a pas encore été vue par MSBuild, MSBuild crée une nouvelle instance du projet, qui peut être construite en parallèle à d’autres instances du projet. Par exemple, une configuration Release peut être générée en même temps qu’une configuration Debug.|
| `RebaseOutputs` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, les chemins d’accès relatifs des éléments de sortie cibles des projets générés sont modifiés par rapport au projet appelant. La valeur par défaut est `false`. |
| `RemoveProperties` | Paramètre `String` facultatif.<br /><br /> Spécifie l’ensemble des propriétés globales à supprimer. |
| `RunEachTargetSeparately` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, la tâche MSBuild invoque chaque cible dans la liste passée à MSBuild un à la fois, au lieu en même temps. Définir ce paramètre sur `true` garantit que les cibles ultérieures seront appelées même en cas d’échec des cibles précédemment appelées. Dans le cas contraire, une erreur de génération arrêterait l’appel de toutes les cibles suivantes. La valeur par défaut est `false`. |
| `SkipNonexistentProjects` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, les fichiers projet qui n’existent pas sur le disque sont ignorés. Dans le cas contraire, ces projets provoquent une erreur. |
| `StopOnFirstFailure` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, en cas d’échec de génération de l’un des projets, aucun autre projet n’est généré. Pour le moment, cela n’est pas pris en charge lors de la génération en parallèle (avec plusieurs processeurs). |
| `TargetAndPropertyListSeparators` | Paramètre `String[]` facultatif.<br /><br /> Spécifie une liste de cibles et de propriétés en tant que métadonnées d’élément `Project`. Avant le traitement, les séparateurs sont retirés de la séquence d’échappement. Par exemple, %3B (caractère « ; » inséré dans une séquence d’échappement) est traité comme s’il s’agissait du caractère « ; » sans séquence d’échappement. |
| `TargetOutputs` | Paramètre de sortie en lecture seule <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Retourne les sorties des cibles générées à partir de tous les fichiers projet. Seules les sorties des cibles spécifiées sont retournées. Les sorties qui peuvent exister sur les cibles dont dépendent ces cibles ne sont pas retournées.<br /><br /> Le paramètre `TargetOutputs` contient également les métadonnées suivantes :<br /><br /> -   `MSBuildSourceProjectFile`: Le fichier du projet MSBuild qui contient l’objectif qui fixe les sorties.<br />-   `MSBuildSourceTargetName` : cible qui a défini les sorties. **Remarque :** si vous souhaitez identifier les sorties de chaque fichier projet ou de chaque cible séparément, exécutez la tâche `MSBuild` séparément pour chaque fichier projet ou cible. Si vous exécutez la tâche `MSBuild` une seule fois pour générer tous les fichiers projet, les sorties de toutes les cibles sont collectées dans un seul tableau. |
| `Targets` | Paramètre `String` facultatif.<br /><br /> Spécifie la ou les cibles à générer dans les fichiers projet. Utilisez un point-virgule pour séparer les noms de cibles dans la liste. Si aucune cible n’est spécifiée dans la tâche `MSBuild`, les cibles par défaut spécifiées dans les fichiers projet sont créées. **Remarque :** les cibles doivent exister dans tous les fichiers projet. Si tel n’est pas le cas, une erreur de génération se produit. |
| `ToolsVersion` | Paramètre `String` facultatif.<br /><br /> Spécifie la `ToolsVersion` à utiliser lors de la génération des projets transmis à cette tâche.<br /><br /> Permet à une tâche MSBuild de construire un projet qui cible une version différente du cadre .NET que celui spécifié dans le projet. Les valeurs valides sont `2.0`, `3.0` et `3.5`. La valeur par défaut est `3.5`. |

## <a name="remarks"></a>Notes 

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour une liste de ces paramètres supplémentaires et leurs descriptions, voir [TaskExtension classe de base](../msbuild/taskextension-base-class.md).

 Contrairement à l’utilisation de la [tâche Exec](../msbuild/exec-task.md) pour démarrer *MSBuild.exe*, cette tâche utilise le même processus MSBuild pour construire les projets pour enfants. La liste des cibles déjà générées qui peuvent être ignorées est partagée entre la génération parente et les générations enfants. Cette tâche est également plus rapide car aucun nouveau processus MSBuild n’est créé.

 Cette tâche peut traiter non seulement les fichiers projet, mais également les fichiers solution.

 Toute configuration requise par MSBuild pour permettre aux projets de construire en même temps, même si la configuration implique une infrastructure à distance (par exemple, les ports, les protocoles, les délais d’attente, les retries, etc.), doit être configurable à l’aide d’un fichier de configuration. Dans la mesure du possible, il convient de spécifier les éléments de configuration comme paramètres de tâche dans la tâche `MSBuild`.

 À partir de MSBuild 3.5, les projets Solution font désormais surface TargetOutputs de tous les sous-projets qu’il construit.

## <a name="pass-properties-to-projects"></a>Transmettre des propriétés aux projets

 Dans les versions de MSBuild avant MSBuild 3.5, il était difficile de transmettre différents ensembles de propriétés à différents projets énumérés dans l’article MSBuild. Si vous avez utilisé l’attribut Propriétés de la [tâche MSBuild](../msbuild/msbuild-task.md), alors son paramètre a été appliqué à tous les projets en cours de construction, sauf si vous avez mis en lots la [tâche MSBuild](../msbuild/msbuild-task.md) et fourni sous condition différentes propriétés pour chaque projet dans la liste d’éléments.

 MSBuild 3.5, cependant, fournit deux nouveaux articles de métadonnées réservées, Propriétés et Accessoires Supplémentaires, qui vous fournissent un moyen flexible de passer différentes propriétés pour différents projets en cours de construction en utilisant la [tâche MSBuild](../msbuild/msbuild-task.md).

> [!NOTE]
> Ces nouvelles métadonnées ne s’appliquent qu’aux éléments adoptés dans l’attribut Projets de la [tâche MSBuild](../msbuild/msbuild-task.md).

## <a name="multi-processor-build-benefits"></a>Avantages de la génération multiprocesseur

 L’un des principaux avantages liés à l’utilisation de ces nouvelles métadonnées se présente lorsque vous générez vos projets en parallèle sur un système multiprocesseur. Les métadonnées vous permettent de regrouper tous les projets en un seul appel [de tâches MSBuild](../msbuild/msbuild-task.md) sans avoir à effectuer de tâches de lotage ou de MSBuild conditionnelles. Et lorsque vous n’appelez qu’une seule [tâche MSBuild,](../msbuild/msbuild-task.md)tous les projets énumérés dans l’attribut Projets seront construits en parallèle. (Seulement, cependant, `BuildInParallel=true` si l’attribut est présent dans la [tâche MSBuild](../msbuild/msbuild-task.md).) Pour plus d’informations, voir [Construire plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Métadonnées Properties

 Quand elles sont spécifiées, les métadonnées Properties remplacent le paramètre Propriétés de la tâche, alors que les métadonnées [AdditionalProperties](#additionalproperties-metadata) sont ajoutées aux définitions du paramètre.

 Un scénario courant est lorsque vous construisez plusieurs fichiers de solutions en utilisant la [tâche MSBuild](../msbuild/msbuild-task.md), seulement en utilisant différentes configurations de construction. Vous souhaiterez peut-être générer la solution a1 à l’aide de la configuration Debug, et la solution a2 à l’aide de la configuration Release. Dans MSBuild 2.0, ce dossier de projet ressemblerait à ce qui suit :

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

 En utilisant les métadonnées Propriétés, cependant, vous pouvez simplifier cela pour utiliser une seule [tâche MSBuild](../msbuild/msbuild-task.md), comme le montre ce qui suit:

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

 Considérez le scénario suivant où vous construisez deux fichiers de solutions en utilisant la [tâche MSBuild](../msbuild/msbuild-task.md), à la fois en utilisant la configuration de version, mais l’un en utilisant l’architecture x86 et l’autre en utilisant l’architecture ia64. Dans MSBuild 2.0, vous devez créer plusieurs instances de la [tâche MSBuild](../msbuild/msbuild-task.md): l’une pour construire le projet en utilisant la configuration De libération avec l’Architecture x86, l’autre en utilisant la configuration De sortie avec l’architecture ia64. Votre fichier projet ressemblerait à ce qui suit :

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

 En utilisant les métadonnées AdditionalProperties, vous pouvez simplifier cela pour utiliser une seule [tâche MSBuild](../msbuild/msbuild-task.md) en utilisant ce qui suit:

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

## <a name="example"></a> Exemple

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
