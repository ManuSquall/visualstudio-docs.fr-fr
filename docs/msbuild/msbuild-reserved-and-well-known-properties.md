---
title: Propriétés réservées et connues de MSBuild | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10b38ca4bfc0ea8a326f015228a4152779a41650
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633250"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Propriétés réservées et connues de MSBuild

MSBuild fournit un ensemble de propriétés prédéfinies qui stockent des informations sur le dossier du projet et les binaires MSBuild. Ces propriétés sont évaluées de la même manière que les autres propriétés MSBuild. Par exemple, pour utiliser la propriété `MSBuildProjectFile`, vous devez taper `$(MSBuildProjectFile)`.

 MSBuild utilise les valeurs du tableau ci-dessous pour prédéfinir les propriétés réservées et connues. Les propriétés réservées ne peuvent pas être remplacées, mais les propriétés connues peuvent être remplacées à l'aide des propriétés d'environnement du même nom, des propriétés globales ou des propriétés déclarées dans le fichier projet.

## <a name="reserved-and-well-known-properties"></a>Propriétés réservées et connues

 Le tableau suivant décrit les propriétés prédéfinies MSBuild.

| Propriété | Réservée ou connue | Description |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Réservé | Le chemin absolu du dossier où se trouvent les binaires MSBuild qui sont actuellement utilisés (par exemple, *C: 'Windows’Microsoft.Net-Framework\\\<versionNumber>*). Cette propriété est utile si vous devez vous référer à des fichiers dans l’annuaire MSBuild.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildExtensionsPath` | Connue | Introduite pour la première fois dans .NET Framework 4 : il n'existe aucune différence entre les valeurs par défaut de `MSBuildExtensionsPath` et de `MSBuildExtensionsPath32`. Vous pouvez affecter à la variable d'environnement `MSBUILDLEGACYEXTENSIONSPATH` une valeur non null pour activer le comportement de la valeur par défaut de `MSBuildExtensionsPath` dans les versions antérieures.<br /><br /> Dans .NET Framework 3.5 et versions antérieures, la valeur par défaut de `MSBuildExtensionsPath` pointe vers le chemin du sous-dossier MSBuild sous le dossier *\Program Files\\* ou *\Program Files (x86)*, en fonction du nombre de bits du processus actuel. Par exemple, pour un processus 32 bits sur un ordinateur 64 bits, la propriété pointe vers le dossier *\Program Files (x86)*. Pour un processus 64 bits sur un ordinateur 64 bits, la propriété pointe vers le dossier *\Program Files*.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété.<br /><br /> Cet emplacement est utile pour placer les fichiers cibles personnalisés. Par exemple, vos fichiers cibles peuvent être installés dans *\Program Files\MSBuild\MyFiles\Northwind.targets*, puis importés dans les fichiers projet à l’aide du code XML suivant :<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | Connue | Le chemin du sous-plieur MSBuild sous le *dossier « Dossiers de programme* » ou « *Dossiers de programme » (x86).* Le chemin d’accès pointe toujours vers le dossier *\Program Files (x86)* 32 bits sur un ordinateur 32 bits et vers le dossier *\Program Files* sur un ordinateur 64 bits. Consultez également `MSBuildExtensionsPath` et `MSBuildExtensionsPath64`.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildExtensionsPath64` | Connue | Le chemin du sous-plieur MSBuild sous le dossier *des fichiers de programme.* Pour un ordinateur 64 bits, ce chemin pointe toujours vers le dossier *\Program Files*. Pour un ordinateur 32 bits, ce chemin d'accès est vierge. Consultez également `MSBuildExtensionsPath` et `MSBuildExtensionsPath32`.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildInteractive` | Réservé | `true`si MSBuild fonctionne de manière interactive, permettant l’entrée de l’utilisateur. Ce paramètre est `-interactive` contrôlé par l’option de ligne de commande. |
| `MSBuildLastTaskResult` | Réservé | `true` si la tâche précédente s'est déroulée sans erreur (même avec des avertissements) ou `false` si la tâche précédente comportait des erreurs. En général, lorsqu'une erreur se produit dans une tâche, l'erreur représente la dernière chose qui se produit dans le projet. Par conséquent, la valeur de cette propriété n'est jamais `false`, sauf dans les scénarios suivants :<br /><br /> - Quand l’attribut `ContinueOnError` de [l’élément Task (MSBuild)](../msbuild/task-element-msbuild.md) est défini sur `WarnAndContinue` (ou `true`) ou `ErrorAndContinue`.<br /><br /> - Quand la `Target` possède un [élément OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) comme élément enfant. |
| `MSBuildNodeCount` | Réservé | Nombre maximal de processus simultanés utilisés lors de la génération. Il s’agit de la valeur que vous avez spécifiée pour **-maxcpucount** en ligne de commande. Si vous avez indiqué **-maxcpucount** sans spécifier de valeur, `MSBuildNodeCount` spécifie le nombre de processeurs sur l’ordinateur. Pour plus d’informations, voir [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md) et [Générer plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). |
| `MSBuildProgramFiles32` | Réservé | Emplacement du dossier du programme 32 bits, par exemple *C:\Program Files (x86)*.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildProjectDefaultTargets` | Réservé | Liste complète des cibles qui sont spécifiées dans l'attribut `DefaultTargets` de l'élément `Project`. Par exemple, l'élément `Project` suivant aurait une valeur de propriété `MSBuildDefaultTargets` égale à `A;B;C` :<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Réservé | Chemin absolu du répertoire contenant le fichier projet, par exemple *C:\MyCompany\MyProduct*.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildProjectDirectoryNoRoot` | Réservé | Valeur de la propriété `MSBuildProjectDirectory`, à l'exclusion du lecteur racine.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildProjectExtension` | Réservé | l’extension du nom de dossier du dossier du projet, y compris la période; par exemple, *.proj*. |
| `MSBuildProjectFile` | Réservé | Nom complet du fichier projet, avec l’extension de nom de fichier, par exemple *MyApp.proj*. |
| `MSBuildProjectFullPath` | Réservé | Chemin absolu et nom complet du fichier projet, avec l’extension de nom de fichier, par exemple *C:\MyCompany\MyProduct\MyApp.proj*. |
| `MSBuildProjectName` | Réservé | Nom du fichier projet sans l’extension de nom de fichier, par exemple *MyApp*. |
| `MSBuildRuntimeType` | Réservé | Type du runtime en cours d’exécution. Introduit dans MSBuild 15. La valeur peut être indéfinie (avant MSBuild `Full` 15), ce qui indique que `Core` MSBuild est en cours d’exécution `dotnet build`sur `Mono` le bureau .NET Framework, indiquant que MSBuild est en cours d’exécution sur .NET Core (par exemple dans ), ou indiquant que MSBuild est en cours d’exécution sur Mono. |
| `MSBuildStartupDirectory` | Réservé | Le chemin absolu du dossier où MSBuild est appelé. En utilisant cette propriété, vous pouvez construire tout ce qui est en dessous d’un point spécifique dans un arbre de projet sans créer * \<dirs>.proj* fichiers dans chaque répertoire. À la place, vous avez un seul projet, par exemple *c:\traversal.proj*, comme indiqué ici :<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Pour générer des éléments en tout point de l'arborescence, tapez :<br /><br /> `msbuild c:\traversal.proj`<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildThisFile` | Réservé | Nom de fichier et partie de l'extension de fichier de `MSBuildThisFileFullPath`. |
| `MSBuildThisFileDirectory` | Réservé | Partie de répertoire de `MSBuildThisFileFullPath`.<br /><br /> Incluez la barre oblique inverse finale dans le chemin. |
| `MSBuildThisFileDirectoryNoRoot` | Réservé | Partie de répertoire de `MSBuildThisFileFullPath`, à l'exclusion du lecteur racine.<br /><br /> Incluez la barre oblique inverse finale dans le chemin. |
| `MSBuildThisFileExtension` | Réservé | Partie de l'extension du nom de fichier de `MSBuildThisFileFullPath`. |
| `MSBuildThisFileFullPath` | Réservé | Chemin d’accès absolu du fichier projet ou de cibles qui contient la cible en cours d’exécution.<br /><br /> Conseil : vous pouvez spécifier un chemin d’accès relatif dans un fichier de cibles, qui se rapporte au fichier de cibles et non au fichier projet d’origine. |
| `MSBuildThisFileName` | Réservé | Partie du nom de fichier de `MSBuildThisFileFullPath`, sans l'extension de nom de fichier. |
| `MSBuildToolsPath` | Réservé | Le chemin d’installation de la version MSBuild `MSBuildToolsVersion`qui est associée à la valeur de .<br /><br /> N'incluez pas la barre oblique inverse finale dans le chemin.<br /><br /> Cette propriété ne peut pas être remplacée. |
| `MSBuildToolsVersion` | Réservé | La version de la MSBuild Toolset qui est utilisée pour construire le projet.<br /><br /> Remarque : Un outil MSBuild se compose de tâches, de cibles et d’outils utilisés pour construire une application. Les outils incluent des compilateurs tels que *csc.exe* et *vbc.exe*. Pour plus d’informations, voir [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)et [les configurations Standard and Custom Toolset](../msbuild/standard-and-custom-toolset-configurations.md). |
| `MSBuildVersion` | Réservé | La version de MSBuild utilisée pour construire le projet. <br /><br/> Cette propriété ne peut pas être substituée, sinon le message d’erreur `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` est retourné. |

## <a name="names-that-conflict-with-msbuild-elements"></a>Noms en conflit avec des éléments MSBuild

En plus des éléments ci-dessus, les noms correspondant à des éléments de langage MSBuild ne peuvent pas être utilisés pour des propriétés, des éléments ou des métadonnées d’élément définis par l’utilisateur :

* VisualStudioProject
* Cible
* PropertyGroup
* Output
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Choose
* Lorsque le répertoire
* Otherwise

## <a name="see-also"></a>Voir aussi

- [Référence MSBuild](../msbuild/msbuild-reference.md)

- [Propriétés MSBuild](../msbuild/msbuild-properties.md)
