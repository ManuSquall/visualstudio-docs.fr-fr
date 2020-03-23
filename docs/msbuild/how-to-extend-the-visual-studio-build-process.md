---
title: Étendre le processus de génération
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6a465a752282f4a0dc00f3fb294ade4169bb19b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093945"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Guide pratique pour étendre le processus de génération Visual Studio

Le processus de construction Visual Studio est défini par une série de fichiers MSBuild *.targets* qui sont importés dans votre fichier de projet. Parmi ces fichiers importés, *Microsoft.Common.targets* peut être étendu de manière à exécuter des tâches personnalisées à différentes étapes du processus de génération. Cet article explique deux méthodes que vous pouvez utiliser pour étendre le processus de construction Visual Studio:

- En prédéfinie des cibles spécifiques définies dans les cibles communes *(Microsoft.Common.targets* ou les fichiers qu’il importe).

- Dépassement des propriétés "DependsOn" définies dans les cibles communes.

## <a name="override-predefined-targets"></a>Substituer des cibles prédéfinies

Les cibles communes contiennent un ensemble d’objectifs vides prédéfinis qui sont appelés avant et après certaines des principales cibles dans le processus de construction. Par exemple, MSBuild `BeforeBuild` appelle la `CoreBuild` cible `AfterBuild` avant la `CoreBuild` cible principale et la cible après la cible. Par défaut, les cibles vides dans les cibles communes ne font rien, mais vous pouvez passer outre à leur comportement par défaut en définissant les cibles que vous voulez dans un fichier de projet qui importe les cibles communes. En prépondérer les cibles prédéfinies, vous pouvez utiliser les tâches MSBuild pour vous donner plus de contrôle sur le processus de construction.
Les cibles communes contiennent un ensemble d’objectifs vides prédéfinis qui sont appelés avant et après certaines des principales cibles dans le processus de construction. Par exemple, MSBuild `BeforeBuild` appelle la `CoreBuild` cible `AfterBuild` avant la `CoreBuild` cible principale et la cible après la cible. Par défaut, les cibles vides dans les cibles communes ne font rien, mais vous pouvez passer outre à leur comportement par défaut en définissant les cibles que vous voulez dans un fichier de projet qui importe les cibles communes. En prépondérer les cibles prédéfinies, vous pouvez utiliser les tâches MSBuild pour vous donner plus de contrôle sur le processus de construction.

> [!NOTE]
> Les projets de type SDK ont une importation implicite de cibles *après la dernière ligne du dossier du projet.* Cela signifie que vous ne pouvez pas remplacer les cibles par défaut à moins que vous ne spécifiiez manuellement vos importations telles que décrites dans [Comment : Utilisez msBuild projet SDKs](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Pour substituer une cible prédéfinie

1. Identifiez une cible prédéfinie dans les cibles communes que vous souhaitez remplacer. Consultez le tableau ci-dessous pour obtenir la liste complète des cibles que vous pouvez substituer en toute sécurité.

2. Définissez la ou les cibles à la fin de votre fichier projet, juste avant la balise `</Project>`. Par exemple :

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. Générez le fichier projet.

Le tableau suivant affiche toutes les cibles dans les cibles communes que vous pouvez remplacer en toute sécurité.

|Nom de la cible|Description|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après la compilation principale. La plupart des personnalisations sont effectuées dans l’une de ces deux cibles.|
|`BeforeBuild`, `AfterBuild`|Les tâches insérées dans l’une de ces cibles s’exécutent avant ou après tout le reste lors de la génération. **Remarque :** Les cibles `BeforeBuild` et `AfterBuild` sont déjà définies dans les commentaires à la fin de la plupart des fichiers projet. Vous pouvez ainsi ajouter facilement des événements pré-build et post-build à votre fichier projet.|
|`BeforeRebuild`, `AfterRebuild`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après l’appel de la fonctionnalité de regénération principale. L’ordre d’exécution de cible dans `BeforeRebuild` `Clean` *Microsoft.Common.targets* est: , , `Build`, et puis `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après l’appel de la fonctionnalité de nettoyage principale.|
|`BeforePublish`, `AfterPublish`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après l’appel de la fonctionnalité de publication principale.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après la résolution des références d’assembly.|
|`BeforeResGen`, `AfterResGen`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après la génération des ressources.|

## <a name="example-aftertargets-and-beforetargets"></a>Exemple : AfterTargets et BeforeTargets

L’exemple suivant montre `AfterTargets` comment utiliser l’attribut pour ajouter une cible personnalisée qui fait quelque chose avec les fichiers de sortie. Dans ce cas, il copie les fichiers de sortie à un nouveau dossier *CustomOutput*.  L’exemple montre également comment nettoyer les fichiers créés `CustomClean` par l’opération de construction personnalisée avec une cible en utilisant un `BeforeTargets` attribut et en spécifiant que l’opération propre personnalisée s’exécute avant la `CoreClean` cible.

```xml
<Project Sdk="Microsoft.NET.Sdk">

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
   <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
</PropertyGroup>

<Target Name="CustomAfterBuild" AfterTargets="Build">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean" BeforeTargets="CoreClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

> [!WARNING]
> Assurez-vous d’utiliser des noms différents des cibles prédéfinis énumérées dans le tableau `CustomAfterBuild`dans `AfterBuild`la section précédente (par exemple, nous avons nommé la cible de construction personnalisée ici , pas ), puisque ces cibles prédéfinies sont annulées par l’importation SDK qui les définit également. Vous ne voyez pas l’importation du fichier cible qui l’emporte sur ces cibles, mais elle `Sdk` est implicitement ajoutée à la fin du fichier de projet lorsque vous utilisez la méthode d’attribut de référencement d’un SDK.

## <a name="override-dependson-properties"></a>Substituer des propriétés DependsOn

L’extension des cibles prédéfinies est un moyen facile d’étendre le processus de construction, mais, parce que MSBuild évalue la définition des cibles de façon séquentielle, il n’existe aucun moyen d’empêcher un autre projet qui importe votre projet de dépasser les cibles que vous avez déjà Substituée. Ainsi, par exemple, la dernière cible `AfterBuild` définie dans le fichier projet, une fois que tous les autres projets ont été importés, sera celle utilisée pour la génération.

Vous pouvez vous prémunir contre les remplacements imprévus des `DependsOnTargets` cibles en l’emportent sur les propriétés DependsOn qui sont utilisées dans les attributs à travers les cibles communes. Par exemple, la cible `Build` contient une valeur d’attribut `DependsOnTargets` égale à `"$(BuildDependsOn)"`. Vous devez :

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Ce code XML indique que pour exécuter la cible `Build`, vous devez d’abord exécuter toutes les cibles spécifiées dans la propriété `BuildDependsOn`. La propriété `BuildDependsOn` est définie de la manière suivante :

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Vous pouvez remplacer cette valeur de propriété en déclarant une autre propriété nommée `BuildDependsOn` à la fin de votre fichier projet. En incluant la propriété `BuildDependsOn` précédente dans la nouvelle propriété, vous pouvez ajouter de nouvelles cibles au début et à la fin de la liste de cibles. Par exemple :

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

Les projets qui importent vos fichiers projet peuvent substituer ces propriétés sans remplacer les personnalisations que vous avez apportées.

#### <a name="to-override-a-dependson-property"></a>Pour substituer une propriété DependsOn

1. Identifiez une propriété DependsOn prédéfinie dans les cibles communes que vous souhaitez remplacer. Consultez le tableau ci-dessous pour obtenir la liste des propriétés DependsOn qui sont communément substituées.

2. Définissez une autre instance de la ou des propriétés à la fin de votre fichier projet. Incluez la propriété d’origine (par exemple `$(BuildDependsOn)`) dans la nouvelle propriété.

3. Définissez vos cibles personnalisées avant ou après la définition de la propriété.

4. Générez le fichier projet.

### <a name="commonly-overridden-dependson-properties"></a>Propriétés DependsOn communément substituées

|Nom de la propriété|Description|
|-------------------|-----------------|
|`BuildDependsOn`|Propriété à substituer si vous souhaitez insérer des cibles personnalisées avant ou après l’intégralité du processus de génération.|
|`CleanDependsOn`|Propriété à substituer si vous souhaitez nettoyer la sortie de votre processus de génération.|
|`CompileDependsOn`|Propriété à substituer si vous souhaitez insérer des processus personnalisés avant ou après l’étape de compilation.|

## <a name="example-builddependson-and-cleandependson"></a>Exemple : BuildDependsOn et CleanDependsOn

L’exemple suivant est `BeforeTargets` `AfterTargets` similaire à l’exemple et à celui-ci, mais montre comment obtenir des fonctionnalités similaires. Il étend la `BuildDependsOn` construction en utilisant `CustomAfterBuild` pour ajouter votre propre tâche qui copie `CustomClean` les `CleanDependsOn`fichiers de sortie après la construction, et ajoute également la tâche correspondante en utilisant .  

Dans cet exemple, il s’agit d’un projet de style SDK. Comme mentionné dans la note sur les projets de style SDK plus `Sdk` tôt dans cet article, vous devez utiliser la méthode d’importation manuelle au lieu de l’attribut que Visual Studio utilise quand il génère des fichiers de projet.

```xml
<Project>
<Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>

<Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <BuildDependsOn>
      $(BuildDependsOn);CustomAfterBuild
    </BuildDependsOn>

    <CleanDependsOn>
      $(CleanDependsOn);CustomClean
    </CleanDependsOn>

    <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

<Target Name="CustomAfterBuild">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

L’ordre des éléments est important. Le `BuildDependsOn` `CleanDependsOn` fichier et les éléments doivent apparaître après l’importation du fichier standard des cibles SDK.

## <a name="see-also"></a>Voir aussi

- [Intégration Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [.cibles fichiers](../msbuild/msbuild-dot-targets-files.md)
