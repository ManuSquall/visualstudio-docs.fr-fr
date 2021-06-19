---
title: Propriétés réservées et connues de MSBuild | Microsoft Docs
description: Découvrez les propriétés réservées et connues de MSBuild, ainsi que les propriétés prédéfinies qui stockent des informations sur le fichier projet et les binaires MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2edfd4b9391beed5c379817c55871759ff02eec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384926"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Propriétés réservées et connues de MSBuild

MSBuild fournit un ensemble de propriétés prédéfinies qui stockent des informations sur le fichier projet et les binaires MSBuild. Ces propriétés sont évaluées de la même manière que les autres propriétés MSBuild. Par exemple, pour utiliser la propriété `MSBuildProjectFile`, vous devez taper `$(MSBuildProjectFile)`.

 MSBuild utilise les valeurs du tableau ci-dessous pour prédéfinir les propriétés réservées et connues. Les propriétés réservées ne peuvent pas être remplacées, mais les propriétés connues peuvent être remplacées à l'aide des propriétés d'environnement du même nom, des propriétés globales ou des propriétés déclarées dans le fichier projet.

## <a name="reserved-and-well-known-properties"></a>Propriétés réservées et connues

Le tableau de cette section présente les propriétés prédéfinies de MSBuild. L’exemple de colonne dans la table est associé à l’exemple de fichier projet suivant, supposé être situé dans `C:\Source\Repos\ConsoleApp1\ConsoleApp1` , et indique que les valeurs de ces propriétés ont été consultées dans le fichier projet, lorsque MSBuild est appelé sans options de ligne de commande spéciales, avec une version préliminaire de Visual Studio 2019 version 16,7 installée.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

| Propriété | Réservée ou connue | Description | Exemple |
|----------------------------------|------------------------| - | - |
| `MSBuildBinPath` | Réservé | Chemin d’accès absolu du dossier dans lequel se trouvent les fichiers binaires MSBuild en cours d’utilisation (par exemple *, \\ \<versionNumber> C:\Windows\Microsoft.NET\Framework*). Cette propriété est utile si vous devez faire référence à des fichiers dans le répertoire MSBuild.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildExtensionsPath` | Connue | Introduite pour la première fois dans .NET Framework 4 : il n'existe aucune différence entre les valeurs par défaut de `MSBuildExtensionsPath` et de `MSBuildExtensionsPath32`. Vous pouvez affecter à la variable d'environnement `MSBUILDLEGACYEXTENSIONSPATH` une valeur non null pour activer le comportement de la valeur par défaut de `MSBuildExtensionsPath` dans les versions antérieures.<br /><br /> Dans .NET Framework 3.5 et versions antérieures, la valeur par défaut de `MSBuildExtensionsPath` pointe vers le chemin du sous-dossier MSBuild sous le dossier *\Program Files\\* ou *\Program Files (x86)*, en fonction du nombre de bits du processus actuel. Par exemple, pour un processus 32 bits sur un ordinateur 64 bits, la propriété pointe vers le dossier *\Program Files (x86)*. Pour un processus 64 bits sur un ordinateur 64 bits, la propriété pointe vers le dossier *\Program Files*.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété.<br /><br /> Cet emplacement est utile pour placer les fichiers cibles personnalisés. Par exemple, vos fichiers cibles peuvent être installés dans *\Program Files\MSBuild\MyFiles\Northwind.targets*, puis importés dans les fichiers projet à l’aide du code XML suivant :<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath32` | Connue | Chemin d’accès du sous-dossier MSBuild sous le dossier *\Program Files* ou *\Program Files (x86)* . Le chemin d’accès pointe toujours vers le dossier *\Program Files (x86)* 32 bits sur un ordinateur 32 bits et vers le dossier *\Program Files* sur un ordinateur 64 bits. Consultez également `MSBuildExtensionsPath` et `MSBuildExtensionsPath64`.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath64` | Connue | Chemin d’accès du sous-dossier MSBuild sous le dossier *\Program Files* . Pour un ordinateur 64 bits, ce chemin pointe toujours vers le dossier *\Program Files*. Pour un ordinateur 32 bits, ce chemin d'accès est vierge. Consultez également `MSBuildExtensionsPath` et `MSBuildExtensionsPath32`.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. | `C:\Program Files\MSBuild`|
| `MSBuildInteractive` | Réservé | `true` Si MSBuild s’exécute de manière interactive, ce qui permet l’entrée d’utilisateur. Ce paramètre est contrôlé par l' `-interactive` option de ligne de commande. | `false` |
| `MSBuildLastTaskResult` | Réservé | `true` si la tâche précédente s'est déroulée sans erreur (même avec des avertissements) ou `false` si la tâche précédente comportait des erreurs. En général, lorsqu'une erreur se produit dans une tâche, l'erreur représente la dernière chose qui se produit dans le projet. Par conséquent, la valeur de cette propriété n'est jamais `false`, sauf dans les scénarios suivants :<br /><br /> - Quand l’attribut `ContinueOnError` de [l’élément Task (MSBuild)](../msbuild/task-element-msbuild.md) est défini sur `WarnAndContinue` (ou `true`) ou `ErrorAndContinue`.<br /><br /> - Quand la `Target` possède un [élément OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) comme élément enfant. | `true` |
| `MSBuildNodeCount` | Réservé | Nombre maximal de processus simultanés utilisés lors de la génération. Il s’agit de la valeur que vous avez spécifiée pour **-maxcpucount** en ligne de commande. Si vous avez indiqué **-maxcpucount** sans spécifier de valeur, `MSBuildNodeCount` spécifie le nombre de processeurs sur l’ordinateur. Pour plus d’informations, voir [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md) et [Générer plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). | 1 |
| `MSBuildProgramFiles32` | Réservé | Emplacement du dossier du programme 32 bits, par exemple *C:\Program Files (x86)*.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. | `C:\Program Files (x86)`|
| `MSBuildProjectDefaultTargets` | Réservé | Liste complète des cibles qui sont spécifiées dans l'attribut `DefaultTargets` de l'élément `Project`. Par exemple, l'élément `Project` suivant aurait une valeur de propriété `MSBuildDefaultTargets` égale à `A;B;C` :<br /><br /> `<Project DefaultTargets="A;B;C" >` | `Build`|
| `MSBuildProjectDirectory` | Réservé | Chemin absolu du répertoire contenant le fichier projet, par exemple *C:\MyCompany\MyProduct*.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. | `C:\Source\Repos\ConsoleApp1\ConsoleApp1` |
| `MSBuildProjectDirectoryNoRoot` | Réservé | Valeur de la propriété `MSBuildProjectDirectory`, à l'exclusion du lecteur racine.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. | `Source\Repos\ConsoleApp1\ConsoleApp1`|
| `MSBuildProjectExtension` | Réservé | Extension de nom de fichier du fichier projet, y compris le point ; par exemple, *. proj*. | `.csproj`|
| `MSBuildProjectFile` | Réservé | Nom complet du fichier projet, avec l’extension de nom de fichier, par exemple *MyApp.proj*. | `ConsoleApp1.csproj`|
| `MSBuildProjectFullPath` | Réservé | Chemin absolu et nom complet du fichier projet, avec l’extension de nom de fichier, par exemple *C:\MyCompany\MyProduct\MyApp.proj*. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj`|
| `MSBuildProjectName` | Réservé | Nom du fichier projet sans l’extension de nom de fichier, par exemple *MyApp*. | `ConsoleApp1` |
| `MSBuildRuntimeType` | Réservé | Type du runtime en cours d’exécution. Introduit dans MSBuild 15. La valeur peut être non définie (avant MSBuild 15), `Full` indiquant que MSBuild s’exécute sur le bureau .NET Framework, `Core` ce qui indique que MSBuild s’exécute sur .net Core (par exemple `dotnet build` , dans), ou `Mono` indique que MSBuild s’exécute sur mono. | `Full` |
| `MSBuildStartupDirectory` | Réservé | Chemin d’accès absolu du dossier où MSBuild est appelé. À l’aide de cette propriété, vous pouvez créer tout ce qui se trouve sous un point spécifique dans une arborescence de projet sans créer de fichiers *\<dirs> . proj* dans chaque répertoire. À la place, vous avez un seul projet, par exemple *c:\traversal.proj*, comme indiqué ici :<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Pour générer des éléments en tout point de l'arborescence, tapez :<br /><br /> `msbuild c:\traversal.proj`<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. | `c:\Source\Repos\ConsoleApp1` |
| `MSBuildThisFile` | Réservé | Nom de fichier et partie de l'extension de fichier de `MSBuildThisFileFullPath`. | `ConsoleApp1.csproj` |
| `MSBuildThisFileDirectory` | Réservé | Partie de répertoire de `MSBuildThisFileFullPath`.<br /><br /> Incluez la barre oblique inverse finale dans le chemin. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileDirectoryNoRoot` | Réservé | Partie de répertoire de `MSBuildThisFileFullPath`, à l'exclusion du lecteur racine.<br /><br /> Incluez la barre oblique inverse finale dans le chemin. | `Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileExtension` | Réservé | Partie de l'extension du nom de fichier de `MSBuildThisFileFullPath`. | `.csproj` |
| `MSBuildThisFileFullPath` | Réservé | Chemin d’accès absolu du fichier projet ou de cibles qui contient la cible en cours d’exécution.<br /><br /> Conseil : vous pouvez spécifier un chemin d’accès relatif dans un fichier de cibles, qui se rapporte au fichier de cibles et non au fichier projet d’origine. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj` |
| `MSBuildThisFileName` | Réservé | Partie du nom de fichier de `MSBuildThisFileFullPath`, sans l'extension de nom de fichier. | `ConsoleApp1` |
| `MSBuildToolsPath` | Réservé | Chemin d’installation de la version MSBuild associée à la valeur de `MSBuildToolsVersion` .<br /><br /> N'incluez pas la barre oblique inverse finale dans le chemin.<br /><br /> Cette propriété ne peut pas être remplacée. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildToolsVersion` | Réservé | Version de l’ensemble d’outils MSBuild utilisé pour générer le projet.<br /><br /> Remarque : un ensemble d’outils MSBuild se compose des tâches, des cibles et des outils utilisés pour générer une application. Les outils incluent des compilateurs tels que *csc.exe* et *vbc.exe*. Pour plus d’informations, consultez ensemble d’outils [(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)et [configurations standard et personnalisée de l’ensemble d’outils](../msbuild/standard-and-custom-toolset-configurations.md). | `Current` |
| `MSBuildVersion` | Réservé | Version de MSBuild utilisée pour générer le projet. <br /><br/> Cette propriété ne peut pas être substituée, sinon le message d’erreur `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` est retourné. | 16.11.0 |
| `MSBuildAssemblyVersion` | Réservé | Version des assemblys MSBuild utilisée pour générer le projet. | 16,0 |
| `MSBuildFileVersion` | Réservé | Version 4 du composant des assemblys MSBuild utilisée pour générer le projet. | 16.11.0.30701 |
| `MSBuildSemanticVersion` | Réservé | Version semver 2,0 complète des assemblys MSBuild utilisés pour générer le projet. | 16.11.0-Preview-21302-05 + 5e37cc992 |

## <a name="names-that-conflict-with-msbuild-elements"></a>Noms en conflit avec des éléments MSBuild

En plus des éléments ci-dessus, les noms correspondant à des éléments de langage MSBuild ne peuvent pas être utilisés pour des propriétés, des éléments ou des métadonnées d’élément définis par l’utilisateur :

* VisualStudioProject
* Cible
* PropertyGroup
* Sortie
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Choose
* Lorsque le répertoire
* Otherwise

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)

- [MSBuild (propriétés)](../msbuild/msbuild-properties.md)
