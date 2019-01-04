---
title: Extensibilité de projet Visual C++
ms.date: 09/12/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0eccf13f38799c1d35b7fe4226fa02ec1a291b0c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986984"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio C++ Project system d’extensibilité et ensemble d’outils integration

Le *système de projet Visual C++* est utilisé pour les fichiers .vcxproj. Il est basé sur le [Visual Studio Common Project System (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) et fournit supplémentaires, des points d’extension spécifique de C++ pour faciliter l’intégration de nouveaux jeux d’outils, des architectures de build et des plateformes cibles. 

## <a name="c-msbuild-targets-structure"></a>Structure de cibles de MSBuild de C++

Tous les fichiers .vcxproj importer ces fichiers :

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Ces fichiers définissent peu de choses par eux-mêmes. Au lieu de cela, ils importent les autres fichiers en fonction de ces valeurs de propriété :

- `$(ApplicationType)`

   Exemples : Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Cela doit être une chaîne de version valide de la forme major.minor]].

   Exemples : les versions 1.0, 10.0.0.0

- `$(Platform)`

   L’architecture de la build, nommé « Plateforme » pour des raisons historiques.

   Exemples : Win32, x86, x64, ARM   

- `$(PlatformToolset)`

   Exemples : v140, v141, v141_xp, llvm

Ces valeurs de propriété spécifient les noms de dossiers sous le `$(VCTargetsPath)` dossier racine :

> `$(VCTargetsPath)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;*Type d’application*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Plateformes*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Ensemble*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  
> &nbsp;&nbsp;&nbsp;&nbsp;Plateformes\\&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(utilisée lorsque `$(ApplicationType)` est vide pour les projets de bureau de Windows)  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Ensemble*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  

### <a name="add-a-new-platform-toolset"></a>Ajouter un nouvel ensemble d’outils de plateforme

Pour ajouter un nouvel ensemble d’outils, par exemple, « MyToolset » pour la plateforme Win32 existante, créez un *MyToolset* dossier sous `$(VCTargetsPath)`  *\\plateformes\\Win32\\ Ensemble\\*et créer *Toolset.props* et *Toolset.targets* fichiers qu’il contient.

Chaque nom de dossier sous *ensemble* s’affiche dans le **propriétés du projet** boîte de dialogue comme une disponible **ensemble d’outils de plateforme** pour la plateforme spécifiée, comme illustré ici :

![La propriété de l’ensemble d’outils de plateforme dans la boîte de dialogue Pages de propriétés projet](media/vc-project-extensibility-platform-toolset-property.png "propriété de l’ensemble d’outils de plateforme dans la boîte de dialogue Pages de propriétés du projet")

Créer similaire *MyToolset* dossiers et *Toolset.props* et *Toolset.targets* files dans chaque dossier existant de la plateforme prend en charge par cet ensemble d’outils.

### <a name="add-a-new-platform"></a>Ajouter une nouvelle plateforme

Pour ajouter une nouvelle plateforme, par exemple, « MyPlatform », créez un *MyPlatform* dossier sous `$(VCTargetsPath)`  *\\plateformes\\*et créer  *Platform.Default.props*, *Platform.props*, et *Platform.targets* fichiers qu’il contient. Créez également un `$(VCTargetsPath)`  *\\plateformes\\*<strong><em>MyPlatform</em></strong>*\\ensemble\\*  dossier et créez au moins un ensemble d’outils qu’il contient.

Tous les noms de dossiers sous le *plateformes* dossier pour chaque `$(ApplicationType)` et `$(ApplicationTypeRevision)` apparaissent dans l’IDE comme étant disponibles **plateforme** choix pour un projet.

![La nouvelle plateforme choisie dans la boîte de dialogue Nouvelle plateforme de projet](media/vc-project-extensibility-new-project-platform.png "la nouvelle plate-forme de choix dans la boîte de dialogue Nouvelle plateforme de projet")

### <a name="add-a-new-application-type"></a>Ajouter un nouveau Type d’Application

Pour ajouter un nouveau type d’application, créez un *MyApplicationType* dossier sous `$(VCTargetsPath)` *\\Type d’Application\\* et créer un *Defaults.props* fichier qu’il contient. Au moins une révision est obligatoire pour un type d’application, donc également créer un `$(VCTargetsPath)`  *\\Type d’Application\\MyApplicationType\\1.0* dossier et créer un  *Defaults.props* fichier qu’il contient. Vous devez également créer un `$(VCTargetsPath)`  *\\ApplicationType\\MyApplicationType\\1.0\\plateformes* dossier et créer au moins une plateforme qu’elle contient.

`$(ApplicationType)` et `$(ApplicationTypeRevision)` propriétés ne sont pas visibles dans l’interface utilisateur. Ils sont définis dans les modèles de projet et ne peut pas être modifiées une fois que le projet est créé.


## <a name="the-vcxproj-import-tree"></a>L’arborescence d’importation .vcxproj

Une arborescence simplifiée des importations pour les fichiers de cibles et les propriétés de Microsoft C++ ressemble à :

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*par défaut*\\\*. *props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Type d’application*\\`$(ApplicationType)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Type d’application*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Type d’application*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*plateformes* \\ `$(Platform)` \\  *Platform.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*par défaut*\\\*. *props*  

Ne définissent pas les projets Windows Desktop `$(ApplicationType)`, donc ils importent uniquement

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*par défaut*\\\*. *props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Plateformes*\\`$(Platform)`\\*Platform.default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*par défaut*\\\*. *props*  

Nous allons utiliser le `$(_PlatformFolder)` propriété permettant de contenir le `$(Platform)` emplacements de dossier de plateforme. Cette propriété est 

> `$(VCTargetsPath)`\\*Plateformes*\\`$(Platform)`

pour les applications de bureau Windows, et 

> `$(VCTargetsPath)`\\*Type d’application*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*plateformes*\\`$(Platform)`

pour tout le reste.

Les fichiers props sont importés dans cet ordre :

> `$(VCTargetsPath)`\\*Microsoft.Cpp.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Ensemble*\\`$(PlatformToolset)`\\*Toolset.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *props*  

Les fichiers cibles sont importés dans cet ordre :

> `$(VCTargetsPath)`\\*Microsoft.Cpp.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Current.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *cibles*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Ensemble*\\`$(PlatformToolset)`\\*Toolset.target*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *cibles*  

Si vous devez définir certaines propriétés par défaut pour votre boîte à outils, vous pouvez ajouter des fichiers dans les dossiers ImportBefore et ImportAfter appropriés.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Fichiers auteur Toolset.props et Toolset.targets

*Toolset.props* et *Toolset.targets* fichiers ont un contrôle total sur ce qui se passe lors d’une génération cet ensemble d’outils est utilisée. Il peut également contrôler les débogueurs disponibles, partie de l’interface utilisateur IDE, tel que le contenu dans le **Pages de propriétés** boîte de dialogue et d’autres aspects du comportement du projet.

Bien qu’un ensemble d’outils peut remplacer le processus de génération entière, généralement vous que vous voulez uniquement votre boîte à outils pour modifier ou ajouter que certaines étapes de génération, ou utiliser des outils de build différente, dans le cadre d’un processus de build existant. Pour atteindre cet objectif, il existe un nombre de votre boîte à outils peut importer les fichiers cibles et propriétés communs. Selon ce que vous souhaitez effectuer votre boîte à outils, ces fichiers peuvent être utiles à utiliser en tant qu’importations ou comme exemples :

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

   Ce fichier définit les principales parties du processus de génération natif et importe également :

   - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

   - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

   - `$(MSBuildToolsPath)`\\*Microsoft.Common.Targets*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   Définit les valeurs par défaut pour les ensembles d’outils qui utilisent les compilateurs Microsoft et de cibler Windows.

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   Ce fichier détermine l’emplacement du SDK Windows et définit certaines propriétés importantes pour les applications ciblant Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Intégrer des cibles spécifiques de l’ensemble d’outils à la valeur par défaut de processus de génération C++ 

La valeur par défaut de processus de génération C++ est défini dans *Microsoft.CppCommon.targets*. Il les cibles n’appellent pas les outils de génération spécifique ; ils spécifient les principaux générer étapes, leur ordre et des dépendances.

La build C++ comporte trois étapes principales, représentés par les cibles suivantes :

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Étant donné que chaque étape de génération peut-être être exécutée indépendamment, les cibles en cours d’exécution en une seule étape ne peut pas s’appuient sur les groupes d’éléments et les propriétés définies dans les cibles qui s’exécutent dans le cadre d’une autre étape. Cette division permet à certains build optimisations des performances. Bien qu’il n’est pas utilisé par défaut, vous êtes toujours invités à honorer cette séparation.

Les cibles qui sont exécutées à l’intérieur de chaque étape sont contrôlées par ces propriétés :

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Chaque étape comporte également avant et après les propriétés. 

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

Consultez le *Microsoft.CppBuild.targets* fichier pour obtenir des exemples de cibles qui sont inclus dans chaque étape :

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Si vous examinez les cibles, tel que `_ClCompile`, vous verrez qu’ils ne font rien directement par eux-mêmes, mais au lieu de cela dépendent d’autres cibles, y compris `ClCompile`:

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` et autres génération des cibles spécifiques de l’outil sont définis en tant que cibles vides dans *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"/>
```

Étant donné que le `ClCompile` cible est vide, sauf si elle est substituée par un ensemble d’outils, aucune action de génération réelle est effectuée. Les cibles de l’ensemble d’outils peuvent remplacer le `ClCompile` cibler, autrement dit, elles peuvent contenir un autre `ClCompile` définition après l’importation *Microsoft.CppBuild.targets*: 

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Malgré son nom, ce qui a été créé avant que Visual Studio implémenté la prise en charge multiplateforme, le `ClCompile` cible n’a pas à appeler CL.exe. Elle peut également appeler Clang, gcc ou autres compilateurs à l’aide des tâches MSBuild appropriées.

Le `ClCompile` cible ne doit pas avoir de dépendances, à l’exception du `SelectClCompile` cible, qui est requis pour la commande de compilation de fichier unique à utiliser dans l’IDE.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Tâches MSBuild à utiliser dans les cibles de l’ensemble d’outils

Pour appeler un outil de génération réelle, la cible doit appeler une tâche MSBuild. Il existe un basic [Exec, tâche](../msbuild/exec-task.md) qui vous permet de spécifier une ligne de commande à exécuter. Toutefois, les outils de génération ont généralement des nombreuses options, entrées. et les sorties pour effectuer le suivi pour les builds incrémentielles, donc il est plus judicieux d’avoir des tâches spéciales pour eux. Par exemple, le `CL` tâche traduit les propriétés MSBuild CL.exe commutateurs, les écrit dans un fichier réponse et appelle CL.exe. Il effectue également le suivi de tous les fichiers d’entrée et de sortie pour les générations incrémentielles ultérieures. Pour plus d’informations, consultez [build incrémentielle et les vérifications de statut](#incremental-build-and-up-to-date-check).

Le Microsoft.Cpp.Common.Tasks.dll implémente ces tâches :

- `BSCMake`

- `CL`

- `ClangCompile` (clang-gcc commutateurs)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (comme Exec mais avec entrée et sortie de suivi)

- `SetEnv`

Si vous avez un outil qui effectue la même action comme un outil existant et qui a des commutateurs de ligne de commande similaires (comme clang-cl et CL), vous pouvez utiliser la même tâche pour chacun d’eux.

Si vous avez besoin créer une nouvelle tâche pour un outil de génération, vous pouvez choisir parmi les options suivantes :

1. Si vous utilisez cette tâche rarement, ou si quelques secondes n’a pas d’importance pour votre build, vous pouvez utiliser les tâches MSBuild 'inline' :

   - Tâche de XAML (une règle de génération personnalisée)

     Pour obtenir un exemple d’une déclaration de la tâche Xaml, consultez `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*et pour son utilisation, consultez `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets*.

   - [Tâche de code](../msbuild/msbuild-inline-tasks.md)

1. Si vous souhaitez que les meilleures performances de la tâche ou simplement besoin des fonctionnalités plus complexes, utiliser MSBuild régulière [écriture de tâches](../msbuild/task-writing.md) processus.

   Si pas toutes les entrées et sorties de l’outil sont répertoriés sur la ligne de commande d’outil, comme dans le `CL`, `MIDL`, et `RC` cas et si vous souhaitez entrée automatique et suivi des fichiers de sortie et la création de fichiers .tlog, dériver votre tâche le `Microsoft.Build.CPPTasks.TrackedVCToolTask`classe. À l’heure actuelle, bien qu’il existe de documentation pour la base de [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) class, aucun exemples ou la documentation pour les détails de la `TrackedVCToolTask` classe. Si cela est particulièrement intéressante, ajouter votre voix à une demande sur [developercommunity.visualstudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="incremental-builds-and-up-to-date-checks"></a>Les builds incrémentielles et les vérifications à jour

La génération incrémentielle de MSBuild par défaut cible utilisation `Inputs` et `Outputs` attributs. Si vous les spécifiez, MSBuild appelle la cible uniquement si une des entrées a un horodatage plus récent que toutes les sorties. Étant donné que les fichiers sources souvent incluant ou importer d’autres fichiers et générer outils produisent des résultats différents selon les options de l’outil, il est difficile de spécifier toutes les entrées possibles et les sorties de cibles de MSBuild.

Pour gérer ce problème, la build C++ utilise une technique différente pour prendre en charge les générations incrémentielles. La plupart des cibles ne spécifier les entrées et sorties et par conséquent, s’exécutent toujours pendant la génération. Les tâches appelés par les cibles écrivent des informations sur toutes les entrées et sorties dans *tlog* fichiers ayant une extension .tlog. Fichiers TLog sont utilisés par les versions ultérieures pour vérifier ce qui a changé et doit être reconstruit, et ce qui est à jour.

Pour déterminer toutes les entrées et sorties, les tâches de l’outil native utilisent tracker.exe et [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) classe fournie par MSBuild.

Microsoft.Build.CPPTasks.Common.dll définit le `TrackedVCToolTask` classe de base abstraite publique. La plupart des tâches de l’outil natif est dérivée de cette classe.

## <a name="tlog-files"></a>fichiers TLog

Il existe trois types de fichiers TLog : *lire*, *écrire*, et *de ligne de commande*. Les fichiers TLog en lecture et écriture sont utilisées par les builds incrémentielles et par la vérification à jour dans l’IDE. Fichiers TLog de ligne de commande sont uniquement utilisés dans les builds incrémentielles.

MSBuild fournit ces classes d’assistance pour lire et écrire des fichiers TLog :

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

Le [FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) classe peut être utilisée pour accéder en lecture et écriture de fichiers TLog et identifier les entrées les plus récentes à des sorties, ou si une sortie est manquante. Il est utilisé dans la vérification à jour.

Fichiers TLog de ligne de commande contiennent des informations sur les lignes de commande utilisées dans la build. Ils sont utilisés uniquement pour les builds incrémentielles, les vérifications de pas à jour, donc le format interne est déterminé par la tâche MSBuild qui génère les.

Si les fichiers .tlog sont créés par une tâche, il est préférable d’utiliser ces classes d’assistance pour les créer. Toutefois, étant donné que la vérification à jour par défaut s’appuie uniquement sur les fichiers TLog, il est parfois plus pratique de les afficher dans une cible sans une tâche. Vous pouvez les écrire en utilisant le `WriteLinesToFile` tâche. Consultez le `_WriteMasmTlogs` cibler dans `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets* comme exemple.

### <a name="read-tlog-format"></a>Format de .tlog lire

*Lecture* fichiers TLog (\*fichiers TLog .read.\*. tlog) contiennent des informations sur les fichiers sources et leurs dépendances.

Un accent circonflexe (**^**) au début d’une ligne indique une ou plusieurs sources. Sources qui partagent les mêmes dépendances sont séparés par une barre verticale (**\|**).

Fichiers de dépendance sont répertoriés après les sources, chacun sur sa propre ligne. Tous les noms de fichier sont des chemins d’accès complets.

Par exemple, supposons que vos sources de projet sont trouvent dans *F:\\tester\\ConsoleApplication1\\ConsoleApplication1*. Si votre fichier source, *Class1.cpp*, lequel ces inclut,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

le *CL.read.1.tlog* fichier contient le fichier source suivi de ses deux dépendances :

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Il n’est pas nécessaire d’écrire des noms de fichiers en majuscules, mais il est pratique pour certains outils.

### <a name="write-tlog-format"></a>Écrire .tlog format

*Écrire* .tlog (\*.write.\*. fichiers TLog) connectent les sources et sorties.

Un accent circonflexe (**^**) au début d’une ligne indique une ou plusieurs sources. Plusieurs sources sont séparés par une barre verticale (**\|**).

Les fichiers de sortie générés à partir des sources doivent figurer après les sources, chacun sur sa propre ligne. Tous les noms de fichiers doivent être des chemins d’accès complets.

Par exemple, pour un projet simple ConsoleApplication contenant déjà un fichier source supplémentaire *Class1.cpp*, le *link.write.1.tlog* fichier peut contenir :

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Au moment du design build

Dans l’IDE, .vcxproj projets utilisent un jeu de cibles de MSBuild pour obtenir des informations supplémentaires à partir du projet et régénérer les fichiers de sortie. Certaines de ces cibles sont utilisés uniquement dans les builds au moment du design, mais bon nombre d'entre eux sont utilisés dans des builds normales et les builds au moment du design.

Pour obtenir des informations générales sur les builds au moment du design, consultez la documentation de CPS pour [génère au moment du Design](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Cette documentation s’en partie applique uniquement aux projets Visual C++.

Le `CompileDesignTime` et `Compile` cibles mentionnés dans le temps de conception s’appuie documentation jamais exécutée pour les projets .vcxproj. Des projets Visual C++ .vcxproj utilisent différentes cibles au moment du design pour obtenir des informations IntelliSense.

### <a name="design-time-targets-for-intellisense-information"></a>Cibles au moment du design pour les informations IntelliSense

Les cibles au moment du design utilisés dans les projets .vcxproj sont définies dans `$(VCTargetsPath)` \\ *Microsoft.Cpp.DesignTime.targets*.

Le `GetClCommandLines` cible collecte les options du compilateur pour IntelliSense :

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` – au moment du design uniquement l’initialisation de build de cibles, nécessaires pour le moment du design. Entre autres choses, ces cibles de désactiver certaines fonctionnalités de build standard pour améliorer les performances.

- `ComputeCompileInputsTargets` – un ensemble de cibles qui modifie les options du compilateur et des éléments. Ces cibles sont exécutées dans les builds au moment du design et régulières.

Les appels cible le `CLCommandLine` tâche à créer la ligne de commande à utiliser pour IntelliSense. Là encore, en dépit de son nom, elle peut gérer non seulement des options CL, mais également les options Clang et gcc. Le type des commutateurs du compilateur est contrôlé par le `ClangMode` propriété.

Actuellement, la ligne de commande généré par le `CLCommandLine` tâche utilise toujours les commutateurs CL (même en mode de Clang), car elles sont plus faciles pour le moteur IntelliSense puisse analyser.

Si vous ajoutez une cible qui s’exécute avant la compilation, ordinaires ou au moment du design, assurez-vous qu’il ne s’arrête pas au moment du design génère ou affecter les performances. Pour tester votre cible, le plus simple consiste à ouvrir une invite de commandes développeur et exécutez la commande suivante :

> MSBuild /p:SolutionDir =*solution-directory-avec-fin-barre oblique inverse*; Configuration = Debug ; Plateforme = Win32 ; BuildingInsideVisualStudio = true ; DesignTimebuild = true/t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj

Cette commande génère un journal de génération détaillées, *msbuild.log*, qui se termine par un résumé pour les cibles et les tâches des performances.

Veillez à utiliser `Condition ="'$(DesignTimeBuild)' != 'true'"` dans toutes les opérations qui ne sont pertinentes pour des builds normales et non pour les builds au moment du design.

### <a name="design-time-targets-that-generate-sources"></a>Cibles au moment du design qui génèrent des sources

*Cette fonctionnalité est désactivée par défaut pour les projets de bureau natives et n’est pas actuellement pris en charge sur les projets mis en cache*.

Si `GeneratorTarget` métadonnées sont définie pour un élément de projet, la cible est exécutée automatiquement à la fois lorsque le projet est chargé et lorsque le fichier source est modifié.

Par exemple, pour générer automatiquement .cpp ou .h des fichiers à partir de fichiers .xaml, le `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\  *WindowsXaml*\\*v15.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets* fichiers définissent ces entités :

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

Pour utiliser `Task.HostObject` pour obtenir le contenu non enregistré des fichiers sources, les cibles et la tâche doivent être inscrit en tant que [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) pour les projets donnés dans un pkgdef :

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Extensibilité de projet Visual C++ dans l’IDE Visual Studio

Le système de projet Visual C++ est basé sur le [système de projet Visual Studio](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)et utilise ses points d’extensibilité. Toutefois, l’implémentation de hiérarchie de projet est spécifique à Visual C++, et ne pas basé sur CPS, extensibilité de la hiérarchie est donc limitée aux éléments de projet.

### <a name="project-property-pages"></a>Pages de propriétés du projet

Pour plus d’informations générales de conception, consultez [extensibilité des plateformes - partie 1](https://blogs.msdn.microsoft.com/vsproject/2009/06/09/platform-extensibility-part-1/) et [extensibilité des plateformes - partie 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/).

En termes simples, les pages de propriétés que vous consultez dans la **propriétés du projet** boîte de dialogue pour un projet C++ sont définis par *règle* fichiers. Un fichier de règle spécifie un jeu de propriétés à afficher sur une page de propriétés et comment et où ils doivent être enregistrés dans le projet de fichier. Fichiers de règles sont des fichiers .xml qui utilisent le format Xaml. Les types utilisés pour sérialiser les sont décrites dans [Microsoft.Build.Framework.XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Pour plus d’informations sur l’utilisation de fichiers de règles dans les projets, consultez [les fichiers de règles XML de la Page propriété](/cpp/ide/property-page-xml-files).

Les fichiers de la règle doivent être ajoutés à la `PropertyPageSchema` groupe d’éléments :

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` limites règle la visibilité des métadonnées, qui est également contrôlée par le type de règle et peut avoir une des valeurs suivantes :

> `Project` | `File` | `PropertySheet`

CPS prend en charge les autres valeurs pour le type de contexte, mais ils ne sont pas utilisés dans les projets Visual C++.

Si la règle doit être visible dans plusieurs contextes, utilisez des points-virgules (**;**) pour séparer les valeurs de contexte, comme illustré ici :

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Format de la règle et les types principaux

Le format de la règle est simple, donc cette section décrit uniquement les attributs qui affectent l’apparence de la règle dans l’interface utilisateur.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

Le `PageTemplate` attribut définit comment la règle s’affiche dans le **Pages de propriétés** boîte de dialogue. L’attribut peut avoir une des valeurs suivantes :


| Attribut | Description |
|------------| - |
| `generic` | Toutes les propriétés sont affichées sur une page sous les en-têtes des catégories<br/>La règle peut être visible pour `Project` et `PropertySheet` contextes, mais pas `File`.<br/><br/> Exemple : `$(VCTargetsPath)`\\*1033*\\*general.xml* |
| `tool` | Catégories sont affichées en tant que pages secondaires.<br/>La règle peut être visible dans tous les contextes : `Project`, `PropertySheet` et `File`.<br/>La règle est visible dans les propriétés du projet uniquement si le projet comporte des éléments avec le `ItemType` définies dans `Rule.DataSource`, sauf si le nom de la règle est inclus dans le `ProjectTools` groupe d’éléments.<br/><br/>Exemple : `$(VCTargetsPath)`\\*1033*\\*clang.xml* |
| `debugger` | La page est affichée dans le cadre de la page de débogage.<br/>Catégories sont ignorés actuellement.<br/>Le nom de la règle doit correspondre à l’objet MEF de Lanceur de débogage `ExportDebugger` attribut.<br/><br/>Exemple : `$(VCTargetsPath)`\\*1033*\\*débogueur\_local\_windows.xml* |
| *custom* | Modèle personnalisé. Le nom du modèle doit correspondre à la `ExportPropertyPageUIFactoryProvider` attribut de la `PropertyPageUIFactoryProvider` objet MEF. Consultez **Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**.<br/><br/> Exemple : `$(VCTargetsPath)`\\*1033*\\*userMacros.xml* |

Si la règle utilise un des modèles basée sur la grille des propriétés, il peut utiliser ces points d’extensibilité pour ses propriétés :

- [Éditeurs de valeurs de propriété](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Fournisseur de valeurs d’énumération dynamique](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Étendre une règle

Si vous souhaitez utiliser une règle existante, mais devez ajouter ou supprimer (qui est, masquer) seulement quelques propriétés, vous pouvez créer un [règle d’Extension](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Remplacer une règle

Peut-être voulez-vous votre boîte à outils à utiliser la plupart des règles projet par défaut, mais pour remplacer simplement un ou plusieurs d'entre eux. Par exemple, supposons que vous souhaitez uniquement modifier la règle de C/C++ pour afficher les commutateurs du compilateur différents. Vous pouvez fournir une nouvelle règle portant le même nom et nom complet en tant que la règle existante et l’inclure dans le `PropertyPageSchema` groupe d’éléments après l’importation des cibles de cpp par défaut. Qu’une seule règle avec un nom donné est utilisée dans le projet, et il est inclus dans le `PropertyPageSchema` élément groupes l’emporte.

#### <a name="project-items"></a>Éléments de projet

Le *ProjectItemsSchema.xml* fichier définit les `ContentType` et `ItemType` de valeurs pour les éléments qui sont traités comme des éléments de projet et définit `FileExtension` éléments pour déterminer un nouveau fichier est ajouté à quel groupe d’éléments.

Le fichier ProjectItemsSchema par défaut se trouve dans `$(VCTargetsPath)` \\ *1033*\\*ProjectItemsSchema.xml*. À cette fin, vous devez créer un fichier de schéma avec un nouveau nom, tel que *MyProjectItemsSchema.xml*:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

Ensuite, dans le fichier de cibles, ajoutez :

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Exemple : `$(VCTargetsPath)`\\*BuildCustomizations*\\*masm.xml*

### <a name="debuggers"></a>Débogueurs

Le service de débogage dans Visual Studio prend en charge l’extensibilité pour le moteur de débogage. Pour plus d’informations, consultez ces exemples :

- [MIEngine, projet open source qui prend en charge le débogage lldb](https://github.com/Microsoft/MIEngine)

- [Exemples du moteur de débogage Visual Studio](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Pour spécifier les moteurs de débogage et d’autres propriétés de la session de débogage, vous devez implémenter un [déboguer le Lanceur](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) composant MEF et ajoutez un `debugger` règle. Pour obtenir un exemple, consultez le `$(VCTargetsPath)` \\1033\\débogueur\_local\_windows.xml fichier.

### <a name="deploy"></a>Déployer

projets de .vcxproj utilisent l’extensibilité du système de projet Visual Studio pour [fournisseurs déployer](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Générer des vérifications de statut

Par défaut, la vérification de build à jour requiert des fichiers TLog lecture .tlog et d’écriture doit être créé dans le `$(TlogLocation)` dossier lors de la génération pour toutes les entrées de génération et les sorties.

Pour utiliser un contrôle personnalisé à jour :

1. Désactiver la vérification à jour par défaut en ajoutant le `NoVCDefaultBuildUpToDateCheckProvider` fonctionnalité dans le *Toolset.targets* fichier :

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Implémenter votre propre [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Mise à niveau du projet

### <a name="default-vcxproj-project-upgrader"></a>Upgrader de projet .vcxproj par défaut

Par défaut .vcxproj projet upgrader devient le `PlatformToolset`, `ApplicationTypeRevision`, framework de version et .net d’ensemble d’outils MSBuild. Les deux dernières sont toujours remplacés par les valeurs par défaut de la version de Visual Studio, mais `PlatformToolset` et `ApplicationTypeRevision` peuvent être contrôlées par les propriétés MSBuild spéciales.

Le programme upgrader utilise ces critères pour déterminer si un projet peut être mis à niveau ou non :

1. Pour les projets qui définissent `ApplicationType` et `ApplicationTypeRevision`, il existe un dossier avec un numéro de révision supérieur à celui en cours.

1. La propriété `_UpgradePlatformToolsetFor_<safe_toolset_name>` est défini pour l’ensemble d’outils actuel, et sa valeur n’est pas égale à l’ensemble d’outils actuel.

   Dans ces noms de propriétés,  *\<safe_toolset_name >* représente le nom de l’ensemble d’outils avec tous les caractères non alphanumériques remplacés par un trait de soulignement (**\_**).

Quand un projet peut être mis à niveau, il participe à *reciblage de la Solution*. Pour plus d’informations, consultez [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Si vous souhaitez orner des noms de projets dans **l’Explorateur de solutions** lorsque les projets utilisent un ensemble d’outils spécifique, définissez un `_PlatformToolsetShortNameFor_<safe_toolset_name>` propriété.

Pour obtenir des exemples de `_UpgradePlatformToolsetFor_<safe_toolset_name>` et `_PlatformToolsetShortNameFor_<safe_toolset_name>` des définitions de propriété, consultez le *Microsoft.Cpp.Default.props* fichier. Pour obtenir des exemples d’utilisation, consultez le `$(VCTargetPath)` \\ *Microsoft.Cpp.Platform.targets* fichier.

### <a name="custom-project-upgrader"></a>Upgrader de projet personnalisé

Pour utiliser un objet upgrader de projet personnalisés, implémentez un composant MEF, comme illustré ici :

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

Votre code peut importer et appeler l’objet d’upgrader .vcxproj par défaut :

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` est défini dans *Microsoft.VisualStudio.ProjectSystem.VS.dll* et est semblable à `IVsRetargetProjectAsync`.

Définir le `VCProjectUpgraderObjectName` propriété pour informer le système de projet à utiliser votre objet personnalisé upgrader :

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Désactiver la mise à niveau du projet

Pour désactiver les mises à niveau du projet, utilisez un `NoUpgrade` valeur :

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Le cache de projet et l’extensibilité

Pour améliorer les performances lorsque vous travaillez avec grandes solutions de C++ dans Visual Studio 2017, le [projet cache](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-solution-load-with-vs-15/) a été introduit. Il est implémenté comme une base de données SQLite rempli avec les données de projet et ensuite utilisé pour charger des projets sans charger des projets MSBuild ou CPS en mémoire.

Comme il n’y a aucun objet CPS présentes pour les projets .vcxproj chargés à partir du cache, les composants MEF de l’extension importer `UnconfiguredProject` ou `ConfiguredProject` ne peut pas être créé. Pour prendre en charge d’extensibilité, le cache du projet n’est pas utilisé lorsque Visual Studio détecte si un projet utilise (ou est susceptible d’utiliser) extensions MEF.

Ces types de projets sont toujours entièrement chargés et ont des objets de CPS en mémoire, afin que toutes les extensions MEF sont créées pour eux :

- Projets de démarrage

- Les projets qui ont un upgrader projet personnalisé, autrement dit, elles définissent un `VCProjectUpgraderObjectName` propriété

- Les projets qui ne ciblent Windows Desktop, autrement dit, elles définissent un `ApplicationType` propriété

- Partagé des projets éléments (.vcxitems) et tous les projets qui font référence à l’importation des projets de .vcxitems.

Si aucune de ces conditions sont détectées, un cache de projet est créé. Le cache inclut toutes les données à partir du projet MSBuild nécessaires pour répondre aux `get` interroge sur `VCProjectEngine` interfaces. Cela signifie que toutes les modifications sur les propriétés MSBuild et au niveau des fichiers cibles effectué par une extension devrait fonctionner dans les projets chargés à partir du cache.

## <a name="shipping-your-extension"></a>Votre extension de livraison

Pour plus d’informations sur la création des fichiers VSIX, consultez [de livraison des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Pour plus d’informations sur la procédure pour ajouter des fichiers à des emplacements d’installation spécial, par exemple, pour ajouter des fichiers sous `$(VCTargetsPath)`, consultez [l’installation en dehors du dossier extensions](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Ressources supplémentaires

Le système de génération de Microsoft ([MSBuild](../msbuild/msbuild.md)) fournit le moteur de génération et le format XML extensible pour les fichiers de projet. Vous devez être familiarisé avec basic [concepts MSBuild](../msbuild/msbuild-concepts.md) et par la procédure [MSBuild pour Visual C++](/cpp/build/msbuild-visual-cpp-overview) système de projet works afin d’étendre le Visual C++.

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) fournit l’API qui sont utilisées par CPS et le système de projet Visual C++ de l’extension. Pour une vue d’ensemble de l’utilisation de MEF par CPS, consultez [CPS et MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) dans le [vue d’ensemble de VSProjectSystem de MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Vous pouvez personnaliser le système de génération existante pour ajouter des étapes de génération ou de nouveaux types de fichiers. Pour plus d’informations, consultez [vue d’ensemble de MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp-overview) et [utilisation des propriétés de projet](/cpp/ide/working-with-project-properties).
