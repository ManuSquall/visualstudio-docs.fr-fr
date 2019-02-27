---
title: 'Procédure : Générer des builds incrémentielles | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59a637a530bfabe784aae2c1fab622e2c2380667
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621329"
---
# <a name="how-to-build-incrementally"></a>Procédure : Générer de façon incrémentielle
Quand vous générez un projet volumineux, il est important de ne pas regénérer les composants précédemment générés qui sont encore à jour. Si toutes les cibles sont générées à chaque fois, la génération de builds prend beaucoup de temps. Pour activer les builds incrémentielles (builds dans lesquelles seules les cibles obsolètes ou n’ayant pas été déjà générées sont regénérées), [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) peut comparer les horodateurs des fichiers d’entrée avec ceux des fichiers de sortie et déterminer s’il faut ignorer, générer ou regénérer partiellement une cible. Toutefois, il doit exister un mappage un-à-un entre les entrées et les sorties. Vous pouvez utiliser des transformations pour permettre aux cibles d’identifier ce mappage direct. Pour plus d’informations sur les transformations, consultez [Transformations](../msbuild/msbuild-transforms.md).

## <a name="specify-inputs-and-outputs"></a>Spécifier des entrées et des sorties
Une cible peut être générée de façon incrémentielle si les entrées et les sorties sont spécifiées dans le fichier projet.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Pour spécifier les entrées et les sorties d’une cible

- Utilisez les attributs `Inputs` et `Outputs` de l’élément `Target`. Par exemple :

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] peut comparer les horodateurs des fichiers d’entrée avec ceux des fichiers de sortie et déterminer s’il faut ignorer, générer ou regénérer partiellement une cible. Dans l’exemple suivant, si un fichier de la liste d’éléments `@(CSFile)` est plus récent que le fichier *hello.exe*, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] exécute la cible ; sinon, il l’ignore :

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

Quand les entrées et les sorties sont spécifiées dans une cible, chaque sortie est mappée avec une seule entrée ou il n’existe pas de mappage direct entre les sorties et les entrées. Dans la [tâche Csc](../msbuild/csc-task.md) précédente, par exemple, la sortie *hello.exe* ne peut pas être mappée à une entrée unique. Elle dépend de toutes les entrées.

> [!NOTE]
> Une cible dans laquelle il n’existe pas de mappage direct entre les entrées et les sorties est toujours générée plus fréquemment qu’une cible dans laquelle chaque sortie ne peut être mappée qu’avec une seule entrée, car [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ne peut pas déterminer les sorties qui doivent être regénérées si certaines des entrées ont changé.

Les tâches dans lesquelles vous pouvez identifier un mappage direct entre les sorties et les entrées, comme la [tâche LC](../msbuild/lc-task.md), sont mieux adaptées aux builds incrémentielles, à l’inverse des tâches telles que [Csc](../msbuild/csc-task.md) et [Vbc](../msbuild/vbc-task.md), qui produisent un seul assembly de sortie à partir de plusieurs entrées.

## <a name="example"></a>Exemple
L’exemple suivant utilise un projet qui génère des fichiers d’aide pour un système d’aide éventuel. Le projet fonctionne en convertissant les fichiers sources *.txt* en fichiers *.content* intermédiaires, qui sont ensuite combinés avec les fichiers de métadonnées XML pour produire le fichier *.help* final utilisé par le système d’aide. Le projet utilise les tâches hypothétiques suivantes :

- `GenerateContentFiles`: convertit des fichiers *.txt* en fichiers *.content*.

- `BuildHelp`: combine des fichiers *.content* et des fichiers de métadonnées XML pour générer le fichier *.help* final.


Le projet utilise les transformations pour créer un mappage un-à-un entre les entrées et les sorties de la tâche `GenerateContentFiles`. Pour plus d’informations, consultez l’article [Transforms (Transformations MSBuild)](../msbuild/msbuild-transforms.md). De même, l’élément `Output` est défini de façon à utiliser automatiquement les sorties de la tâche `GenerateContentFiles` comme entrées de la tâche `BuildHelp`.

Ce fichier projet contient à la fois les cibles `Convert` et `Build`. Les tâches `GenerateContentFiles` et `BuildHelp` sont placées respectivement dans les cibles `Convert` et `Build` pour que chaque cible puisse être générée de façon incrémentielle. En utilisant l’élément `Output`, les sorties de la tâche `GenerateContentFiles` sont placées dans la liste d’éléments `ContentFile`, où elles peuvent être utilisées comme entrées pour la tâche `BuildHelp`. En utilisant l’élément `Output` de cette façon, vous pouvez utiliser automatiquement les sorties d’une tâche comme entrées d’une autre tâche. Vous n’avez donc pas à répertorier manuellement les éléments ou les listes d’éléments dans chaque tâche.

> [!NOTE]
> Bien que la cible `GenerateContentFiles` puisse être générée de façon incrémentielle, toutes les sorties de cette cible sont toujours exigées comme entrées de la cible `BuildHelp`. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fournit automatiquement toutes les sorties d’une cible comme entrées d’une autre cible quand vous utilisez l’élément `Output`.

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <TXTFile Include="*.txt"/>
        <XMLFiles Include="\metadata\*.xml"/>
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
            MetadataFiles = "@(XMLFiles)"
            OutputFileName = "$(MSBuildProjectName).help"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi
- [Cibles](../msbuild/msbuild-targets.md)
- [Target, élément (MSBuild)](../msbuild/target-element-msbuild.md)
- [Transformations](../msbuild/msbuild-transforms.md)
- [Tâche Csc](../msbuild/csc-task.md)
- [Vbc, tâche](../msbuild/vbc-task.md)
