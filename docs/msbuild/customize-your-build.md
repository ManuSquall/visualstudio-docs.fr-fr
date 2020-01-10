---
title: Personnaliser votre build | Microsoft Docs
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f1b0e774d70c5787a7221aa0dfa7b0834dac7e3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588289"
---
# <a name="customize-your-build"></a>Personnaliser votre build

Les projets MSBuild qui utilisent le processus de génération standard (importation de *Microsoft.Common.props* et *Microsoft.Common.targets*) ont plusieurs crochets d’extensibilité qui permettent de personnaliser le processus.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Ajouter des arguments aux appels MSBuild en ligne de commande pour un projet

Un fichier *Directory.Build.rsp* dans ou au-dessus de votre répertoire source est appliqué aux générations à partir de la ligne de commande de votre projet. Pour plus d’informations, consultez [Fichiers réponse MSBuild](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props et Directory.Build.targets

Avant MSBuild version 15, si vous souhaitiez fournir une nouvelle propriété personnalisée aux projets de votre solution, vous deviez ajouter manuellement une référence à cette propriété pour chaque fichier projet de la solution. Ou vous deviez définir la propriété dans un fichier *.props*, puis importer explicitement le fichier *.props* dans chaque projet de la solution, entre autres.

Maintenant, vous pouvez ajouter une nouvelle propriété à chaque projet en une seule étape en la définissant dans un seul fichier appelé *Directory.Build.props* dans le dossier racine contenant votre source. Quand MSBuild s’exécute, *Microsoft.Common.props* recherche le fichier *Directory.Build.props* dans votre structure de répertoire (et *Microsoft.Common.targets* recherche *Directory.Build.targets*). S’il en trouve un, il importe la propriété. *Directory.Build.props* est un fichier défini par l’utilisateur qui fournit des personnalisations aux projets situés dans un répertoire.

> [!NOTE]
> Les systèmes de fichiers Linux respectent la casse. Veillez à ce que la casse du nom de fichier Directory.Build.props corresponde exactement ; sinon, il ne sera pas détecté pendant le processus de build.
>
> Pour plus d’informations, voir [ce problème GitHub](https://github.com/dotnet/core/issues/1991#issue-368441031).

### <a name="directorybuildprops-example"></a>Exemple avec Directory.Build.props

Par exemple, si vous souhaitez permettre à l’ensemble de vos projets d’accéder à la nouvelle fonctionnalité Roslyn **/deterministic** (qui est exposée dans la cible `CoreCompile` de Roslyn par la propriété `$(Deterministic)`), vous pouvez procéder comme suit.

1. Créez un nouveau fichier à la racine de votre référentiel appelé *Directory.Build.props*.
2. Ajoutez le code XML suivant au fichier.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. Exécutez MSBuild. Les importations existantes de votre projet de *Microsoft.Common.props* et *Microsoft.Common.targets* trouvent le fichier et l’importent.

### <a name="search-scope"></a>Étendue de la recherche

Lorsque vous recherchez un fichier *Directory.Build.props*, MSBuild remonte dans la structure de répertoire par rapport à l’emplacement de votre projet (`$(MSBuildProjectFullPath)`) et s’arrête après avoir localisé un fichier *Directory.Build.props*. Par exemple, si votre `$(MSBuildProjectFullPath)` était *c:\users\username\code\test\case1*, MSBuild commencerait à rechercher ici, puis remonterait dans la structure de répertoire jusqu’à ce qu’il trouve un fichier *Directory.Build.props*, comme dans la structure de répertoire suivante.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

L’emplacement du fichier solution est sans importance pour *Directory.Build.props*.

### <a name="import-order"></a>Ordre d’importation

*Directory.Build.props* est importé très tôt dans *Microsoft.Common.props* et les propriétés définies ultérieurement ne sont pas disponibles pour ce dernier. Par conséquent, évitez de faire référence aux propriétés qui ne sont pas encore définies (et qui seront évaluées comme vides).

*Directory.Build.targets* est importé à partir de *Microsoft.Common.targets* après l’importation des fichiers *.targets* à partir des packages NuGet. Il peut donc remplacer les propriétés et les cibles définies dans la quasi-totalité de la logique de build. Dans certains cas, toutefois, il peut être nécessaire de personnaliser le fichier projet après l’importation finale.

### <a name="use-case-multi-level-merging"></a>Cas d’utilisation : Fusion à plusieurs niveaux

Supposons que vous ayez la structure de solution standard suivante :

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Il peut être souhaitable d’avoir des propriétés communes pour tous les projets *(1)* , des propriétés communes pour les projets *src* *(2-src)* et des propriétés communes pour les projets *test* *(2-test)* .

Pour que MSBuild fusionne correctement les fichiers « internes » (*2-src* et *2-test*) avec le fichier « externe » (*1*), vous devez prendre en compte le fait qu’une fois que MSBuild a trouvé un fichier *Directory.Build.props*, il arrête l’analyse. Pour poursuivre l’analyse et fusionner les fichiers internes avec le fichier externe, placez ce code dans les deux fichiers internes :

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Voici un résumé de l’approche générale MSBuild :

- Pour un projet donné, MSBuild recherche le premier *Directory.Build.props* vers le haut de la structure de la solution, le fusionne avec les valeurs par défaut et arrête la recherche
- Si vous souhaitez rechercher et fusionner plusieurs niveaux, importez ([`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove), ci-dessus) le fichier « externe » à partir du fichier « interne ».
- Si le fichier « externe » n’importe pas également un élément situé au-dessus, la recherche s’arrête.
- Pour contrôler le processus de recherche et de fusion, utilisez `$(DirectoryBuildPropsPath)` et `$(ImportDirectoryBuildProps)`.

Ou plus simplement : MSBuild s’arrête au premier *Directory.Build.props* qui n’importe aucun élément.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Choisir entre l’ajout de propriétés dans un fichier .props ou .targets

MSBuild est dépend de l’ordre d’importation, et la dernière définition d’une propriété (ou d’une `UsingTask` ou d’une cible) est la définition utilisée.

Lorsque vous utilisez des importations explicites, vous pouvez importer à partir d’un fichier *.props* ou *.targets* à tout moment. Voici la convention la plus utilisée :

- Les fichiers *.props* sont importés au début de l’ordre d’importation.

- Les fichiers *.targets* sont importés à la fin de l’ordre de build.

Cette convention est appliquée par les importations `<Project Sdk="SdkName">` (autrement dit, l’importation de *Sdk.props* passe d’abord, avant tout le contenu du fichier, puis *Sdk.targets* vient en dernier, après tout le contenu du fichier).

Lorsque vous choisissez où placer les propriétés, utilisez les directives générales suivantes :

- Pour de nombreuses propriétés, peu importe où elles sont définies, elles ne sont pas remplacées et sont en lecture seule au moment de l’exécution.

- Pour un comportement qui peut être personnalisé dans un projet individuel, définissez des valeurs par défaut dans le fichier *.props*.

- Évitez de définir des propriétés dépendantes dans les fichiers *.props* en lisant la valeur d’une propriété éventuellement personnalisée, car la personnalisation ne se produira qu’une fois que MSBuild aura lu le projet de l’utilisateur.

- Définissez les propriétés dépendantes dans les fichiers *.targets*, car ils récupèrent les personnalisations à partir de projets individuels.

- Si vous avez besoin de remplacer les propriétés, faites-le dans un fichier *.targets*, une fois que toutes les personnalisations de projet de l’utilisateur ont eu l’occasion de prendre effet. Faites attention lors de l’utilisation de propriétés dérivées, car elles peuvent également être remplacées.

- Ajoutez des éléments dans les fichiers *.props* (conditionnés sur une propriété). Toutes les propriétés sont prises en compte avant n’importe quel élément, afin que les personnalisations de propriétés du projet de l’utilisateur soient récupérées, et cela donne au projet de l’utilisateur la possibilité de `Remove` ou `Update` n’importe quel élément introduit par l’importation.

- Définissez des cibles dans les fichiers *.targets*. Toutefois, si le fichier *.targets* est importé par un kit de développement logiciel (SDK), n’oubliez pas que ce scénario rend la substitution de la cible plus difficile, car le projet de l’utilisateur n’a pas un emplacement pour le remplacer par défaut.

- Si possible, préférez la personnalisation des propriétés au moment de l’évaluation à la modification des propriétés à l’intérieur d’une cible. Cette recommandation vous permettra de charger un projet et comprendre ce qu’il fait plus facilement.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Par défaut, *Microsoft.Common.props* importe `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` et *Microsoft.Common.targets* importe `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. La valeur par défaut de `MSBuildProjectExtensionsPath` est `$(BaseIntermediateOutputPath)`, `obj/`. NuGet utilise ce mécanisme pour faire référence à la logique de génération fournie avec les packages ; autrement dit, au moment de la restauration, il crée les fichiers `{project}.nuget.g.props` qui font référence au contenu des packages.

Vous pouvez désactiver ce mécanisme d’extensibilité en définissant la propriété `ImportProjectExtensionProps` sur `false` dans un fichier *Directory.Build.props* ou avant d’importer *Microsoft.Common.props*.

> [!NOTE]
> La désactivation de MSBuildProjectExtensionsPath empêche d’appliquer à votre projet la logique de génération fournie dans les packages NuGet. Certains packages NuGet nécessitent la logique de génération pour effectuer leur fonction et sont rendus inutiles quand ce mécanisme est désactivé.

## <a name="user-file"></a>Fichier .user

*Microsoft.Common.CurrentVersion.targets* importe `$(MSBuildProjectFullPath).user` s’il existe, afin que vous puissiez créer un fichier à côté de votre projet avec cette extension supplémentaire. Pour les changements à long terme que vous envisagez d’archiver dans le contrôle de code source, préférez la modification du projet proprement dit, afin que les futurs responsables de la maintenance n’aient pas à connaître ce mécanisme d’extension.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath et MSBuildUserExtensionsPath

> [!WARNING]
> L’utilisation de ces mécanismes d’extension rend très difficile la répétition de générations d’une machine à l’autre. Essayez d’utiliser une configuration qui puisse être archivée dans votre système de contrôle de code source et partagée entre tous les développeurs de votre code base.

Par convention, de nombreux fichiers de logique de génération de base importent

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

avant leur contenu, et

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

après. Avec cette convention, les kits SDK installés peuvent renforcer la logique de génération des types de projets courants.

La même structure de répertoires fait l’objet d’une recherche dans `$(MSBuildUserExtensionsPath)`, qui est le dossier par utilisateur *%LOCALAPPDATA%\Microsoft\MSBuild*. Les fichiers placés dans ce dossier sont importés pour toutes les générations du type de projet correspondant exécutées sous les informations d’identification de l’utilisateur concerné. Vous pouvez désactiver les extensions utilisateur en définissant les propriétés nommées d’après le fichier d’importation selon le modèle `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`. Par exemple, si vous définissez `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` avec la valeur `false`, vous empêchez l’importation de `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`.

## <a name="customize-the-solution-build"></a>Personnaliser la génération de la solution

> [!IMPORTANT]
> La personnalisation de la génération de la solution de cette façon s’applique uniquement aux générations de ligne de commande avec *MSBuild.exe*. Elle **ne s’applique pas** aux générations à l’intérieur de Visual Studio.

Quand MSBuild génère un fichier solution, il le convertit en interne en fichier projet, puis génère ce dernier. Le fichier projet généré importe `before.{solutionname}.sln.targets` avant de définir des cibles et `after.{solutionname}.sln.targets` après avoir importé les cibles, notamment les cibles installées dans les répertoires `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` et `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter`.

Par exemple, vous pouvez définir une nouvelle cible pour écrire un message de journal personnalisé après avoir généré *MyCustomizedSolution.sln* en créant un fichier dans le même répertoire que celui nommé *after.MyCustomizedSolution.sln.targets* qui contient

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Concepts MSBuild](../msbuild/msbuild-concepts.md)

- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
