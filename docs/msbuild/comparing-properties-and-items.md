---
title: Comparaison des propriétés et des éléments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a86365ffe839b45fcd09862040fb88f0d4148bc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634407"
---
# <a name="compare-properties-and-items"></a>Comparer des propriétés et des éléments

Les propriétés et les éléments MSBuild permettent de transmettre des informations aux tâches, d’évaluer des conditions et de stocker les valeurs qui peuvent être référencées dans le fichier projet.

- Les propriétés sont des paires nom-valeur. Pour plus d’informations, voir [propriétés MSBuild](../msbuild/msbuild-properties.md).

- Les éléments sont des objets qui représentent généralement des fichiers. Des collections de métadonnées peuvent être associées aux objets d’élément. Les métadonnées sont des paires nom-valeur. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

## <a name="scalars-and-vectors"></a>Scalaires et vecteurs

Comme les propriétés MSBuild sont des paires nom-valeur qui ont seulement une valeur de chaîne, elles sont souvent décrites en tant que *scalaires*. Comme les types d’élément MSBuild sont des listes d’éléments, ils sont souvent décrits comme des *vecteurs*. Toutefois, en pratique, les propriétés peuvent représenter plusieurs valeurs, et les types d’élément peuvent posséder zéro ou un élément.

### <a name="target-dependency-injection"></a>Injection de dépendances cibles

Pour voir comment les propriétés peuvent représenter plusieurs valeurs, examinez un modèle d’utilisation courante pour ajouter une cible à la liste des cibles à générer. Cette liste est généralement représentée par une valeur de propriété, les noms des cibles étant séparés par des points-virgules.

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

La propriété `BuildDependsOn` est généralement utilisée comme argument d’un attribut `DependsOnTargets` cible, le convertissant effectivement en une liste d’éléments. Cette propriété peut être remplacée pour ajouter une cible ou modifier l’ordre d’exécution des cibles. Par exemple,

```xml
<PropertyGroup>
    <BuildDependsOn>
        $(BuildDependsOn);
        CustomBuild;
    </BuildDependsOn>
</PropertyGroup>
```

ajoute la cible CustomBuild à la liste des cibles, donnant ainsi à la propriété `BuildDependsOn` la valeur `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.

Depuis MSBuild 4.0, l’injection de dépendances cibles est dépréciée. L’utilisation des attributs `AfterTargets` et `BeforeTargets` est préférable. Pour plus d’informations, consultez [Ordre de génération des cibles](../msbuild/target-build-order.md).

### <a name="conversions-between-strings-and-item-lists"></a>Conversion entre des chaînes et des listes d’éléments

MSBuild effectue au besoin les conversions vers et depuis des types d’élément et des valeurs de chaîne. Pour voir comment une liste d’éléments peut devenir une valeur de chaîne, examinez ce qui se passe lorsqu’un type d’élément est utilisé comme valeur d’une propriété MSBuild :

```xml
<ItemGroup>
    <OutputDir Include="KeyFiles\;Certificates\" />
</ItemGroup>
<PropertyGroup>
    <OutputDirList>@(OutputDir)</OutputDirList>
</PropertyGroup>
```

Le type d’élément OutputDir possède un attribut `Include` pourvu de la valeur « KeyFiles\\;Certificates\\ ». MSBuild analyse cette chaîne en deux éléments : KeyFiles\ et Certificates\\. Si le type d’élément OutputDir est utilisé comme valeur de la propriété OutputDirList, MSBuild convertit ou « aplanit » le type d’élément dans la chaîne séparée par des points-virgules « KeyFiles\\;Certificates\\ ».

## <a name="properties-and-items-in-tasks"></a>Propriétés et éléments des tâches

Les propriétés et éléments sont utilisés comme entrées et sorties pour les tâches MSBuild. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).

Les propriétés sont transmises aux tâches en tant qu’attributs. Dans la tâche, une propriété MSBuild est représentée par un type de propriété dont la valeur peut être convertie vers et depuis une chaîne. Les types de propriété pris en charge incluent `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int` et `string`, ainsi que tout type pouvant être géré par <xref:System.Convert.ChangeType%2A>.

Les éléments sont passés aux tâches en tant qu’objets <xref:Microsoft.Build.Framework.ITaskItem>. Dans la tâche, <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> représente la valeur de l’élément, et <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> récupère ses métadonnées.

La liste d’éléments d’un type d’élément peut être transmise en tant que tableau d’objets `ITaskItem`. Depuis .NET Framework 3.5, les éléments peuvent être supprimés d’une liste d’éléments dans une cible à l’aide de l’attribut `Remove`. Comme les éléments peuvent être supprimés d’une liste d’éléments, un type d’élément peut comporter zéro élément. Si une liste d’éléments est transmise à une tâche, le code de la tâche doit vérifier cette possibilité.

## <a name="property-and-item-evaluation-order"></a>Ordre d’évaluation des propriétés et des éléments

Pendant la phase d’évaluation d’une génération, les fichiers importés sont incorporés à la génération dans l’ordre dans lequel ils apparaissent. Les propriétés et les éléments sont définis en trois passes dans l’ordre suivant :

- Les propriétés sont définies et modifiées dans l’ordre dans lequel elles apparaissent.

- Les définitions d’élément sont créées et modifiées dans l’ordre dans lequel elles apparaissent.

- Les éléments sont définis et modifiés dans l’ordre dans lequel ils apparaissent.

Pendant la phase d’exécution d’une génération, les propriétés et les éléments qui sont définis dans des cibles sont évalués ensemble en une seule phase dans l’ordre dans lequel ils apparaissent.

Néanmoins, ce n’est pas complet. Lorsqu’une propriété, une définition d’élément ou un élément sont définis, leur valeur est évaluée. L’évaluateur d’expression développe la chaîne qui spécifie la valeur. Le développement de la chaîne dépend de la phase de la génération. Voici un ordre d’évaluation des éléments et des propriétés plus détaillé :

- Pendant la phase d’évaluation d’une génération :

  - Les propriétés sont définies et modifiées dans l’ordre dans lequel elles apparaissent. Les fonctions de propriétés sont exécutées. Les valeurs de propriété de la forme $(PropertyName) sont développées dans des expressions. La valeur de propriété est définie sur l’expression développée.

  - Les définitions d’élément sont créées et modifiées dans l’ordre dans lequel elles apparaissent. Les fonctions de propriétés ont déjà été développées dans des expressions. Les valeurs de métadonnées sont définies sur les expressions développées.

  - Les types d’élément sont définis et modifiés dans l’ordre dans lequel ils apparaissent. Les valeurs d’éléments de la forme @(ItemType) sont développées. Les transformations d’élément sont également développées. Les fonctions et valeurs de propriétés ont déjà été développées dans des expressions. La liste d’éléments et les valeurs de métadonnées sont définies sur les expressions développées.

- Pendant la phase d’exécution d’une génération :

  - Les propriétés et les éléments qui sont définis dans des cibles sont évalués ensemble dans l’ordre dans lequel ils apparaissent. Les fonctions de propriétés sont exécutées, et les valeurs de propriétés sont développées dans des expressions. Les valeurs d’éléments et les transformations d’élément sont également développées. Les valeurs de propriétés, les valeurs de types d’élément et les valeurs de métadonnées sont définies sur les expressions développées.

### <a name="subtle-effects-of-the-evaluation-order"></a>Effets discrets de l’ordre d’évaluation

Dans la phase d’évaluation d’une génération, l’évaluation des propriétés précède celle des éléments. Néanmoins, les valeurs de certaines propriétés peuvent sembler dépendre des valeurs d’éléments. Examinez le script ci-dessous.

```xml
<ItemGroup>
    <KeyFile Include="KeyFile.cs">
        <Version>1.0.0.3</Version>
    </KeyFile>
</ItemGroup>
<PropertyGroup>
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
</PropertyGroup>
<Target Name="AfterBuild">
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

L’exécution de la tâche Message affiche ce message :

```
KeyFileVersion: 1.0.0.3
```

C’est parce que la valeur de `KeyFileVersion` correspond réellement à la chaîne « \@(KeyFile->'%(Version)') ». Comme l’élément et les transformations d’élément n’ont pas été développés lorsque la propriété a été définie, la valeur de la chaîne non développée a été affectée à la propriété `KeyFileVersion`.

Pendant la phase d’exécution de la génération, quand il traite la tâche Message, MSBuild développe la chaîne « \@(KeyFile->'%(Version)') » pour générer « 1.0.0.3 ».

Notez que le même message s’affiche même si les groupes de propriétés et d’éléments ont été annulés dans l’ordre.

Pour illustrer un deuxième exemple, examinez ce qui peut se produire lorsque des groupes de propriétés et d’éléments se trouvent dans des cibles :

```xml
<Target Name="AfterBuild">
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

La tâche Message affiche le message suivant :

```
KeyFileVersion:
```

En effet, pendant la phase d’exécution de la génération, les groupes de propriétés et d’éléments définis dans des cibles sont évalués simultanément de haut en bas. Lorsque la propriété `KeyFileVersion` est définie, `KeyFile` est inconnu. Par conséquent, la transformation d’élément se développe en une chaîne vide.

Dans ce cas, l’inversion de l’ordre des groupes de propriétés et d’éléments restaure le message d’origine :

```xml
<Target Name="AfterBuild">
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

`KeyFileVersion` prend la valeur « 1.0.0.3 » et non « \@(KeyFile->'%(Version)') ». La tâche Message affiche le message suivant :

```
KeyFileVersion: 1.0.0.3
```

## <a name="see-also"></a>Voir aussi

- [Concepts avancés](../msbuild/msbuild-advanced-concepts.md)
