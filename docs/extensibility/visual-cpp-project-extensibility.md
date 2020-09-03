---
title: Extensibilité de projet Visual C++
ms.date: 04/23/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10869ad290b0b8df614d25d792d0b3ed1e88eb17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825567"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Extensibilité du système de projet Visual Studio C++ et intégration de l’ensemble d’outils

Le système de projet Visual C++ est utilisé pour les fichiers. vcxproj. Il est basé sur le [système de projet commun (CPS) de Visual Studio](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) et fournit des points d’extensibilité spécifiques à C++ pour faciliter l’intégration de nouveaux ensembles d’outils, des architectures de build et des plateformes cibles.

## <a name="c-msbuild-targets-structure"></a>Structure de cibles C++ MSBuild

Tous les fichiers. vcxproj importent ces fichiers :

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Ces fichiers définissent peu eux-mêmes. Au lieu de cela, ils importent d’autres fichiers en fonction de ces valeurs de propriété :

- `$(ApplicationType)`

   Exemples : Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Il doit s’agir d’une chaîne de version valide, de la forme major. minor [. Build [. Revision]].

   Exemples : 1,0, 10.0.0.0

- `$(Platform)`

   Architecture de la build, nommée « plateforme » pour des raisons historiques.

   Exemples : Win32, x86, x64, ARM

- `$(PlatformToolset)`

   Exemples : V140, V141, v141_xp, LLVM

Ces valeurs de propriété spécifient des noms de dossiers sous le `$(VCTargetsPath)` dossier racine :

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*Type d’application*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Plateformes*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` \
&nbsp;&nbsp;&nbsp;&nbsp;*Plateformes*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

Le `$(VCTargetsPath)` \\ dossier *plates-formes* \\ est utilisé lorsque `$(ApplicationType)` est vide pour les projets de bureau Windows.

### <a name="add-a-new-platform-toolset"></a>Ajouter un nouvel ensemble d’outils de plateforme

Pour ajouter un nouvel ensemble d’outils, par exemple « MyToolset » pour la plateforme Win32 existante, créez un dossier *MyToolset* sous `$(VCTargetsPath)` * \\ Platforms \\ Win32 \\ PlatformToolsets \\ *et créez des fichiers *Toolset. props* et *Toolset. targets* .

Chaque nom de dossier sous *PlatformToolsets* apparaît dans la boîte de dialogue **Propriétés du projet** comme un ensemble d’outils de **plateforme** disponible pour la plateforme spécifiée, comme illustré ici :

![Propriété de l’ensemble d’outils de plateforme dans la boîte de dialogue pages de propriétés du projet](media/vc-project-extensibility-platform-toolset-property.png "Propriété de l’ensemble d’outils de plateforme dans la boîte de dialogue pages de propriétés du projet")

Créez des dossiers *MyToolset* et des fichiers Toolset *. targets* similaires dans chaque dossier de plateforme existant que cet ensemble d’outils prend en charge. *Toolset.props*

### <a name="add-a-new-platform"></a>Ajouter une nouvelle plateforme

Pour ajouter une nouvelle plateforme, par exemple « myplatform », créez un dossier *myplatform* sous `$(VCTargetsPath)` * \\ plateformes \\ *et créez des fichiers Platform. *default. props*, *Platform. props*et *Platform. targets* . Créez également un `$(VCTargetsPath)` dossier * \\ plates-formes \\ *<strong><em>myplatform</em></strong>* \\ PlatformToolsets \\ * et créez au moins un ensemble d’outils.

Tous les noms de dossiers sous le dossier *plateformes* pour chacun d’eux `$(ApplicationType)` et `$(ApplicationTypeRevision)` apparaissent dans l’IDE en tant que choix de **plateforme** disponible pour un projet.

![Nouveau choix de plateforme dans la boîte de dialogue nouvelle plateforme de projet](media/vc-project-extensibility-new-project-platform.png "Nouveau choix de plateforme dans la boîte de dialogue nouvelle plateforme de projet")

### <a name="add-a-new-application-type"></a>Ajouter un nouveau type d’application

Pour ajouter un nouveau type d’application, créez un dossier *MyApplicationType* sous `$(VCTargetsPath)` * \\ type \\ d’application* et créez-y un fichier *par défaut. props* . Au moins une révision est requise pour un type d’application. vous devez donc également créer un dossier de `$(VCTargetsPath)` * \\ type d’application \\ MyApplicationType \\ 1,0* et y créer un fichier *par défaut. props* . Vous devez également créer un `$(VCTargetsPath)` dossier * \\ ApplicationType \\ MyApplicationType \\ 1,0 \\ Platforms* et y créer au moins une plateforme.

`$(ApplicationType)``$(ApplicationTypeRevision)`les propriétés et ne sont pas visibles dans l’interface utilisateur. Ils sont définis dans les modèles de projet et ne peuvent pas être modifiés une fois le projet créé.

## <a name="the-vcxproj-import-tree"></a>Arborescence d’importation. vcxproj

Une arborescence simplifiée d’importations pour les fichiers de cibles et de propriétés de Microsoft C++ ressemble à ceci :

> `$(VCTargetsPath)`\\*Microsoft. cpp. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Les* \\ *Valeur par défaut* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Application Type* \\ Type `$(ApplicationType)` d' \\ application *Valeurs par défaut. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Application Type* \\ Type `$(ApplicationType)` \\ d' `$(ApplicationTypeRevision)` application \\ *Valeurs par défaut. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Application Type* \\ Type `$(ApplicationType)` \\ d' `$(ApplicationTypeRevision)` application \\ *Platforms* \\ `$(Platform)` Plateformes \\ *Plateforme. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Valeur par défaut* \\ \* . *props*

Les projets de bureau Windows ne sont pas définis `$(ApplicationType)` et ne peuvent donc être importés

> `$(VCTargetsPath)`\\*Microsoft. cpp. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Les* \\ *Valeur par défaut* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Platforms* \\ `$(Platform)` Plateformes \\ *Plateforme. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Valeur par défaut* \\ \* . *props*

Nous allons utiliser la `$(_PlatformFolder)` propriété pour stocker les `$(Platform)` emplacements de dossier de plateforme. Cette propriété est

> `$(VCTargetsPath)`\\*Plateformes*\\`$(Platform)`

pour les applications de bureau Windows et

> `$(VCTargetsPath)`\\*Application Type* \\ Type `$(ApplicationType)` \\ d' `$(ApplicationTypeRevision)` application \\ *Plateformes*\\`$(Platform)`

pour tout le reste.

Les fichiers props sont importés dans cet ordre :

> `$(VCTargetsPath)`\\*Microsoft. cpp. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Plateforme. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Les* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets* \\ `$(PlatformToolset)` PlatformToolsets \\ *Ensemble d’outils. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *props*

Les fichiers cibles sont importés dans cet ordre :

> `$(VCTargetsPath)`\\*Microsoft. cpp. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Current. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Les* \\ \* . *cibles* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets* \\ `$(PlatformToolset)` PlatformToolsets \\ *Ensemble d’outils. Target* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *cibles*

Si vous devez définir des propriétés par défaut pour votre ensemble d’outils, vous pouvez ajouter des fichiers aux dossiers les et ImportAfter appropriés.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Créer des fichiers d’ensemble d’outils. props et d’ensemble d’outils. targets

Les fichiers *Toolset. props* et *Toolset. targets* ont un contrôle total sur ce qui se passe lors d’une génération lorsque cet ensemble d’outils est utilisé. Ils peuvent également contrôler les débogueurs disponibles, une partie de l’interface utilisateur de l’IDE, telle que le contenu de la boîte de dialogue **pages de propriétés** , ainsi que d’autres aspects du comportement du projet.

Bien qu’un ensemble d’outils puisse remplacer l’ensemble du processus de génération, vous souhaitez généralement que votre ensemble d’outils puisse modifier ou ajouter des étapes de génération, ou utiliser des outils de génération différents dans le cadre d’un processus de génération existant. Pour atteindre cet objectif, il existe un certain nombre de fichiers de propriétés et de cibles communs que votre ensemble d’outils peut importer. Selon ce que vous souhaitez faire de votre ensemble d’outils, ces fichiers peuvent être utiles pour l’utilisation de en tant qu’importations ou comme exemples :

- `$(VCTargetsPath)`\\*Microsoft. CppCommon. targets*

  Ce fichier définit les principales parties du processus de génération natif et importe également les éléments suivants :

  - `$(VCTargetsPath)`\\*Microsoft. CppBuild. targets*

  - `$(VCTargetsPath)`\\*Microsoft. BuildSteps. targets*

  - `$(MSBuildToolsPath)`\\*Microsoft. Common. targets*

- `$(VCTargetsPath)`\\*Microsoft. cpp. Common. props*

   Définit les valeurs par défaut pour les ensembles d’outils qui utilisent les compilateurs Microsoft et les fenêtres cibles.

- `$(VCTargetsPath)`\\*Microsoft. cpp. WindowsSDK. props*

   Ce fichier détermine l’emplacement du SDK Windows et définit des propriétés importantes pour les applications ciblant Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Intégrer des cibles spécifiques à un ensemble d’outils avec le processus de génération C++ par défaut

Le processus de génération C++ par défaut est défini dans *Microsoft. CppCommon. targets*. Les cibles n’appellent pas d’outils de génération spécifiques ; ils spécifient les étapes de build principales, leur ordre et leurs dépendances.

La version C++ comporte trois étapes principales, qui sont représentées par les cibles suivantes :

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Étant donné que chaque étape de génération peut être exécutée indépendamment, les cibles qui s’exécutent en une seule étape ne peuvent pas reposer sur les groupes d’éléments et les propriétés définis dans les cibles qui s’exécutent dans le cadre d’une autre étape. Cette division autorise certaines optimisations des performances de la génération. Bien qu’il ne soit pas utilisé par défaut, vous êtes toujours encouragé à respecter cette séparation.

Les cibles qui sont exécutées à l’intérieur de chaque étape sont contrôlées par les propriétés suivantes :

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Chaque étape a également les propriétés Before et after.

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

Pour obtenir des exemples des cibles incluses dans chaque étape, consultez le fichier *Microsoft. CppBuild. targets* :

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Si vous examinez les cibles, telles que `_ClCompile` , vous verrez qu’elles ne font rien d’autre directement, mais dépendent plutôt d’autres cibles, notamment `ClCompile` :

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` et d’autres cibles spécifiques à l’outil de génération sont définies en tant que cibles vides dans *Microsoft. CppBuild. targets*:

```xml
<Target Name="ClCompile"/>
```

Étant donné que la `ClCompile` cible est vide, sauf si elle est remplacée par un ensemble d’outils, aucune action de génération réelle n’est effectuée. Les cibles de l’ensemble d’outils peuvent remplacer la `ClCompile` cible, autrement dit, elles peuvent contenir une autre `ClCompile` définition après l’importation de *Microsoft. CppBuild. targets*:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

En dépit de son nom, qui a été créé avant l’implémentation de la prise en charge multiplateforme de Visual Studio, la `ClCompile` cible n’a pas besoin d’appeler CL.exe. Il peut également appeler Clang, GCC ou d’autres compilateurs à l’aide des tâches MSBuild appropriées.

La `ClCompile` cible ne doit pas avoir de dépendances à l’exception de la `SelectClCompile` cible, ce qui est nécessaire pour que la commande de compilation de fichier unique fonctionne dans l’IDE.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Tâches MSBuild à utiliser dans les cibles d’ensemble d’outils

Pour appeler un outil de génération réel, la cible doit appeler une tâche MSBuild. Une [tâche exec](../msbuild/exec-task.md) de base vous permet de spécifier une ligne de commande à exécuter. Toutefois, les outils de génération ont généralement de nombreuses options, entrées. et les sorties sont suivies pour les builds incrémentielles. il est donc plus judicieux d’avoir des tâches spéciales pour eux. Par exemple, la `CL` tâche traduit les propriétés MSBuild en commutateurs CL.exe, les écrit dans un fichier réponse et appelle CL.exe. Il effectue également le suivi de tous les fichiers d’entrée et de sortie pour les builds incrémentielles ultérieures. Pour plus d’informations, consultez [Builds incrémentielles et contrôles à jour](#incremental-builds-and-up-to-date-checks).

Le Microsoft.Cpp.Common.Tasks.dll implémente les tâches suivantes :

- `BSCMake`

- `CL`

- `ClangCompile` (commutateurs Clang-GCC)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (par exemple, exec mais avec suivi d’entrée et de sortie)

- `SetEnv`

- `GetOutOfDateItems`

Si vous avez un outil qui effectue la même action qu’un outil existant et qui possède des commutateurs de ligne de commande similaires (comme Clang-CL et CL), vous pouvez utiliser la même tâche pour les deux.

Si vous avez besoin de créer une nouvelle tâche pour un outil de génération, vous pouvez choisir parmi les options suivantes :

1. Si vous utilisez cette tâche rarement ou si quelques secondes n’ont pas d’importance pour votre Build, vous pouvez utiliser les tâches « inline » de MSBuild :

   - Tâche XAML (règle de génération personnalisée)

     Pour obtenir un exemple de déclaration de tâche XAML, consultez `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml*et pour son utilisation, consultez `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *MASM. targets*.

   - [Tâche de code](../msbuild/msbuild-inline-tasks.md)

1. Si vous souhaitez améliorer les performances des tâches ou si vous avez simplement besoin de fonctionnalités plus complexes, utilisez le processus d' [écriture de tâches](../msbuild/task-writing.md) MSBuild normal.

   Si les entrées et les sorties de l’outil ne sont pas toutes répertoriées sur la ligne de commande de l’outil, comme dans les `CL` cas, et `MIDL` `RC` , et si vous souhaitez le suivi automatique des fichiers d’entrée et de sortie et la création de fichiers. TLog, dérivez votre tâche de la `Microsoft.Build.CPPTasks.TrackedVCToolTask` classe. À l’heure actuelle, bien qu’il existe une documentation pour la classe de base [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) , il n’existe aucun exemple ni aucune documentation pour les détails de la `TrackedVCToolTask` classe. S’il s’agit d’un intérêt particulier, ajoutez votre voix à une demande sur [developercommunity.VisualStudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="incremental-builds-and-up-to-date-checks"></a>Builds incrémentielles et vérifications à jour

La build incrémentielle MSBuild par défaut cible les `Inputs` `Outputs` attributs et. Si vous les spécifiez, MSBuild appelle la cible uniquement si l’une des entrées a un horodateur plus récent que toutes les sorties. Étant donné que les fichiers sources incluent ou importent souvent d’autres fichiers et que les outils de génération produisent des sorties différentes selon les options de l’outil, il est difficile de spécifier toutes les entrées et sorties possibles dans les cibles MSBuild.

Pour gérer ce problème, la génération C++ utilise une technique différente pour prendre en charge les builds incrémentielles. La plupart des cibles ne spécifient pas d’entrées et de sorties et, par conséquent, s’exécutent toujours pendant la génération. Les tâches appelées par les cibles écrivent des informations sur toutes les entrées et sorties dans les fichiers *TLog* qui ont une extension. TLog. Les fichiers. TLog sont utilisés par les builds ultérieures pour vérifier ce qui a changé et doivent être reconstruits, et ce qui est à jour. Les fichiers. TLog sont également la seule source pour la mise à jour de la build par défaut dans l’IDE.

Pour déterminer toutes les entrées et sorties, les tâches d’outil natives utilisent tracker.exe et la classe [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) fournie par MSBuild.

Microsoft.Build.CPPTasks.Common.dll définit la `TrackedVCToolTask` classe de base abstraite publique. La plupart des tâches d’outils natives sont dérivées de cette classe.

À compter de Visual Studio 2017 Update 15,8, vous pouvez utiliser la `GetOutOfDateItems` tâche implémentée dans Microsoft.Cpp.Common.Tasks.dll pour produire des fichiers. TLog pour des cibles personnalisées avec des entrées et des sorties connues.
Vous pouvez également les créer à l’aide de la `WriteLinesToFile` tâche. Consultez la `_WriteMasmTlogs` cible dans `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *MASM. targets* à titre d’exemple.

## <a name="tlog-files"></a>fichiers. TLog

Il existe trois types de fichiers. TLog : *lecture*, *écriture*et *ligne de commande*. Les fichiers Read et Write. TLog sont utilisés par les builds incrémentielles et par la vérification à jour dans l’IDE. Les fichiers de ligne de commande. TLog sont utilisés uniquement dans les builds incrémentielles.

MSBuild fournit ces classes d’assistance pour lire et écrire des fichiers. TLog :

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

La classe [FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) peut être utilisée pour accéder à la fois aux fichiers Read et Write. TLog et identifier les entrées qui sont plus récentes que les sorties, ou si une sortie est manquante. Elle est utilisée dans le contrôle à jour.

Les fichiers de ligne de commande. TLog contiennent des informations sur les lignes de commande utilisées dans la Build. Elles sont uniquement utilisées pour les builds incrémentielles, pas pour les contrôles à jour. par conséquent, le format interne est déterminé par la tâche MSBuild qui les produit.

### <a name="read-tlog-format"></a>Format de lecture. TLog

*Lire* les fichiers. TLog ( \* . Read. \* . TLog) contient des informations sur les fichiers sources et leurs dépendances.

Un signe insertion ( **^** ) au début d’une ligne indique une ou plusieurs sources. Les sources qui partagent les mêmes dépendances sont séparées par une barre verticale ( **\|** ).

Les fichiers de dépendances sont répertoriés après les sources, chacun sur sa propre ligne. Tous les noms de fichiers sont des chemins d’accès complets.

Par exemple, supposons que les sources de votre projet se trouvent dans *F : \\ test \\ ConsoleApplication1 \\ ConsoleApplication1*. Si votre fichier source, *Class1. cpp*, contient ces fichiers include,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

Ensuite, le fichier *CL. Read. 1. TLog* contient le fichier source suivi de ses deux dépendances :

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Il n’est pas nécessaire d’écrire des noms de fichiers en majuscules, mais cela est pratique pour certains outils.

### <a name="write-tlog-format"></a>Format Write. TLog

*Écrire* . TLog ( \* . Write. \* . les fichiers TLog) connectent les sources et les sorties.

Un signe insertion ( **^** ) au début d’une ligne indique une ou plusieurs sources. Plusieurs sources sont séparées par une barre verticale ( **\|** ).

Les fichiers de sortie générés à partir des sources doivent être listés après les sources, chacun sur sa propre ligne. Tous les noms de fichiers doivent être des chemins d’accès complets.

Par exemple, pour un projet ConsoleApplication simple qui a un fichier source supplémentaire *Class1. cpp*, le fichier *Link. Write. 1. TLog* peut contenir :

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Build au moment du design

Dans l’IDE, les projets. vcxproj utilisent un ensemble de cibles MSBuild pour obtenir des informations supplémentaires à partir du projet et pour régénérer des fichiers de sortie. Certaines de ces cibles sont uniquement utilisées dans les builds au moment du design, mais beaucoup d’entre elles sont utilisées dans les builds standard et les builds au moment du Design.

Pour obtenir des informations générales sur les builds au moment du design, consultez la documentation CPS pour les [Builds au moment du design](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Cette documentation n’est applicable qu’en partie aux projets Visual C++.

Les `CompileDesignTime` `Compile` cibles et mentionnées dans la documentation sur les builds au moment du design ne sont jamais exécutées pour les projets. vcxproj. Les projets Visual C++. vcxproj utilisent différentes cibles au moment du design pour accéder aux informations IntelliSense.

### <a name="design-time-targets-for-intellisense-information"></a>Cibles au moment du design pour les informations IntelliSense

Les cibles au moment du design utilisées dans les projets. vcxproj sont définies dans `$(VCTargetsPath)` \\ *Microsoft. cpp. designtime. targets*.

La `GetClCommandLines` cible collecte les options du compilateur pour IntelliSense :

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` : cibles au moment de la conception uniquement, requises pour l’initialisation de la build au moment du Design. Entre autres choses, ces cibles désactivent certaines fonctionnalités de génération standard pour améliorer les performances.

- `ComputeCompileInputsTargets` : ensemble de cibles qui modifie les options et les éléments du compilateur. Ces cibles s’exécutent à la fois au moment du design et dans les builds normales.

La cible appelle la `CLCommandLine` tâche pour créer la ligne de commande à utiliser pour IntelliSense. Là encore, en dépit de son nom, il peut gérer non seulement les options CL, mais également les options Clang et GCC. Le type des commutateurs du compilateur est contrôlé par la `ClangMode` propriété.

Actuellement, la ligne de commande produite par la `CLCommandLine` tâche utilise toujours des commutateurs CL (même en mode Clang), car elles sont plus faciles à analyser par le moteur IntelliSense.

Si vous ajoutez une cible qui s’exécute avant la compilation, qu’elle soit normale ou au moment du design, assurez-vous qu’elle n’interrompt pas les builds au moment du design ou n’affecte pas les performances. Le moyen le plus simple de tester votre cible consiste à ouvrir une invite de commandes développeur et à exécuter cette commande :

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

Cette commande produit un journal de génération détaillé, *MSBuild. log*, qui présente un récapitulatif des performances pour les cibles et les tâches à la fin.

Veillez à utiliser `Condition ="'$(DesignTimeBuild)' != 'true'"` dans toutes les opérations qui n’ont de sens que pour les builds normales et non pour les builds au moment du Design.

### <a name="design-time-targets-that-generate-sources"></a>Cibles au moment du design qui génèrent des sources

*Cette fonctionnalité est désactivée par défaut pour les projets bureautiques natifs et n’est actuellement pas prise en charge sur les projets mis en cache*.

Si `GeneratorTarget` des métadonnées sont définies pour un élément de projet, la cible est exécutée automatiquement lorsque le projet est chargé et lorsque le fichier source est modifié.

::: moniker range="vs-2017"

Par exemple, pour générer automatiquement des fichiers. cpp ou. h à partir de fichiers. xaml, les `$(VSInstallDir)` \\ fichiers *MSBuild* \\ *Microsoft* \\ *WindowsXaml* \\ *v 15* \\ \* \\ *Microsoft. Windows. UI. Xaml. cpp. targets* définissent ces entités :

::: moniker-end

::: moniker range=">=vs-2019"

Par exemple, pour générer automatiquement des fichiers. cpp ou. h à partir de fichiers. xaml, les `$(VSInstallDir)` \\ fichiers *MSBuild* \\ *Microsoft* \\ *WindowsXaml* \\ *v 16*et \\ \* \\ *Microsoft. Windows. UI. Xaml. cpp. targets* définissent ces entités :

::: moniker-end

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

Pour utiliser `Task.HostObject` pour obtenir le contenu non enregistré des fichiers sources, les cibles et la tâche doivent être inscrites en tant que [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) pour les projets donnés dans un pkgdef :

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual C++ l’extensibilité de projet dans l’IDE de Visual Studio

Le système de projet Visual C++ est basé sur le [système de projet vs](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)et utilise ses points d’extensibilité. Toutefois, l’implémentation de la hiérarchie de projet est spécifique à Visual C++ et non basée sur CPS. l’extensibilité de la hiérarchie est donc limitée aux éléments de projet.

### <a name="project-property-pages"></a>Pages de propriétés du projet

Pour obtenir des informations générales sur la conception, consultez [multi-ciblage de l’infrastructure pour les projets VC + +](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/).

En termes simples, les pages de propriétés que vous voyez dans la boîte de dialogue **Propriétés du projet** pour un projet C++ sont définies par les fichiers de *règles* . Un fichier de règles spécifie un ensemble de propriétés à afficher dans une page de propriétés, ainsi que le mode et l’emplacement où ils doivent être enregistrés dans le fichier projet. Les fichiers de règles sont des fichiers. XML qui utilisent le format XAML. Les types utilisés pour les sérialiser sont décrits dans [Microsoft. Build. Framework. XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Pour plus d’informations sur l’utilisation des fichiers de règles dans les projets, consultez [fichiers de règles XML](/cpp/build/reference/property-page-xml-files)de la page de propriétés.

Les fichiers de règles doivent être ajoutés au `PropertyPageSchema` groupe d’éléments :

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` les métadonnées limitent la visibilité de la règle, qui est également contrôlée par le type de règle, et peut avoir l’une des valeurs suivantes :

`Project` | `File` | `PropertySheet`

CPS prend en charge d’autres valeurs pour le type de contexte, mais elles ne sont pas utilisées dans les projets Visual C++.

Si la règle doit être visible dans plusieurs contextes, utilisez des points-virgules (**;**) pour séparer les valeurs de contexte, comme illustré ici :

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Format de règle et types principaux

Le format de la règle étant simple, cette section décrit uniquement les attributs qui affectent l’aspect de la règle dans l’interface utilisateur.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

L' `PageTemplate` attribut définit le mode d’affichage de la règle dans la boîte de dialogue **pages de propriétés** . L’attribut peut avoir l’une des valeurs suivantes :

| Attribut | Description |
|------------| - |
| `generic` | Toutes les propriétés sont affichées sur une page sous les en-têtes de catégorie<br/>La règle peut être visible pour `Project` les `PropertySheet` contextes et, mais pas pour les contextes `File` .<br/><br/> Exemple : `$(VCTargetsPath)` \\ *1033* \\ *general.xml* |
| `tool` | Les catégories s’affichent sous la forme de sous-pages.<br/>La règle peut être visible dans tous les contextes `Project` : `PropertySheet` et `File` .<br/>La règle est visible dans les propriétés du projet uniquement si le projet a des éléments avec le `ItemType` défini dans `Rule.DataSource` , à moins que le nom de la règle ne soit inclus dans le `ProjectTools` groupe d’éléments.<br/><br/>Exemple : `$(VCTargetsPath)` \\ *1033* \\ *clang.xml* |
| `debugger` | La page est affichée dans la page de débogage.<br/>Les catégories sont actuellement ignorées.<br/>Le nom de la règle doit correspondre à l’attribut de l’objet MEF du lanceur de débogage `ExportDebugger` .<br/><br/>Exemple : `$(VCTargetsPath)` \\ *1033* \\ * \_ \_windows.xmllocal du débogueur* |
| *propre* | Modèle personnalisé. Le nom du modèle doit correspondre à l' `ExportPropertyPageUIFactoryProvider` attribut de l' `PropertyPageUIFactoryProvider` objet MEF. Consultez **Microsoft. VisualStudio. ProjectSystem. designers. Properties. IPropertyPageUIFactoryProvider**.<br/><br/> Exemple : `$(VCTargetsPath)` \\ *1033* \\ *userMacros.xml* |

Si la règle utilise l’un des modèles basés sur la grille des propriétés, elle peut utiliser ces points d’extensibilité pour ses propriétés :

- [Éditeurs de valeurs de propriété](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Fournisseur de valeurs enum dynamiques](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Étendre une règle

Si vous souhaitez utiliser une règle existante, mais que vous devez ajouter ou supprimer (autrement dit, Masquer) quelques propriétés, vous pouvez créer une règle d' [extension](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Remplacer une règle

Peut-être souhaitez-vous que votre ensemble d’outils utilise la plupart des règles par défaut du projet, mais ne les remplace qu’une seule ou plusieurs d’entre elles. Par exemple, imaginons que vous souhaitez uniquement modifier la règle C/C++ pour afficher des commutateurs de compilateur différents. Vous pouvez fournir une nouvelle règle portant le même nom et le même nom d’affichage que la règle existante, et l’inclure dans le `PropertyPageSchema` groupe d’éléments après l’importation des cibles CPP par défaut. Une seule règle avec un nom donné est utilisée dans le projet, et la dernière incluse dans le `PropertyPageSchema` groupe d’éléments gagne.

#### <a name="project-items"></a>Éléments de projet

Le fichier *ProjectItemsSchema.xml* définit les `ContentType` `ItemType` valeurs et pour les éléments qui sont traités comme des éléments de projet, et définit des `FileExtension` éléments pour déterminer le groupe d’éléments auquel un nouveau fichier est ajouté.

Le fichier ProjectItemsSchema par défaut se trouve dans `$(VCTargetsPath)` \\ *1033* \\ *ProjectItemsSchema.xml*. Pour l’étendre, vous devez créer un fichier de schéma avec un nouveau nom, tel que *MyProjectItemsSchema.xml*:

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

Exemple : `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml*

### <a name="debuggers"></a>Débogueurs

Le service de débogage de Visual Studio prend en charge l’extensibilité pour le moteur de débogage. Pour plus d’informations, consultez les exemples suivants :

- [MIEngine, projet open source prenant en charge le débogage lldb](https://github.com/Microsoft/MIEngine)

- [Exemple de moteur de débogage Visual Studio](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Pour spécifier les moteurs de débogage et d’autres propriétés de la session de débogage, vous devez implémenter un composant MEF du [lanceur de débogage](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) et ajouter une `debugger` règle. Pour obtenir un exemple, consultez le `$(VCTargetsPath)` \\ \\ \_ fichierwindows.xml local du débogueur 1033 \_ .

### <a name="deploy"></a>Déployer

les projets. vcxproj utilisent l’extensibilité du système de projet Visual Studio pour [déployer des fournisseurs](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Build à jour

Par défaut, le contrôle à jour de la build requiert la création de fichiers Read. TLog et Write. TLog dans le `$(TlogLocation)` dossier pendant la génération pour toutes les entrées et sorties de génération.

Pour utiliser un contrôle de mise à jour personnalisé :

1. Désactivez la vérification de mise à jour par défaut en ajoutant la `NoVCDefaultBuildUpToDateCheckProvider` fonctionnalité dans le fichier *Toolset. targets* :

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Implémentez votre propre [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Mise à niveau du projet

### <a name="default-vcxproj-project-upgrader"></a>Mise à niveau du projet default. vcxproj

Le projet de mise à niveau par défaut. vcxproj modifie la version de l' `PlatformToolset` `ApplicationTypeRevision` ensemble d’outils MSBuild et le .NET Framework. Les deux dernières sont toujours remplacées par les valeurs par défaut de la version de Visual Studio, mais `PlatformToolset` et `ApplicationTypeRevision` peuvent être contrôlées par des propriétés MSBuild spéciales.

La mise à niveau utilise ces critères pour décider si un projet peut être mis à niveau ou non :

1. Pour les projets qui définissent `ApplicationType` et `ApplicationTypeRevision` , il existe un dossier avec un numéro de révision plus élevé que celui en cours.

1. La propriété `_UpgradePlatformToolsetFor_<safe_toolset_name>` est définie pour l’ensemble d’outils actuel et sa valeur n’est pas égale à l’ensemble d’outils actuel.

   Dans ces noms de propriétés, *\<safe_toolset_name>* représente le nom de l’ensemble d’outils avec tous les caractères non alphanumériques remplacés par un trait de soulignement ( **\_** ).

Lorsqu’un projet peut être mis à niveau, il participe au *reciblage*de la solution. Pour plus d’informations, consultez [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Si vous souhaitez orner les noms de projet dans **Explorateur de solutions** lorsque les projets utilisent un ensemble d’outils spécifique, définissez une `_PlatformToolsetShortNameFor_<safe_toolset_name>` propriété.

Pour obtenir des exemples de `_UpgradePlatformToolsetFor_<safe_toolset_name>` `_PlatformToolsetShortNameFor_<safe_toolset_name>` définitions de propriétés et, consultez le fichier *Microsoft. cpp. default. props* . Pour obtenir des exemples d’utilisation, consultez le `$(VCTargetPath)` \\ fichier *Microsoft. cpp. Platform. targets* .

### <a name="custom-project-upgrader"></a>Mise à niveau de projet personnalisée

Pour utiliser un objet de mise à niveau de projet personnalisé, implémentez un composant MEF, comme illustré ici :

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

Votre code peut importer et appeler l’objet de mise à niveau par défaut. vcxproj :

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` est défini dans *Microsoft.VisualStudio.ProjectSystem.VS.dll* et est semblable à `IVsRetargetProjectAsync` .

Définissez la `VCProjectUpgraderObjectName` propriété pour indiquer au système de projet d’utiliser votre objet de mise à niveau personnalisée :

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Désactiver la mise à niveau du projet

Pour désactiver les mises à niveau de projet, utilisez une `NoUpgrade` valeur :

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Cache de projet et extensibilité

Pour améliorer les performances lors de l’utilisation de solutions C++ de grande taille dans Visual Studio 2017, le [cache du projet](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) a été introduit. Elle est implémentée en tant que base de données SQLite remplie avec les données de projet, puis utilisée pour charger des projets sans charger les projets MSBuild ou CPS en mémoire.

Étant donné qu’aucun objet CPS n’est présent pour les projets. vcxproj chargés à partir du cache, les composants MEF de l’extension qui importent `UnconfiguredProject` ou `ConfiguredProject` ne peuvent pas être créés. Pour prendre en charge l’extensibilité, le cache de projet n’est pas utilisé lorsque Visual Studio détecte si un projet utilise (ou est susceptible d’utiliser) des extensions MEF.

Ces types de projets étant toujours entièrement chargés et disposant d’objets CPS en mémoire, toutes les extensions MEF sont créées pour eux :

- Projets de démarrage

- Projets qui ont un projet de mise à niveau de projet personnalisé, autrement dit, ils définissent une `VCProjectUpgraderObjectName` propriété

- Projets qui ne ciblent pas les fenêtres de bureau, autrement dit, ils définissent une `ApplicationType` propriété

- Projets d’éléments partagés (. vcxitems) et tous les projets qui les référencent par importation de projets. vcxitems.

Si aucune de ces conditions n’est détectée, un cache de projet est créé. Le cache comprend toutes les données du projet MSBuild requis pour répondre aux `get` requêtes sur les `VCProjectEngine` interfaces. Cela signifie que toutes les modifications apportées au niveau de fichier des propriétés et cibles MSBuild effectuées par une extension doivent simplement fonctionner dans des projets chargés à partir du cache.

## <a name="shipping-your-extension"></a>Expédition de votre extension

Pour plus d’informations sur la création de fichiers VSIX, consultez la page [expédition d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Pour plus d’informations sur la façon d’ajouter des fichiers à des emplacements d’installation spéciaux, par exemple pour ajouter des fichiers sous `$(VCTargetsPath)` , consultez [installation en dehors du dossier Extensions](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Ressources supplémentaires

Le système de génération Microsoft ([MSBuild](../msbuild/msbuild.md)) fournit le moteur de génération et le format extensible XML pour les fichiers projet. Vous devez être familiarisé avec les [concepts](../msbuild/msbuild-concepts.md) de base de MSBuild et avec la façon dont [MSBuild pour Visual C++](/cpp/build/reference/msbuild-visual-cpp-overview) fonctionne afin d’étendre le système de projet Visual C++.

Le Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) fournit les API d’extension utilisées par CPS et le système de projet Visual C++. Pour obtenir une vue d’ensemble de l’utilisation de MEF par CPS, consultez [CPS et MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) dans [VSPROJECTSYSTEM Overview of MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Vous pouvez personnaliser le système de génération existant pour ajouter des étapes de génération ou de nouveaux types de fichiers. Pour plus d’informations, consultez [vue d’ensemble de MSBuild (Visual C++)](/cpp/build/reference/msbuild-visual-cpp-overview) et [utilisation des propriétés de projet](/cpp/build/working-with-project-properties).
