---
title: Traitement par lots de MSBuild | Microsoft Docs
ms.date: 06/09/2020
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d7c72d1da270220144cd5e6167ebecb66462ba9
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289272"
---
# <a name="msbuild-batching"></a>Traitement par lots MSBuild

MSBuild divise les listes d’éléments en différentes catégories, ou lots, en fonction des métadonnées de l’élément, et exécute une cible ou une tâche une fois avec chaque lot.

## <a name="task-batching"></a>Traitement par lots des tâches

Le traitement de tâches par lots vous permet de simplifier vos fichiers projet en fournissant un moyen de diviser les listes d’éléments en différents lots et de passer chacun de ces lots dans une tâche séparément. Cela signifie qu’une tâche et ses attributs ne doivent être déclarés qu’une seule fois dans un fichier projet, même si elle peut être exécutée plusieurs fois.

Vous spécifiez que MSBuild doit exécuter le traitement par lots avec une tâche à l’aide de la `%(ItemMetaDataName)` notation dans l’un des attributs de tâche. L’exemple suivant fractionne la liste d’éléments `Example` en lots en fonction de la valeur des métadonnées de l’élément `Color` et passe séparément chacun des lots à la tâche `MyTask`.

> [!NOTE]
> Si vous ne référencez pas la liste des éléments ailleurs dans les attributs de tâche, ou si le nom de métadonnées peut être ambigu, vous pouvez utiliser la notation%(<ItemCollection. ItemMetaDataName>) pour qualifier entièrement la valeur des métadonnées de l’élément à utiliser pour le traitement par lot.

```xml
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

Pour obtenir des exemples de traitement par lots plus spécifiques, consultez [Métadonnées d’élément dans le traitement par lots des tâches](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Traitement par lots des cibles

MSBuild vérifie si les entrées et les sorties d’une cible sont à jour avant d’exécuter la cible. Si les entrées et les sorties sont à jour, la cible est ignorée. Si une tâche à l’intérieur d’une cible utilise le traitement par lot, MSBuild doit déterminer si les entrées et sorties pour chaque lot d’éléments sont à jour. Dans le cas contraire, la cible est exécutée à chaque fois qu’elle est atteinte.

L’exemple suivant montre un `Target` élément qui contient un `Outputs` attribut avec la `%(ItemMetadataName)` notation. MSBuild divise la `Example` liste d’éléments en lots en fonction des `Color` métadonnées de l’élément et analyse les horodateurs des fichiers de sortie pour chaque lot. Si les sorties d’un lot ne sont pas à jour, la cible est exécutée. Sinon, la cible est ignorée.

```xml
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

Pour obtenir un autre exemple de traitement par lots des cibles, consultez [Métadonnées d’élément dans le traitement par lots des cibles](../msbuild/item-metadata-in-target-batching.md).

## <a name="item-and-property-mutations"></a>Mutations d’éléments et de propriétés

Cette section décrit comment comprendre les effets de la modification des propriétés et/ou des métadonnées d’élément, lors de l’utilisation du traitement par lots cible ou du traitement par lot des tâches.

Étant donné que le traitement par lots cible et le traitement par lots de tâches sont deux opérations MSBuild différentes, il est important de comprendre exactement quelle forme de traitement par lot MSBuild utilise dans chaque cas. Lorsque la syntaxe de traitement par lot `%(ItemMetadataName)` apparaît dans une tâche dans une cible, mais pas dans un attribut sur la cible, MSBuild utilise le traitement par lots des tâches. La seule façon de spécifier le traitement par lot des cibles consiste à utiliser la syntaxe de traitement par lot sur un attribut cible, généralement l' `Outputs` attribut.

Avec le traitement par lot et le traitement par lot de tâches, les lots peuvent être considérés comme exécutés indépendamment. Tous les lots commencent par une copie du même état initial des valeurs de métadonnées de propriété et d’élément. Les mutations de valeurs de propriété lors de l’exécution du lot ne sont pas visibles par les autres lots. Prenons l’exemple suivant :

```xml
  <ItemGroup>
    <Thing Include="2" Color="blue" />
    <Thing Include="1" Color="red" />
  </ItemGroup>

  <Target Name="DemoIndependentBatches">
    <ItemGroup>
      <Thing Condition=" '%(Color)' == 'blue' ">
        <Color>red</Color>
        <NeededColorChange>true</NeededColorChange>
      </Thing>
    </ItemGroup>
    <Message Importance="high"
             Text="Things: @(Thing->'%(Identity) is %(Color); needed change=%(NeededColorChange)')"/>
  </Target>
```

La sortie est la suivante :

```output
Target DemoIndependentBatches:
  Things: 2 is red; needed change=true;1 is red; needed change=
```

Le `ItemGroup` dans la cible est implicitement une tâche et, avec le `%(Color)` dans l' `Condition` attribut, le traitement par lots des tâches est effectué. Il existe deux lots : un pour le rouge et l’autre pour le bleu. La propriété `%(NeededColorChange)` est définie uniquement si les `%(Color)` métadonnées sont bleues et le paramètre affecte uniquement l’élément individuel qui correspond à la condition lors de l’exécution du lot bleu. L' `Message` attribut de la tâche `Text` ne déclenche pas le traitement par lot, malgré la `%(ItemMetadataName)` syntaxe, car il est utilisé à l’intérieur d’une transformation d’élément.

Les lots s’exécutent indépendamment, mais pas en parallèle. Cela fait une différence lorsque vous accédez à des valeurs de métadonnées qui changent dans l’exécution par lot. Dans le cas où vous définissez une propriété en fonction de certaines métadonnées dans l’exécution par lot, la propriété prend la *dernière* valeur définie :

```xml
   <PropertyGroup>
       <SomeProperty>%(SomeItem.MetadataValue)</SomeProperty>
   </PropertyGroup>
```

Après l’exécution par lot, la propriété conserve la valeur finale de `%(MetadataValue)` .

Bien que les lots s’exécutent indépendamment, il est important de tenir compte de la différence entre le traitement par lots de cibles et le traitement par lot de tâches, et de savoir quel type s’applique à votre situation. Prenons l’exemple suivant pour mieux comprendre l’importance de cette distinction.

Les tâches peuvent être implicites, plutôt que explicites, ce qui peut prêter à confusion lorsque le traitement par lots des tâches se produit avec des tâches implicites. Lorsqu’un `PropertyGroup` `ItemGroup` élément ou apparaît dans un `Target` , chaque déclaration de propriété dans le groupe est traitée implicitement comme une tâche [CreateProperty](createproperty-task.md) ou [CreateItem](createitem-task.md) distincte. Cela signifie que le comportement est différent lorsque la cible est regroupée par lot, et lorsque la cible n’est pas regroupée par lot (autrement dit, lorsqu’il n’y a pas `%(ItemMetadataName)` de syntaxe dans l' `Outputs` attribut). Lorsque la cible est regroupée par lot, `ItemGroup` s’exécute une fois par cible, mais lorsque la cible n’est pas regroupée par lot, les équivalents implicites des `CreateItem` `CreateProperty` tâches ou sont regroupés par lot à l’aide du traitement par lots de tâches, de sorte que la cible ne s’exécute qu’une seule fois, et chaque élément ou propriété du groupe est traité séparément à l’aide

L’exemple suivant illustre le traitement par lots de cibles et le traitement par lots de tâches dans le cas où les métadonnées sont mutées. Imaginez une situation dans laquelle vous disposez de dossiers A et B avec certains fichiers :

```
A\1.stub
B\2.stub
B\3.stub
```

Examinez maintenant la sortie de ces deux projets similaires.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build" Outputs="%(StubDirs.Identity)">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

La sortie est la suivante :

```output
Test1:
  >> A\ 'A\' 'A'
Test1:
  >> B\ 'B\' 'B'
```

Supprimez maintenant l' `Outputs` attribut qui a spécifié le traitement par lots de cibles.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

La sortie est la suivante :

```output
Test1:
  >> A\ 'B\' 'B'
  >> B\ 'B\' 'B'
```

Notez que l’en-tête `Test1` n’est imprimé qu’une seule fois, mais dans l’exemple précédent, il a été imprimé deux fois. Cela signifie que la cible n’est pas regroupée par lot.  En conséquence, la sortie est déroutante.

En effet, lors de l’utilisation du traitement par lot cible, chaque lot cible exécute tout ce qui se trouve dans la cible avec sa propre copie indépendante de l’ensemble des propriétés et éléments, mais lorsque vous omettez l' `Outputs` attribut, les lignes individuelles dans le groupe de propriétés sont traitées comme des tâches distinctes, potentiellement par lot. Dans ce cas, la `ComponentDir` tâche est traitée par lot (elle utilise la `%(ItemMetadataName)` syntaxe), de sorte qu’au moment de l’exécution de la `ComponentName` ligne, les deux lots de la `ComponentDir` ligne soient terminés et le second qui a exécuté la valeur telle qu’elle apparaît dans la deuxième ligne.

## <a name="property-functions-using-metadata"></a>Fonctions de propriété utilisant des métadonnées

Le traitement par lots peut être contrôlé par des fonctions de propriété qui incluent des métadonnées. Par exemple,

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

utilise <xref:System.IO.Path.Combine%2A> pour combiner un chemin de dossier racine avec un chemin d’élément de compilation.

Les fonctions de propriété ne peuvent pas apparaître dans des valeurs de métadonnées. Par exemple,

`%(Compile.FullPath.Substring(0,3))`

n’est pas autorisé.

Pour plus d’informations sur les fonctions de propriété, consultez [Fonctions de propriété](../msbuild/property-functions.md).

## <a name="see-also"></a>Voir aussi

- [ItemMetadata, élément (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [Concepts avancés](../msbuild/msbuild-advanced-concepts.md)
