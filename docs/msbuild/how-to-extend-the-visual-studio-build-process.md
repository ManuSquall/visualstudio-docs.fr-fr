---
title: Étendre le processus de génération
description: Découvrez les différentes façons de modifier le processus de génération afin de pouvoir contrôler et personnaliser la génération de vos projets.
ms.custom: seodec18, SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94e5680f8e8635c969e25555463a21bba069284a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055815"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Guide pratique pour étendre le processus de génération Visual Studio

Le processus de génération Visual Studio est défini par une série de fichiers MSBuild *. targets* importés dans votre fichier projet. Parmi ces fichiers importés, *Microsoft.Common.targets* peut être étendu de manière à exécuter des tâches personnalisées à différentes étapes du processus de génération. Cet article décrit deux méthodes que vous pouvez utiliser pour étendre le processus de génération de Visual Studio :

- Substitution de cibles prédéfinies spécifiques définies dans les cibles communes (*Microsoft. Common. targets* ou les fichiers qu’il importe).

- Substitution des propriétés « DependsOn » définies dans les cibles courantes.

## <a name="override-predefined-targets"></a>Substituer des cibles prédéfinies

Les cibles courantes contiennent un ensemble de cibles vides prédéfinies qui sont appelées avant et après certaines des cibles majeures dans le processus de génération. Par exemple, MSBuild appelle la `BeforeBuild` cible avant la cible principale `CoreBuild` et la `AfterBuild` cible après la `CoreBuild` cible. Par défaut, les cibles vides dans les cibles courantes ne font rien, mais vous pouvez remplacer leur comportement par défaut en définissant les cibles souhaitées dans un fichier projet qui importe les cibles communes. En substituant les cibles prédéfinies, vous pouvez utiliser des tâches MSBuild pour mieux contrôler le processus de génération.

> [!NOTE]
> Les projets de style SDK ont une importation implicite des cibles *après la dernière ligne du fichier projet*. Cela signifie que vous ne pouvez pas remplacer les cibles par défaut, sauf si vous spécifiez vos importations manuellement, comme décrit dans Guide pratique [pour utiliser des kits de développement](how-to-use-project-sdk.md)logiciel (SDK) de projet MSBuild.

#### <a name="to-override-a-predefined-target"></a>Pour substituer une cible prédéfinie

1. Identifiez une cible prédéfinie dans les cibles courantes que vous souhaitez substituer. Consultez le tableau ci-dessous pour obtenir la liste complète des cibles que vous pouvez substituer en toute sécurité.

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

Le tableau suivant répertorie toutes les cibles dans les cibles courantes que vous pouvez substituer en toute sécurité.

|Nom de la cible|Description|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après la compilation principale. La plupart des personnalisations sont effectuées dans l’une de ces deux cibles.|
|`BeforeBuild`, `AfterBuild`|Les tâches insérées dans l’une de ces cibles s’exécutent avant ou après tout le reste lors de la génération. **Remarque :** Les cibles `BeforeBuild` et `AfterBuild` sont déjà définies dans les commentaires à la fin de la plupart des fichiers projet. Vous pouvez ainsi ajouter facilement des événements pré-build et post-build à votre fichier projet.|
|`BeforeRebuild`, `AfterRebuild`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après l’appel de la fonctionnalité de regénération principale. L’ordre d’exécution des cibles dans *Microsoft. Common. targets* est : `BeforeRebuild` , `Clean` , `Build` , puis `AfterRebuild` .|
|`BeforeClean`, `AfterClean`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après l’appel de la fonctionnalité de nettoyage principale.|
|`BeforePublish`, `AfterPublish`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après l’appel de la fonctionnalité de publication principale.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après la résolution des références d’assembly.|
|`BeforeResGen`, `AfterResGen`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après la génération des ressources.|

## <a name="example-aftertargets-and-beforetargets"></a>Exemple : AfterTargets et BeforeTargets

L’exemple suivant montre comment utiliser l' `AfterTargets` attribut pour ajouter une cible personnalisée qui effectue une opération avec les fichiers de sortie. Dans ce cas, il copie les fichiers de sortie dans un nouveau dossier *CustomOutput*.  L’exemple montre également comment nettoyer les fichiers créés par l’opération de génération personnalisée avec une `CustomClean` cible à l’aide d’un `BeforeTargets` attribut et en spécifiant que l’opération de nettoyage personnalisée s’exécute avant la `CoreClean` cible.

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
> Veillez à utiliser des noms différents de ceux des cibles prédéfinies répertoriées dans le tableau de la section précédente (par exemple, nous avons nommé la cible build personnalisée ici `CustomAfterBuild` , pas `AfterBuild` ), car ces cibles prédéfinies sont remplacées par l’importation du kit de développement logiciel (SDK) qui les définit également. L’importation du fichier cible qui remplace ces cibles ne s’affiche pas, mais elle est implicitement ajoutée à la fin du fichier projet lorsque vous utilisez la `Sdk` méthode d’attribut de référencement d’un kit de développement logiciel (SDK).

## <a name="override-dependson-properties"></a>Substituer des propriétés DependsOn

La substitution de cibles prédéfinies est un moyen simple d’étendre le processus de génération, mais comme MSBuild évalue la définition des cibles de manière séquentielle, il n’existe aucun moyen d’empêcher un autre projet qui importe votre projet de remplacer les cibles que vous avez déjà remplacées. Ainsi, par exemple, la dernière cible `AfterBuild` définie dans le fichier projet, une fois que tous les autres projets ont été importés, sera celle utilisée pour la génération.

Vous pouvez vous protéger contre les substitutions involontaires de cibles en substituant les propriétés DependsOn utilisées dans `DependsOnTargets` les attributs dans les cibles courantes. Par exemple, la cible `Build` contient une valeur d’attribut `DependsOnTargets` égale à `"$(BuildDependsOn)"`. Vous devez :

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

1. Identifiez une propriété DependsOn prédéfinie dans les cibles courantes que vous souhaitez substituer. Consultez le tableau ci-dessous pour obtenir la liste des propriétés DependsOn qui sont communément substituées.

2. Définissez une autre instance de la ou des propriétés à la fin de votre fichier projet. Incluez la propriété d’origine (par exemple `$(BuildDependsOn)`) dans la nouvelle propriété.

3. Définissez vos cibles personnalisées avant ou après la définition de la propriété.

4. Générez le fichier projet.

### <a name="commonly-overridden-dependson-properties"></a>Propriétés DependsOn communément substituées

|Nom de la propriété|Description|
|-------------------|-----------------|
|`BuildDependsOn`|Propriété à substituer si vous souhaitez insérer des cibles personnalisées avant ou après l’intégralité du processus de génération.|
|`CleanDependsOn`|Propriété à substituer si vous souhaitez nettoyer la sortie de votre processus de génération.|
|`CompileDependsOn`|Propriété à substituer si vous souhaitez insérer des processus personnalisés avant ou après l’étape de compilation.|

## <a name="example-builddependson-and-cleandependson"></a>Exemple : BuildDependsOn et CleanDependsOn

L’exemple suivant est similaire à l' `BeforeTargets` `AfterTargets` exemple et, mais il montre comment obtenir des fonctionnalités similaires. Elle étend la génération à l’aide `BuildDependsOn` de pour ajouter votre propre tâche `CustomAfterBuild` qui copie les fichiers de sortie après la génération, et ajoute également la `CustomClean` tâche correspondante à l’aide de `CleanDependsOn` .  

Dans cet exemple, il s’agit d’un projet de type SDK. Comme mentionné dans la remarque à propos des projets de type SDK plus haut dans cet article, vous devez utiliser la méthode d’importation manuelle au lieu de l' `Sdk` attribut que Visual Studio utilise lors de la génération des fichiers projet.

```xml
<Project>
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk"/>

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk"/>

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
    <Message Importance="high" Text="_FilesToCopy: @(_FilesToCopy)"/>

    <Message Text="DestFiles:
      @(_FilesToCopy-&gt;'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

    <Copy SourceFiles="@(_FilesToCopy)"
          DestinationFiles="@(_FilesToCopy-&gt;'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Importance="high" Text="Inside Custom Clean"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files="@(_CustomFilesToDelete)"/>
  </Target>
</Project>
```

L’ordre des éléments est important. Les `BuildDependsOn` `CleanDependsOn` éléments et doivent apparaître après l’importation du fichier de cibles du kit de développement logiciel (SDK) standard.

## <a name="see-also"></a>Voir aussi

- [Visual Studio, intégration](../msbuild/visual-studio-integration-msbuild.md)
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [fichiers. targets](../msbuild/msbuild-dot-targets-files.md)
