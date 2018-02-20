---
title: "Propriétés réservées et connues de MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 89610426b944c3b3948c23c246337fd7aa9c1af8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild, propriétés réservées et connues
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fournit un jeu de propriétés prédéfinies qui stockent les informations relatives au fichier projet et aux binaires [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Ces propriétés sont évaluées de la même manière que les autres propriétés [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Par exemple, pour utiliser la propriété `MSBuildProjectFile`, vous devez taper `$(MSBuildProjectFile)`.  
  
 MSBuild utilise les valeurs du tableau ci-dessous pour prédéfinir les propriétés réservées et connues. Les propriétés réservées ne peuvent pas être remplacées, mais les propriétés connues peuvent être remplacées à l'aide des propriétés d'environnement du même nom, des propriétés globales ou des propriétés déclarées dans le fichier projet.  
  
## <a name="reserved-and-well-known-properties"></a>Propriétés réservées et connues  
 Le tableau ci-dessous décrit les propriétés prédéfinies de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
|Propriété|Description|Réservée ou connue|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Chemin d’accès absolu du dossier contenant les binaires [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] actuellement utilisés (par exemple, C:\Windows\Microsoft.Net\Framework\\*versionNumber*). Cette propriété est utile si vous devez faire référence à des fichiers dans le répertoire [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété.|Réservée|  
|`MSBuildExtensionsPath`|Introduite pour la première fois dans .NET Framework 4 : il n'existe aucune différence entre les valeurs par défaut de `MSBuildExtensionsPath` et de `MSBuildExtensionsPath32`. Vous pouvez affecter à la variable d'environnement `MSBUILDLEGACYEXTENSIONSPATH` une valeur non null pour activer le comportement de la valeur par défaut de `MSBuildExtensionsPath` dans les versions antérieures.<br /><br /> Dans .NET Framework 3.5 et les versions antérieures, la valeur par défaut de `MSBuildExtensionsPath` pointe vers le chemin d'accès du sous-dossier MSBuild sous le dossier \Program Files\ ou \Program Files (x86), en fonction du nombre de bits du processus actuel. Par exemple, pour un processus 32 bits sur un ordinateur 64 bits, la propriété pointe vers le dossier \Program Files (x86). Pour un processus 64 bits sur un ordinateur 64 bits, la propriété pointe vers le dossier \Program Files.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété.<br /><br /> Cet emplacement est utile pour placer les fichiers cibles personnalisés. Par exemple, vos fichiers cibles peuvent être installés dans \Program Files\MSBuild\MyFiles\Northwind.targets, puis importés dans les fichiers projet à l'aide du code XML suivant :<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|Connue|  
|`MSBuildExtensionsPath32`|Chemin du sous-dossier [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sous le dossier \Program Files ou \Program Files (x86). Ce chemin d'accès pointe toujours vers le dossier \Program Files 32 bits sur un ordinateur 32 bits et vers le dossier \Program Files (x86) sur un ordinateur 64 bits. Consultez également `MSBuildExtensionsPath` et `MSBuildExtensionsPath64`.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété.|Connue|  
`MSBuildExtensionsPath64`|Chemin d’accès du sous-dossier [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] figurant dans le dossier \Program Files. Pour un ordinateur 64 bits, ce chemin d’accès pointe toujours sur le dossier \Program Files. Pour un ordinateur 32 bits, ce chemin d'accès est vierge. Consultez également `MSBuildExtensionsPath` et `MSBuildExtensionsPath32`.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété.|Connue|  
|`MSBuildLastTaskResult`|`true` si la tâche précédente s'est déroulée sans erreur (même avec des avertissements) ou `false` si la tâche précédente comportait des erreurs. En général, lorsqu'une erreur se produit dans une tâche, l'erreur représente la dernière chose qui se produit dans le projet. Par conséquent, la valeur de cette propriété n'est jamais `false`, sauf dans les scénarios suivants :<br /><br /> -Lorsque l’attribut `ContinueOnError` de l’[élément Task (MSBuild)](../msbuild/task-element-msbuild.md) est défini sur `WarnAndContinue` (ou `true`) ou `ErrorAndContinue`.<br /><br /> -Lorsque la `Target` possède un [élément OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) comme élément enfant.|Réservée|  
|`MSBuildNodeCount`|Nombre maximal de processus simultanés utilisés lors de la génération. Il s’agit de la valeur que vous avez spécifiée pour **/maxcpucount** sur la ligne de commande. Si vous avez indiqué **/maxcpucount** sans spécifier de valeur, `MSBuildNodeCount` spécifie le nombre de processeurs sur l’ordinateur. Pour plus d’informations, consultez les articles [Command-Line Reference (Informations de référence sur la ligne de commande)](../msbuild/msbuild-command-line-reference.md) et [Building Multiple Projects in Parallel (Génération de plusieurs projets en parallèle avec MSBuild)](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Réservée|  
|`MSBuildProgramFiles32`|Emplacement du dossier du programme 32 bits. Par exemple, `C:\Program Files (x86)`.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété.|Réservée|  
|`MSBuildProjectDefaultTargets`|Liste complète des cibles qui sont spécifiées dans l'attribut `DefaultTargets` de l'élément `Project`. Par exemple, l'élément `Project` suivant aurait une valeur de propriété `MSBuildDefaultTargets` égale à `A;B;C` :<br /><br /> `<Project DefaultTargets="A;B;C" >`|Réservée|  
|`MSBuildProjectDirectory`|Chemin d'accès absolu du répertoire contenant le fichier projet, par exemple `C:\MyCompany\MyProduct`.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété.|Réservée|  
|`MSBuildProjectDirectoryNoRoot`|Valeur de la propriété `MSBuildProjectDirectory`, à l'exclusion du lecteur racine.<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété.|Réservée|  
|`MSBuildProjectExtension`|Extension de nom de fichier du fichier projet, y compris le point. Par exemple : .proj.|Réservée|  
|`MSBuildProjectFile`|Nom de fichier complet du fichier projet, y compris l'extension de nom de fichier. Par exemple : MyApp.proj.|Réservée|  
|`MSBuildProjectFullPath`|Chemin d'accès absolu et nom de fichier complet du fichier projet, notamment l'extension du nom de fichier. Par exemple : C:\MyCompany\MyProduct\MyApp.proj.|Réservée|  
|`MSBuildProjectName`|Nom de fichier du fichier projet sans l'extension de nom de fichier. Par exemple : MyApp.|Réservée|  
|`MSBuildRuntimeType`|Type du runtime en cours d’exécution. Introduit dans MSBuild 15. La valeur peut être indéfinie (avant MSBuild 15), `Full` (MSBuild s’exécute sur le .NET Framework Desktop), `Core` (MSBuild s’exécute sur .NET Core) ou `Mono` (MSBuild s’exécute sur Mono).|Réservée|  
|`MSBuildStartupDirectory`|Chemin d'accès absolu du dossier où [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] est appelé. Cette propriété vous permet de générer tout élément sous un point spécifique dans une arborescence du projet sans créer de fichiers dirs.proj dans chaque répertoire. À la place, vous avez un seul projet, par exemple, c:\traversal.proj, comme indiqué ici :<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Pour générer des éléments en tout point de l'arborescence, tapez :<br /><br /> `msbuild c:\traversal.proj`<br /><br /> N'incluez pas la barre oblique inverse finale dans cette propriété.|Réservée|  
|`MSBuildThisFile`|Nom de fichier et partie de l'extension de fichier de `MSBuildThisFileFullPath`.|Réservée|  
|`MSBuildThisFileDirectory`|Partie de répertoire de `MSBuildThisFileFullPath`.<br /><br /> Incluez la barre oblique inverse finale dans le chemin.|Réservée|  
|`MSBuildThisFileDirectoryNoRoot`|Partie de répertoire de `MSBuildThisFileFullPath`, à l'exclusion du lecteur racine.<br /><br /> Incluez la barre oblique inverse finale dans le chemin.|Réservée|  
|`MSBuildThisFileExtension`|Partie de l'extension du nom de fichier de `MSBuildThisFileFullPath`.|Réservée|  
|`MSBuildThisFileFullPath`|Chemin d’accès absolu du fichier projet ou de cibles qui contient la cible en cours d’exécution.<br /><br /> Conseil : vous pouvez spécifier un chemin d’accès relatif dans un fichier de cibles, qui se rapporte au fichier de cibles et non au fichier projet d’origine.|Réservée|  
|`MSBuildThisFileName`|Partie du nom de fichier de `MSBuildThisFileFullPath`, sans l'extension de nom de fichier.|Réservée|  
|`MSBuildToolsPath`|Chemin d'installation de la version de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] qui est associée à la valeur de `MSBuildToolsVersion`.<br /><br /> N'incluez pas la barre oblique inverse finale dans le chemin.<br /><br /> Cette propriété ne peut pas être remplacée.|Réservée|  
|`MSBuildToolsVersion`|Version de l'ensemble d'outils [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] qui est utilisée pour générer le projet.<br /><br /> Remarque : un ensemble d’outils [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se compose de tâches, de cibles et d’outils, qui sont utilisés pour générer une application. Les outils incluent des compilateurs tels que csc.exe et vbc.exe. Pour plus d’informations, consultez les articles [Toolset (ToolsVersion) Ensemble d’outils MSBuild [ToolsVersion])](../msbuild/msbuild-toolset-toolsversion.md) et [Configurations standard et personnalisée de l’ensemble d’outils](../msbuild/standard-and-custom-toolset-configurations.md).|Réservée|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence MSBuild](../msbuild/msbuild-reference.md) [Propriétés MSBuild](../msbuild/msbuild-properties.md)