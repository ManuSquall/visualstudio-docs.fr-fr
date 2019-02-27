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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35ef81aba75e42e7d3d713d5f6efb7129b55b2d2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632392"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Propriétés réservées et connues de MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fournit un jeu de propriétés prédéfinies qui stockent les informations relatives au fichier projet et aux binaires [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Ces propriétés sont évaluées de la même manière que les autres propriétés [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Par exemple, pour utiliser la propriété `MSBuildProjectFile`, vous devez taper `$(MSBuildProjectFile)`.

 MSBuild utilise les valeurs du tableau ci-dessous pour prédéfinir les propriétés réservées et connues. Les propriétés réservées ne peuvent pas être remplacées, mais les propriétés connues peuvent être remplacées à l'aide des propriétés d'environnement du même nom, des propriétés globales ou des propriétés déclarées dans le fichier projet.

## <a name="reserved-and-well-known-properties"></a>Propriétés réservées et connues
 Le tableau ci-dessous décrit les propriétés prédéfinies de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].


| Property | Réservée ou connue | Description |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Réservée | Chemin absolu du dossier contenant les binaires [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] actuellement utilisés (par exemple, *C:\Windows\Microsoft.Net\Framework\\\<NuméroVersion>*). Cette propriété est utile si vous devez faire référence à des fichiers dans le répertoire [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildExtensionsPath` | Connue | Introduite pour la première fois dans .NET Framework 4 : il n'existe aucune différence entre les valeurs par défaut de `MSBuildExtensionsPath` et de `MSBuildExtensionsPath32`. Vous pouvez affecter à la variable d'environnement `MSBUILDLEGACYEXTENSIONSPATH` une valeur non null pour activer le comportement de la valeur par défaut de `MSBuildExtensionsPath` dans les versions antérieures.<br /><br /> Dans .NET Framework 3.5 et versions antérieures, la valeur par défaut de `MSBuildExtensionsPath` pointe vers le chemin du sous-dossier MSBuild sous le dossier *\Program Files\\* ou *\Program Files (x86)*, en fonction du nombre de bits du processus actuel. Par exemple, pour un processus 32 bits sur un ordinateur 64 bits, la propriété pointe vers le dossier *\Program Files (x86)*. Pour un processus 64 bits sur un ordinateur 64 bits, la propriété pointe vers le dossier *\Program Files*.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété.<br /><br /> Cet emplacement est utile pour placer les fichiers cibles personnalisés. Par exemple, vos fichiers cibles peuvent être installés dans *\Program Files\MSBuild\MyFiles\Northwind.targets*, puis importés dans les fichiers projet à l’aide du code XML suivant :<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | Connue | Chemin du sous-dossier [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sous le dossier *\Program Files* ou *\Program Files (x86)*. Le chemin d’accès pointe toujours vers le dossier *\Program Files (x86)* 32 bits sur un ordinateur 32 bits et vers le dossier *\Program Files* sur un ordinateur 64 bits. Consultez également `MSBuildExtensionsPath` et `MSBuildExtensionsPath64`.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildExtensionsPath64` | Connue | Chemin du sous-dossier [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sous le dossier *\Program Files*. Pour un ordinateur 64 bits, ce chemin pointe toujours vers le dossier *\Program Files*. Pour un ordinateur 32 bits, ce chemin d'accès est vierge. Consultez également `MSBuildExtensionsPath` et `MSBuildExtensionsPath32`.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildLastTaskResult` | Réservée | `true` si la tâche précédente s'est déroulée sans erreur (même avec des avertissements) ou `false` si la tâche précédente comportait des erreurs. En général, lorsqu'une erreur se produit dans une tâche, l'erreur représente la dernière chose qui se produit dans le projet. Par conséquent, la valeur de cette propriété n'est jamais `false`, sauf dans les scénarios suivants :<br /><br /> - Quand l’attribut `ContinueOnError` de [l’élément Task (MSBuild)](../msbuild/task-element-msbuild.md) est défini sur `WarnAndContinue` (ou `true`) ou `ErrorAndContinue`.<br /><br /> - Quand la `Target` possède un [élément OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) comme élément enfant. |
| `MSBuildNodeCount` | Réservée | Nombre maximal de processus simultanés utilisés lors de la génération. Il s’agit de la valeur que vous avez spécifiée pour **-maxcpucount** en ligne de commande. Si vous avez indiqué **-maxcpucount** sans spécifier de valeur, `MSBuildNodeCount` spécifie le nombre de processeurs sur l’ordinateur. Pour plus d’informations, voir [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md) et [Générer plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). |
| `MSBuildProgramFiles32` | Réservée | Emplacement du dossier du programme 32 bits, par exemple *C:\Program Files (x86)*.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildProjectDefaultTargets` | Réservée | Liste complète des cibles qui sont spécifiées dans l'attribut `DefaultTargets` de l'élément `Project`. Par exemple, l'élément `Project` suivant aurait une valeur de propriété `MSBuildDefaultTargets` égale à `A;B;C` :<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Réservée | Chemin absolu du répertoire contenant le fichier projet, par exemple *C:\MyCompany\MyProduct*.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildProjectDirectoryNoRoot` | Réservée | Valeur de la propriété `MSBuildProjectDirectory`, à l'exclusion du lecteur racine.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildProjectExtension` | Réservée | Extension de nom du fichier projet, avec le point, par exemple *.proj*. |
| `MSBuildProjectFile` | Réservée | Nom complet du fichier projet, avec l’extension de nom de fichier, par exemple *MyApp.proj*. |
| `MSBuildProjectFullPath` | Réservée | Chemin absolu et nom complet du fichier projet, avec l’extension de nom de fichier, par exemple *C:\MyCompany\MyProduct\MyApp.proj*. |
| `MSBuildProjectName` | Réservée | Nom du fichier projet sans l’extension de nom de fichier, par exemple *MyApp*. |
| `MSBuildRuntimeType` | Réservée | Type du runtime en cours d’exécution. Introduit dans MSBuild 15. La valeur peut être indéfinie (avant MSBuild 15), `Full` (MSBuild s’exécute sur le .NET Framework Desktop), `Core` (MSBuild s’exécute sur .NET Core) ou `Mono` (MSBuild s’exécute sur Mono). |
| `MSBuildStartupDirectory` | Réservée | Chemin d'accès absolu du dossier où [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] est appelé. Cette propriété vous permet de générer tout élément sous un point spécifique dans une arborescence du projet sans créer de fichiers *\<dirs>.proj* dans chaque répertoire. À la place, vous avez un seul projet, par exemple *c:\traversal.proj*, comme indiqué ici :<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Pour générer des éléments en tout point de l'arborescence, tapez :<br /><br /> `msbuild c:\traversal.proj`<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété. |
| `MSBuildThisFile` | Réservée | Nom de fichier et partie de l'extension de fichier de `MSBuildThisFileFullPath`. |
| `MSBuildThisFileDirectory` | Réservée | Partie de répertoire de `MSBuildThisFileFullPath`.<br /><br /> Incluez la barre oblique inverse finale dans le chemin. |
| `MSBuildThisFileDirectoryNoRoot` | Réservée | Partie de répertoire de `MSBuildThisFileFullPath`, à l'exclusion du lecteur racine.<br /><br /> Incluez la barre oblique inverse finale dans le chemin. |
| `MSBuildThisFileExtension` | Réservée | Partie de l'extension du nom de fichier de `MSBuildThisFileFullPath`. |
| `MSBuildThisFileFullPath` | Réservée | Chemin d’accès absolu du fichier projet ou de cibles qui contient la cible en cours d’exécution.<br /><br /> Conseil : Vous pouvez spécifier un chemin d’accès relatif dans un fichier de cibles, qui se rapporte au fichier de cibles et non pas au fichier projet d’origine. |
| `MSBuildThisFileName` | Réservée | Partie du nom de fichier de `MSBuildThisFileFullPath`, sans l'extension de nom de fichier. |
| `MSBuildToolsPath` | Réservée | Chemin d'installation de la version de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] qui est associée à la valeur de `MSBuildToolsVersion`.<br /><br /> N'incluez pas la barre oblique inverse finale dans le chemin.<br /><br /> Cette propriété ne peut pas être remplacée. |
| `MSBuildToolsVersion` | Réservée | Version de l'ensemble d'outils [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] qui est utilisée pour générer le projet.<br /><br /> Remarque : Un ensemble d’outils [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se compose de tâches, de cibles et d’outils, utilisés pour générer une application. Les outils incluent des compilateurs tels que *csc.exe* et *vbc.exe*. Pour plus d’informations, voir [Ensemble d’outils (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) et [Configurations standard et personnalisées des ensembles d’outils](../msbuild/standard-and-custom-toolset-configurations.md). |

## <a name="names-that-conflict-with-msbuild-elements"></a>Noms en conflit avec des éléments MSBuild

En plus des éléments ci-dessus, les noms correspondant à des éléments de langage MSBuild ne peuvent pas être utilisés pour des propriétés, des éléments ou des métadonnées d’élément définis par l’utilisateur :

* VisualStudioProject
* une cible
* PropertyGroup
* Sortie
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Choisir
* When
* Otherwise

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)

- [Propriétés MSBuild](../msbuild/msbuild-properties.md)
