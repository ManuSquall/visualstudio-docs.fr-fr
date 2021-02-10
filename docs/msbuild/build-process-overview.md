---
title: Comment MSBuild génère des projets
description: Découvrez comment MSBuild traite vos fichiers projet, s’ils sont appelés à partir de Visual Studio ou à partir d’une ligne de commande ou d’un script.
ms.custom: SEO-VS-2020
ms.date: 05/18/2020
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, build process overview
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8a7f8645cd34fe56d7d8d0f6a9efa6bf01bd13d8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939654"
---
# <a name="how-msbuild-builds-projects"></a>Comment MSBuild génère des projets

Comment MSBuild fonctionne-t-il réellement ? Dans cet article, vous découvrirez comment MSBuild traite vos fichiers projet, s’ils sont appelés à partir de Visual Studio, ou à partir d’une ligne de commande ou d’un script. La connaissance du fonctionnement de MSBuild peut vous aider à mieux diagnostiquer les problèmes et à mieux personnaliser votre processus de génération. Cet article décrit le processus de génération et s’applique en grande partie à tous les types de projets.

Le processus de génération complet se compose du [démarrage initial](#startup), de l' [évaluation](#evaluation-phase)et de l' [exécution](#execution-phase) des cibles et des tâches qui génèrent le projet. En plus de ces entrées, les importations externes définissent les détails du processus de génération, y compris les [importations standard](#standard-imports) , telles que *Microsoft. Common. targets* et les [importations configurables](#user-configurable-imports) par l’utilisateur au niveau de la solution ou du projet.

## <a name="startup"></a>Démarrage

MSBuild peut être appelé à partir de Visual Studio via le modèle objet MSBuild dans *Microsoft.Build.dll*, ou en appelant l’exécutable directement sur la ligne de commande, ou dans un script, tel que dans le système d’intégration continue (ci). Dans les deux cas, les entrées qui affectent le processus de génération incluent le fichier projet (ou l’objet de projet interne à Visual Studio), éventuellement un fichier solution, des variables d’environnement et des commutateurs de ligne de commande ou leurs équivalents de modèle objet. Au cours de la phase de démarrage, les options de ligne de commande ou les équivalents de modèle objet sont utilisés pour configurer des paramètres MSBuild tels que la configuration des journaux. Les propriétés définies sur la ligne de commande à l’aide du `-property` `-p` commutateur ou sont définies en tant que propriétés globales, qui remplacent toutes les valeurs qui seraient définies dans les fichiers projet, même si les fichiers projet sont lus plus tard.

Les sections suivantes concernent les fichiers d’entrée, tels que les fichiers solution ou les fichiers projet.

### <a name="solutions-and-projects"></a>Solutions et projets

Les instances MSBuild peuvent se composer d’un projet ou de plusieurs projets dans le cadre d’une solution. Le fichier solution n’est pas un fichier XML MSBuild, mais MSBuild l’interprète pour connaître tous les projets qui doivent être générés pour les paramètres de plateforme et de configuration donnés. Lorsque MSBuild traite cette entrée XML, il est désigné comme la génération de la solution. Il comporte des points extensibles qui vous permettent d’exécuter des éléments à chaque génération de solution, mais étant donné que cette Build est une exécution distincte des générations de projet individuelles, aucun paramètre de propriétés ou de définitions cibles de la génération de solution n’est pertinent pour chaque génération de projet.

Vous pouvez découvrir comment étendre la génération de la solution dans [personnaliser la génération de la solution](customize-your-build.md#customize-the-solution-build).

### <a name="visual-studio-builds-vs-msbuildexe-builds"></a>Visual Studio génère des builds vs. MSBuild.exe

Il existe des différences significatives entre le moment où les projets sont générés dans Visual Studio et le moment où vous appelez MSBuild directement, par le biais de l’exécutable MSBuild ou lorsque vous utilisez le modèle objet MSBuild pour démarrer une génération. Visual Studio gère l’ordre de génération du projet pour les builds Visual Studio. Il appelle MSBuild uniquement au niveau du projet individuel et, quand c’est le cas, quelques propriétés booléennes ( `BuildingInsideVisualStudio` , `BuildProjectReferences` ) sont définies et affectent de manière significative ce que MSBuild fait. Dans chaque projet, l’exécution se produit de la même manière que lorsqu’elle est appelée via MSBuild, mais la différence se pose avec les projets référencés. Dans MSBuild, lorsque des projets référencés sont requis, une build se produit réellement ; autrement dit, il exécute des tâches et des outils et génère la sortie. Quand une build Visual Studio trouve un projet référencé, MSBuild retourne uniquement les sorties attendues du projet référencé ; Il permet à Visual Studio de contrôler la génération de ces autres projets. Visual Studio détermine l’ordre de génération et les appels dans MSBuild séparément (si nécessaire), entièrement sous le contrôle de Visual Studio.

Une autre différence survient lorsque MSBuild est appelé avec un fichier solution, MSBuild analyse le fichier solution, crée un fichier d’entrée XML standard, l’évalue et l’exécute en tant que projet. La génération de la solution est exécutée avant tout projet. Lors de la génération à partir de Visual Studio, ce n’est pas le cas. MSBuild ne voit jamais le fichier solution. Par conséquent, la personnalisation de la build de la solution (à l’aide de *avant. SolutionName. sln. targets* et *after. NomSolution. sln. targets*) s’applique uniquement aux MSBuild.exe ou aux modèles d’objet, et non aux builds Visual Studio.

### <a name="project-sdks"></a>Kits SDK de projet

La fonctionnalité du kit de développement logiciel (SDK) pour les fichiers projet MSBuild est relativement nouvelle. Avant cette modification, les fichiers projet importaient explicitement les fichiers *. targets* et *. props* qui définissaient le processus de génération pour un type de projet particulier.

Les projets .NET Core importent la version du kit de développement logiciel (SDK) .NET qui leur convient. Consultez la vue d’ensemble, les [SDK de projet .net Core](/dotnet/core/project-sdk/overview)et la référence aux [Propriétés](/dotnet/core/project-sdk/msbuild-props).

## <a name="evaluation-phase"></a>Phase d’évaluation

Cette section explique comment ces fichiers d’entrée sont traités et analysés pour produire des objets en mémoire qui déterminent ce qui sera généré.

L’objectif de la phase d’évaluation est de créer les structures d’objets en mémoire en fonction des fichiers XML d’entrée et de l’environnement local. La phase d’évaluation est constituée de six passages qui traitent les fichiers d’entrée tels que les fichiers XML du projet ou, ainsi que les fichiers XML importés, généralement nommés en tant que fichiers *. props* ou *. targets* , selon qu’ils ont principalement défini des propriétés ou défini des cibles de génération. Chaque passe génère une partie des objets en mémoire qui sont ensuite utilisés dans la phase d’exécution pour générer les projets, mais aucune action de génération réelle n’a lieu pendant la phase d’évaluation. Au sein de chaque passe, les éléments sont traités dans l’ordre dans lequel ils apparaissent.

Les passes de la phase d’évaluation sont les suivantes :

- Évaluer les variables d’environnement
- Évaluer les importations et les propriétés
- Évaluer les définitions d’élément
- Évaluer les éléments
- Évaluer les éléments [UsingTask](usingtask-element-msbuild.md)
- Évaluer les cibles

L’ordre de ces passes a des implications significatives et il est important de savoir quand vous personnalisez le fichier projet. Consultez [ordre d’évaluation des propriétés et des éléments](comparing-properties-and-items.md#property-and-item-evaluation-order).

### <a name="evaluate-environment-variables"></a>Évaluer les variables d’environnement

Dans cette phase, les variables d’environnement sont utilisées pour définir des propriétés équivalentes. Par exemple, la variable d’environnement PATH est rendue disponible en tant que propriété `$(PATH)` . Lorsqu’il est exécuté à partir de la ligne de commande ou d’un script, l’environnement de commande est utilisé normalement et, lorsqu’il est exécuté à partir de Visual Studio, l’environnement de démarrage de Visual Studio est utilisé.

### <a name="evaluate-imports-and-properties"></a>Évaluer les importations et les propriétés

Au cours de cette phase, le code XML d’entrée est lu dans son intégralité, y compris les fichiers projet et la chaîne entière d’importations. MSBuild crée une structure XML en mémoire qui représente le XML du projet et tous les fichiers importés. À ce stade, les propriétés qui ne sont pas dans les cibles sont évaluées et définies.

À la suite de la lecture de tous les fichiers d’entrée XML tôt dans son processus, les modifications apportées à ces entrées pendant le processus de génération n’affectent pas la génération actuelle.

Les propriétés en dehors de toute cible sont gérées différemment des propriétés dans les cibles. Dans cette phase, seules les propriétés définies en dehors de la cible sont évaluées.

Étant donné que les propriétés sont traitées dans l’ordre dans la passe de propriétés, une propriété à n’importe quel endroit de l’entrée peut accéder aux valeurs de propriété qui s’affichent plus tôt dans l’entrée, mais pas aux propriétés qui s’affichent ultérieurement.

Étant donné que les propriétés sont traitées avant que les éléments ne soient évalués, vous ne pouvez pas accéder à la valeur d’un élément pendant une partie de la passe de propriétés. 

### <a name="evaluate-item-definitions"></a>Évaluer les définitions d’élément

Dans cette phase, les [définitions d’élément](item-definitions.md) sont interprétées et une représentation en mémoire de ces définitions est créée.

### <a name="evaluate-items"></a>Évaluer les éléments

Les éléments définis dans une cible sont gérés différemment des éléments en dehors des cibles. Dans cette phase, les éléments en dehors de toute cible et leurs métadonnées associées sont traités.  Les métadonnées définies par les définitions d’élément sont remplacées par les paramètres de métadonnées sur les éléments. Étant donné que les éléments sont traités dans l’ordre dans lequel ils apparaissent, vous pouvez référencer des éléments qui ont été définis précédemment, mais pas ceux qui s’affichent ultérieurement. Étant donné que les éléments sont transmis après les propriétés, les éléments peuvent accéder à n’importe quelle propriété si elle est définie en dehors des cibles, que la définition de la propriété apparaisse plus tard ou non.

### <a name="evaluate-usingtask-elements"></a>Évaluer les `UsingTask` éléments

Au cours de cette phase, les éléments [UsingTask](usingtask-element-msbuild.md) sont lus et les tâches sont déclarées pour une utilisation ultérieure pendant la phase d’exécution.

### <a name="evaluate-targets"></a>Évaluer les cibles

Dans cette phase, toutes les structures d’objets cibles sont créées en mémoire, en vue de leur exécution. Aucune exécution réelle n’a lieu. 

## <a name="execution-phase"></a>Phase d’exécution

Pendant la phase d’exécution, les cibles sont triées et exécutées, et toutes les tâches sont exécutées. Mais tout d’abord, les propriétés et les éléments qui sont définis dans des cibles sont évalués ensemble en une seule phase, dans l’ordre dans lequel ils apparaissent. L’ordre de traitement diffère notamment de la façon dont les propriétés et les éléments qui ne sont pas dans une cible sont traités : toutes les propriétés en premier, puis tous les éléments, dans des passes distinctes. Les modifications apportées aux propriétés et aux éléments d’une cible peuvent être observées après la cible où elles ont été modifiées.

### <a name="target-build-order"></a>Ordre de génération des cibles

Dans un projet unique, les cibles s’exécutent en série. Le problème central est de savoir comment déterminer l’ordre de génération de tous les éléments dans afin que les dépendances soient utilisées pour créer les cibles dans le bon ordre.  

L’ordre de génération de la cible est déterminé par l’utilisation des `BeforeTargets` `DependsOnTargets` attributs, et `AfterTargets` sur chaque cible. L’ordre des cibles ultérieures peut être influencé lors de l’exécution d’une cible antérieure si la cible antérieure modifie une propriété référencée dans ces attributs.

Les règles de classement sont décrites dans [déterminer l’ordre de génération de la cible](target-build-order.md#determine-the-target-build-order). Le processus est déterminé par une structure de pile contenant des cibles à générer. La cible en haut de cette tâche démarre l’exécution et, si elle dépend de n’importe quel autre, ces cibles sont poussées vers le haut de la pile, et elles commencent à s’exécuter.  Lorsqu’il existe une cible sans dépendances, elle s’exécute jusqu’à la fin et son cible parent reprend.

### <a name="project-references"></a>Références de projets

MSBuild peut prendre deux chemins de code, le mode normal, décrit ici et l’option Graph décrite dans la section suivante.

Les projets individuels spécifient leur dépendance vis-à-vis d’autres projets par le biais d' `ProjectReference` éléments. Lorsqu’un projet situé en haut de la pile commence à être généré, il atteint le point d’exécution de la `ResolveProjectReferences` cible, une cible standard définie dans les fichiers cibles communs.

`ResolveProjectReferences` appelle la tâche MSBuild avec les entrées des `ProjectReference` éléments pour récupérer les sorties. Les `ProjectReference` éléments sont transformés en éléments locaux tels que `Reference` . La phase d’exécution MSBuild pour le projet actuel est suspendue pendant que la phase d’exécution commence à traiter le projet référencé (la phase d’évaluation est effectuée en premier si nécessaire). Le projet référencé est généré uniquement une fois que vous avez commencé à générer le projet dépendant, ce qui crée une arborescence de projets en génération.

Visual Studio permet de créer des dépendances de projet dans des fichiers solution (. sln). Les dépendances sont spécifiées dans le fichier solution et sont uniquement respectées lors de la génération d’une solution ou lors de la génération dans Visual Studio. Si vous générez un seul projet, ce type de dépendance est ignoré. Les références de solution sont transformées par MSBuild en `ProjectReference` éléments et sont ensuite traitées de la même manière.

### <a name="graph-option"></a>Option Graph

Si vous spécifiez le commutateur de génération de graphique ( `-graphBuild` ou `-graph` ), le `ProjectReference` devient un concept de première classe utilisé par MSBuild. MSBuild analyse tous les projets et construit le graphique d’ordre de génération, un graphique de dépendance réel des projets, qui est ensuite parcouru pour déterminer l’ordre de génération. Comme avec les cibles dans des projets individuels, MSBuild s’assure que les projets référencés sont générés après les projets dont ils dépendent.

## <a name="parallel-execution"></a>Exécution parallèle

Si vous utilisez la prise en charge d’un multiprocesseur ( `-maxCpuCount` ou `-m` commutateur), MSBuild crée des nœuds, qui sont des processus MSBuild qui utilisent les cœurs de processeur disponibles. Chaque projet est soumis à un nœud disponible. Dans un nœud, les builds de projet individuelles s’exécutent en série.

Les tâches peuvent être activées pour une exécution parallèle en définissant une variable booléenne <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> , qui est définie en fonction de la valeur de la `$(BuildInParallel)` propriété dans MSBuild. Pour les tâches qui sont activées pour l’exécution en parallèle, un planificateur de tâches gère les nœuds et affecte le travail aux nœuds.

Consultez [génération de plusieurs projets en parallèle avec MSBuild](building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="standard-imports"></a>Importations standard

*Microsoft. Common. props* et *Microsoft. Common. targets* sont importés par les fichiers projet .net (explicitement ou implicitement dans les projets de style SDK) et se trouvent dans le dossier *MSBuild\Current\bin* dans une installation Visual Studio. Les projets C++ ont leur propre hiérarchie d’importations ; consultez [MSBuild Internals pour les projets C++](/cpp/build/reference/msbuild-visual-cpp-overview).

Le fichier *Microsoft. Common. props* définit les valeurs par défaut que vous pouvez remplacer. Il est importé (explicitement ou implicitement) au début d’un fichier projet. De cette façon, les paramètres de votre projet s’affichent après les valeurs par défaut, afin de les remplacer.

Le fichier *Microsoft. Common. targets* et les fichiers cibles qu’il importe définissent le processus de génération standard pour les projets .net. Il fournit également des points d’extension que vous pouvez utiliser pour personnaliser la Build.

Dans l’implémentation, *Microsoft. Common. targets* est un wrapper léger qui importe *Microsoft. Common. CurrentVersion. targets*. Ce fichier contient des paramètres pour les propriétés standard et définit les cibles réelles qui définissent le processus de génération. La `Build` cible est définie ici, mais elle est elle-même vide. Toutefois, la `Build` cible contient l' `DependsOn` attribut qui spécifie les cibles individuelles qui composent les étapes de génération réelles, qui sont `BeforeBuild` , `CoreBuild` et `AfterBuild` . La `Build` cible est définie comme suit :

```xml
  <PropertyGroup>
    <BuildDependsOn>
      BeforeBuild;
      CoreBuild;
      AfterBuild
    </BuildDependsOn>
  </PropertyGroup>

  <Target
      Name="Build"
      Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
      DependsOnTargets="$(BuildDependsOn)"
      Returns="@(TargetPathWithTargetPlatformMoniker)" />
```

`BeforeBuild` et `AfterBuild` sont des points d’extension. Elles sont vides dans le fichier *Microsoft. Common. CurrentVersion. targets* , mais les projets peuvent fournir leurs propres `BeforeBuild` et `AfterBuild` cibles avec des tâches qui doivent être effectuées avant ou après le processus de génération principal. `AfterBuild` est exécuté avant la cible de non-opération, `Build` , car `AfterBuild` apparaît dans l' `DependsOn` attribut sur la `Build` cible, mais il se produit après `CoreBuild` .

La `CoreBuild` cible contient les appels aux outils de génération, comme suit :

```xml
  <PropertyGroup>
    <CoreBuildDependsOn>
      BuildOnlySettings;
      PrepareForBuild;
      PreBuildEvent;
      ResolveReferences;
      PrepareResources;
      ResolveKeySource;
      Compile;
      ExportWindowsMDFile;
      UnmanagedUnregistration;
      GenerateSerializationAssemblies;
      CreateSatelliteAssemblies;
      GenerateManifests;
      GetTargetPath;
      PrepareForRun;
      UnmanagedRegistration;
      IncrementalClean;
      PostBuildEvent
    </CoreBuildDependsOn>
  </PropertyGroup>
  <Target
      Name="CoreBuild"
      DependsOnTargets="$(CoreBuildDependsOn)">

    <OnError ExecuteTargets="_TimeStampAfterCompile;PostBuildEvent" Condition="'$(RunPostBuildEvent)'=='Always' or '$(RunPostBuildEvent)'=='OnOutputUpdated'"/>
    <OnError ExecuteTargets="_CleanRecordFileWrites"/>

  </Target>
```

Le tableau suivant décrit ces cibles. certaines cibles s’appliquent uniquement à certains types de projets.

| Cible | Description |
|--------|-------------|
| BuildOnlySettings | Paramètres pour les générations réelles uniquement, et non pour lorsque MSBuild est appelé lors du chargement du projet par Visual Studio. |
| PrepareForBuild | Préparer les conditions préalables à la génération |
| PreBuildEvent | Point d’extension pour les projets afin de définir les tâches à exécuter avant la génération |
| ResolveProjectReferences | Analyser les dépendances du projet et générer des projets référencés |
| ResolveAssemblyReferences| Localisez les assemblys référencés. |
| ResolveReferences | Se compose de `ResolveProjectReferences` et `ResolveAssemblyReferences` de pour rechercher toutes les dépendances |
| PrepareResources | Traiter les fichiers de ressources |
| ResolveKeySource| Résolvez la clé de nom fort utilisée pour signer l’assembly et le certificat utilisé pour signer les manifestes [ClickOnce](../deployment/clickonce-security-and-deployment.md) . |
| Compiler | Appelle le compilateur |
| ExportWindowsMDFile | Générez un fichier [baWinMD](/uwp/winrt-cref/winmd-files) à partir des fichiers WinMDModule générés par le compilateur. |
| UnmanagedUnregistration | Supprimer/nettoyer les entrées de Registre [COM Interop](/dotnet/standard/native-interop/cominterop) d’une build précédente |
| GenerateSerializationAssemblies | Générez un assembly de sérialisation XML à l’aide de [sgen.exe](/dotnet/standard/serialization/xml-serializer-generator-tool-sgen-exe).|
| CreateSatelliteAssemblies | Créez un assembly satellite pour chaque culture unique dans les ressources. |
| Générer des manifestes | Génère des manifestes d’application et de déploiement [ClickOnce](../deployment/clickonce-security-and-deployment.md) ou un manifeste natif. |
| GetTargetPath | Retourne un élément contenant le produit de build (exécutable ou assembly) pour ce projet, avec les métadonnées. |
| PrepareForRun | Copiez les sorties de génération dans le répertoire final s’ils ont été modifiés. |
| UnmanagedRegistration | Définir des entrées de Registre pour [COM Interop](/dotnet/standard/native-interop/cominterop) |
| IncrementalClean | Supprimer les fichiers qui ont été produits dans une génération antérieure mais qui n’ont pas été produits dans la build actuelle. Cela est nécessaire pour effectuer le `Clean` travail dans les builds incrémentielles. |
| PostBuildEvent | Point d’extension pour les projets afin de définir les tâches à exécuter après la génération |

La plupart des cibles du tableau précédent se trouvent dans les importations spécifiques au langage, telles que *Microsoft. CSharp. targets*. Ce fichier définit les étapes du processus de génération standard spécifiques aux projets C# .NET. Par exemple, il contient la `Compile` cible qui appelle en fait le compilateur C#.

## <a name="user-configurable-imports"></a>Importations configurables par l’utilisateur

Outre les importations standard, vous pouvez ajouter plusieurs importations pour personnaliser le processus de génération.

- *Directory. Build. props*
- *Directory.Build.targets*

Ces fichiers sont lus par les importations standard pour tous les projets dans les sous-dossiers qu’ils contiennent. C’est généralement au niveau de la solution que les paramètres contrôlent tous les projets de la solution, mais peuvent également être plus hauts dans le système de fichiers, jusqu’à la racine du lecteur.

Le fichier *Directory. Build. props* est importé par *Microsoft. Common. props*, donc les propriétés définies dans celui-ci sont disponibles dans le fichier projet. Ils peuvent être redéfinis dans le fichier projet pour personnaliser les valeurs par projet. Le fichier *Directory. Build. targets* est lu après le fichier projet. Il contient généralement des cibles, mais ici vous pouvez également définir des propriétés que vous ne souhaitez pas redéfinir pour les projets individuels.

## <a name="customizations-in-a-project-file"></a>Personnalisations dans un fichier projet

Visual Studio met à jour vos fichiers projet à mesure que vous apportez des modifications dans **Explorateur de solutions**, la fenêtre **Propriétés** ou dans les **Propriétés du projet**, mais vous pouvez également apporter vos propres modifications en modifiant directement le fichier projet.

De nombreux comportements de génération peuvent être configurés en définissant les propriétés MSBuild, soit dans le fichier projet pour les paramètres locaux d’un projet, soit comme indiqué dans la section précédente, en créant un fichier *Directory. Build. props* pour définir les propriétés globalement pour les dossiers entiers des projets et solutions. Pour les builds ad hoc sur la ligne de commande, ou les scripts, vous pouvez également utiliser l' `/p` option sur la ligne de commande pour définir les propriétés d’un appel particulier de MSBuild. Pour plus d’informations sur les propriétés que vous pouvez définir, consultez [Propriétés de projet MSBuild courantes](common-msbuild-project-properties.md) .

## <a name="next-steps"></a>Étapes suivantes

Le processus MSBuild a plusieurs autres points d’extension autres que ceux décrits ici. Consultez [personnaliser votre Build](customize-your-build.md). et [comment étendre le processus de génération Visual Studio](how-to-extend-the-visual-studio-build-process.md).

## <a name="see-also"></a>Voir aussi

[MSBuild](msbuild.md)
