---
title: Intégration de Visual Studio (MSBuild)
titleSuffix: ''
description: Découvrez comment Visual Studio peut héberger des projets au format MSBuild, même s’ils ont été créés par différents outils et ont des processus de génération personnalisés.
ms.custom: seodec18, SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 63e78d935d515ccafda461a8f7af77623387940b
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602148"
---
# <a name="visual-studio-integration-msbuild"></a>Intégration de Visual Studio (MSBuild)

Visual Studio héberge MSBuild pour charger et générer des projets managés. Étant donné que MSBuild est responsable du projet, presque tous les projets au format MSBuild peuvent être utilisés avec succès dans Visual Studio, même si le projet a été créé par un outil différent et possède un processus de génération personnalisé.

 Cet article décrit des aspects spécifiques de l’hébergement MSBuild de Visual Studio qui doivent être pris en compte lors de la personnalisation des projets et des fichiers *. targets* que vous souhaitez charger et générer dans Visual Studio. Celles-ci vous aideront à vérifier que les fonctionnalités de Visual Studio comme IntelliSense et le débogage fonctionnent pour votre projet personnalisé.

 Pour plus d’informations sur les projets C++, consultez [fichiers projet](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Extensions de nom de fichier projet

 *MSBuild.exe* reconnaît toute extension de nom de fichier projet correspondant au modèle *. \* proj*. Toutefois, Visual Studio ne reconnaît qu’un sous-ensemble de ces extensions de nom de fichier projet, qui déterminent le système de projet spécifique au langage qui chargera le projet. Visual Studio n’a pas de système de projet basé sur MSBuild indépendant du langage.

 Par exemple, le système de projet C# charge les fichiers *. csproj* , mais Visual Studio n’est pas en mesure de charger un fichier *. fichier xxproj* . Un fichier projet pour les fichiers sources dans un langage arbitraire doit utiliser la même extension que Visual Basic ou les fichiers projet C# à charger dans Visual Studio.

## <a name="well-known-target-names"></a>Noms de cibles connus

 Si vous cliquez sur la commande **générer** dans Visual Studio, la cible par défaut est exécutée dans le projet. Dans de nombreux cas, cette cible est également nommée `Build`. La sélection de la commande **Régénérer** ou **Nettoyer** entraîne une tentative d'exécution d'une cible du même nom dans le projet. Un clic sur **Publier** se traduit par l'exécution d'une cible nommée `PublishOnly` dans le projet.

## <a name="configurations-and-platforms"></a>Configurations et plateformes

 Les configurations sont représentées dans les projets MSBuild par des propriétés regroupées dans un `PropertyGroup` élément qui contient un `Condition` attribut. Visual Studio examine ces conditions pour créer une liste de configurations de projet et de plateformes à afficher. Pour réussir à extraire cette liste, les conditions doivent avoir un format similaire à ce qui suit :

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 À cet effet, Visual Studio examine les conditions sur les éléments,, `PropertyGroup` `ItemGroup` , de `Import` Propriétés et Item.

## <a name="additional-build-actions"></a>Actions de génération supplémentaires

 Visual Studio vous permet de modifier le nom du type d’élément d’un fichier dans un projet avec la propriété **action de génération** de la fenêtre **Propriétés du fichier** . Les noms des types d'éléments **Compiler**, **EmbeddedResource**, **Contenu** et **Aucun** sont toujours répertoriés dans ce menu, avec tous les autres noms de types d'éléments figurant déjà dans votre projet. Pour garantir la disponibilité permanente de tous les noms de types d'éléments personnalisés dans ce menu, vous pouvez ajouter les noms à un type d'élément nommé `AvailableItemName`. Par exemple, en ajoutant ce qui suit à votre fichier projet, le type personnalisé **JScript** est ajouté à ce menu pour tous les projets qui l'importent :

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

L’ajout de noms de type d’élément au `AvailableItemName` type d’élément entraîne l’affichage des éléments de ce type dans **Explorateur de solutions**.

> [!NOTE]
> Certains noms de types d’éléments sont spécifiques à Visual Studio, mais ils ne sont pas répertoriés dans cette liste déroulante.

## <a name="in-process-compilers"></a>Compilateurs in-process

 Lorsque cela est possible, Visual Studio tente d’utiliser la version in-process du compilateur Visual Basic pour des performances accrues. (Non applicable à C#.) Pour que cela fonctionne correctement, les conditions suivantes doivent être remplies :

- Une cible du projet doit contenir une tâche nommée `Vbc` pour les projets Visual Basic.

- Le paramètre `UseHostCompilerIfAvailable` de la tâche doit avoir la valeur true.

## <a name="design-time-intellisense"></a>IntelliSense au moment du design

 Pour obtenir la prise en charge d’IntelliSense dans Visual Studio avant qu’une génération ait généré un assembly de sortie, les conditions suivantes doivent être remplies :

- Il doit exister une cible nommée `Compile`.

- La cible `Compile` ou l'une de ses dépendances doit appeler la tâche du compilateur du projet, par exemple `Csc` ou `Vbc`.

- La cible `Compile` ou l'une de ses dépendances doit faire en sorte que le compilateur reçoive tous les paramètres nécessaires à IntelliSense, en particulier toutes les références.

- Les conditions indiquées dans la section [compilateurs in-process](#in-process-compilers) doivent être remplies.

## <a name="build-solutions"></a>Créer des solutions

 Dans Visual Studio, le fichier solution et l’ordre de génération du projet sont contrôlés par Visual Studio lui-même. Lors de la génération d’une solution avec *msbuild.exe* sur la ligne de commande, MSBuild analyse le fichier solution et classe les générations du projet. Dans les deux cas, les projets sont générés individuellement en fonction de l'ordre des dépendances et les références entre projets ne sont pas parcourues. En revanche, quand des projets individuels sont générés avec *msbuild.exe*, les références entre projets sont parcourues.

 Lors de la génération dans Visual Studio, la propriété `$(BuildingInsideVisualStudio)` a la valeur `true` . Cela peut être utilisé dans vos fichiers projet ou *. targets* pour que la génération se comporte différemment.

## <a name="display-properties-and-items"></a>Afficher des propriétés et des éléments

 Visual Studio reconnaît certains noms et valeurs de propriétés. Par exemple, la présence de la propriété suivante dans un projet entraîne l'affichage de **Application Windows** dans la zone **Type d'application** du **Concepteur de projets**.

```xml
<OutputType>WinExe</OutputType>
```

 La valeur de la propriété peut être modifiée dans le **Concepteur de projets** et enregistrée dans le fichier projet. Si une valeur non valide est affectée à une telle propriété lors d’une modification manuelle, Visual Studio affiche un avertissement lorsque le projet est chargé et remplace la valeur non valide par une valeur par défaut.

 Visual Studio comprend les valeurs par défaut de certaines propriétés. Ces propriétés ne sont pas rendues persistantes dans le fichier projet sauf si elles possèdent des valeurs non définies par défaut.

 Les propriétés avec des noms arbitraires ne sont pas affichées dans Visual Studio. Pour modifier des propriétés arbitraires dans Visual Studio, vous devez ouvrir le fichier projet dans l’éditeur XML et les modifier manuellement. Pour plus d’informations, consultez la section [Modifier les fichiers projet dans Visual Studio](#edit-project-files-in-visual-studio) plus loin dans cette rubrique.

 Les éléments définis dans le projet avec des noms de types d’éléments arbitraires sont affichés par défaut dans la **Explorateur de solutions** sous leur nœud de projet. Pour masquer un élément, attribuez la valeur `Visible` aux métadonnées `false`. Par exemple, l’élément suivant participera au processus de génération, mais ne sera pas affiché dans **Explorateur de solutions**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> Les `Visible` métadonnées sont ignorées par **Explorateur de solutions** pour les projets C++. Les éléments s’affichent toujours même si `Visible` a la valeur false.

 Les éléments déclarés dans les fichiers importés dans le projet ne sont pas affichés par défaut. Les éléments créés pendant le processus de génération ne sont jamais affichés dans **Explorateur de solutions**.

## <a name="conditions-on-items-and-properties"></a>Conditions appliquées aux éléments et aux propriétés

 Pendant une génération, toutes les conditions sont respectées pleinement.

 Lors de la détermination des valeurs de propriété à afficher, les propriétés que Visual Studio considère comme dépendantes de la configuration sont évaluées différemment des propriétés qui sont considérées comme indépendantes de la configuration. Pour les propriétés dépendantes de la configuration, Visual Studio définit les `Configuration` Propriétés et de `Platform` manière appropriée et indique à MSBuild de réévaluer le projet. Pour les propriétés indépendantes de la configuration, le mode d'évaluation des conditions n'est pas déterminé.

 Les expressions conditionnelles sur les éléments sont toujours ignorées pour déterminer si l’élément doit être affiché dans **Explorateur de solutions**.

## <a name="debugging"></a>Débogage

 Pour rechercher et lancer l’assembly de sortie et attacher le débogueur, Visual Studio a besoin des propriétés `OutputPath` , `AssemblyName` et `OutputType` correctement définies. Le débogueur ne peut pas être attaché si le processus de génération n’a pas provoqué la génération d’un fichier *. pdb* par le compilateur.

## <a name="design-time-target-execution"></a>Exécution des cibles au moment du design

 Visual Studio tente d’exécuter des cibles portant certains noms lorsqu’il charge un projet. Il s'agit notamment des cibles `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths` et `CopyRunEnvironmentFiles`. Visual Studio exécute ces cibles afin que le compilateur puisse être initialisé pour fournir IntelliSense, que le débogueur puisse être initialisé et que les références affichées dans Explorateur de solutions peuvent être résolues. Si ces cibles ne sont pas présentes, le projet est chargé et généré correctement, mais l’expérience au moment du design dans Visual Studio ne sera pas entièrement fonctionnelle.

## <a name="edit-project-files-in-visual-studio"></a>Modifier des fichiers projet dans Visual Studio

 Pour modifier directement un projet MSBuild, vous pouvez ouvrir le fichier projet dans l’éditeur XML de Visual Studio.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Pour décharger et modifier un fichier projet dans Visual Studio

1. Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Décharger le projet**.

     Le projet est alors marqué **(non disponible)**.

2. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet non disponible, puis choisissez **modifier \<Project File>**.

     Le fichier projet s'ouvre dans l'Éditeur XML de Visual Studio.

3. Modifiez, enregistrez, puis fermez le fichier projet.

4. Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet indisponible et choisissez **Recharger le projet**.

## <a name="intellisense-and-validation"></a>IntelliSense et validation

 Lorsque vous utilisez l’éditeur XML pour modifier des fichiers projet, IntelliSense et la validation sont pilotés par les fichiers de schéma MSBuild. Celles-ci sont installées dans le cache de schéma, qui se trouve dans *\<Visual Studio installation directory> \Xml\Schemas\1033\MSBuild*.

 Les types MSBuild de base sont définis dans *Microsoft. Build. Core. xsd* et les types communs utilisés par Visual Studio sont définis dans *Microsoft. Build. CommonTypes. xsd*. Pour personnaliser les schémas afin d’obtenir IntelliSense et la validation des noms, des propriétés et des tâches de types d’éléments personnalisés, vous pouvez modifier *Microsoft. Build. xsd* ou créer votre propre schéma qui comprend les schémas CommonTypes ou Core. Si vous créez votre propre schéma, vous devez indiquer à l'Éditeur XML de l'utiliser à l'aide de la fenêtre **Propriétés** .

## <a name="edit-loaded-project-files"></a>Modifier des fichiers projet chargés

 Visual Studio met en cache le contenu des fichiers projet et des fichiers importés par les fichiers projet. Si vous modifiez un fichier projet chargé, Visual Studio vous invite automatiquement à recharger le projet afin que les modifications soient prises en compte. Toutefois, si vous modifiez un fichier importé par un projet chargé, aucune invite de rechargement ne s'affiche et vous devez décharger et recharger manuellement le projet pour que les modifications prennent effet.

## <a name="output-groups"></a>Groupes de sortie

 Plusieurs cibles définies dans *Microsoft. Common. targets* ont des noms se terminant par `OutputGroups` ou `OutputGroupDependencies` . Visual Studio appelle ces cibles pour recevoir des listes spécifiques de sorties de projet. Ainsi, la cible `SatelliteDllsProjectOutputGroup` crée une liste de tous les assemblys satellites créés par une génération. Ces groupes de sorties sont utilisés par des fonctionnalités, telles que la publication, le déploiement et les références entre projets. Les projets qui ne les définissent pas seront chargés et générés dans Visual Studio, mais certaines fonctionnalités risquent de ne pas fonctionner correctement.

## <a name="reference-resolution"></a>Résolution de référence

 La résolution des références est le processus consistant à utiliser des éléments de référence stockés dans un fichier projet pour localiser les assemblys actifs. Visual Studio doit déclencher la résolution de références pour afficher les propriétés détaillées de chaque référence dans la fenêtre **Propriétés** . La liste suivante décrit les trois types de références et leur mode de résolution.

- Références d'assembly :

   Le système de projet appelle une cible avec le nom connu `ResolveAssemblyReferences`. Cette cible doit produire des éléments avec le nom de type d'élément `ReferencePath`. Chacun de ces éléments doit avoir une spécification d'élément (la valeur de l'attribut `Include` d'un élément) qui contient le chemin d'accès complet à la référence. Les éléments doivent avoir toutes les métadonnées des éléments d'entrée passés en plus des nouvelles métadonnées suivantes :

  - `CopyLocal`, indiquant si l'assembly doit être copié dans le dossier de sortie ; la valeur peut être true ou false.

  - `OriginalItemSpec`, contenant la spécification d'élément d'origine de la référence.

  - `ResolvedFrom`, défini sur « {TargetFrameworkDirectory} » s’il a été résolu à partir du répertoire de .NET Framework.

- Références COM :

   Le système de projet appelle une cible avec le nom connu `ResolveCOMReferences`. Cette cible doit produire des éléments avec le nom de type d'élément `ComReferenceWrappers`. Chacun de ces éléments doit posséder une spécification d'élément qui contient le chemin d'accès complet à l'assembly d'interopérabilité pour la référence COM. Les éléments doivent avoir toutes les métadonnées des éléments d'entrée passés, en plus de nouvelles métadonnées portant le nom `CopyLocal`, qui indiquent si l'assembly doit être copié dans le dossier de sortie ; la valeur peut être true ou false.

- Références natives

   Le système de projet appelle une cible avec le nom connu `ResolveNativeReferences`. Cette cible doit produire des éléments avec le nom de type d'élément `NativeReferenceFile`. Les éléments doivent avoir toutes les métadonnées des éléments d'entrée passés, en plus d'une nouvelle métadonnée nommée `OriginalItemSpec`, contenant la spécification d'élément d'origine de la référence.

## <a name="performance-shortcuts"></a>Raccourcis de performances

 Si vous utilisez l’IDE de Visual Studio pour démarrer le débogage (en choisissant la touche F5 ou en choisissant **Déboguer**  >  **Démarrer le débogage** dans la barre de menus) ou pour générer votre projet (par exemple, **générer** la  >  **solution de build**), le processus de génération utilise une vérification des mises à jour rapide pour améliorer les performances. Dans les cas où les générations personnalisées créent les fichiers qui sont générés à leur tour, la vérification de mise à jour rapide n'identifie pas correctement les fichiers modifiés. Les projets qui ont besoin de vérifications de mise à jour plus complètes peuvent désactiver la vérification rapide en définissant la variable d'environnement `DISABLEFASTUPTODATECHECK=1`. Les projets peuvent également définir cela comme une propriété MSBuild dans le projet ou dans un fichier que le projet importe.

 Pour des builds classiques dans Visual Studio, la vérification des mises à jour rapide ne s'applique pas, et le projet est généré comme si vous appeliez la build dans une invite de commandes.

## <a name="see-also"></a>Voir aussi

- [Comment : étendre le processus de génération Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Démarrer une build à partir de l’IDE](../msbuild/starting-a-build-from-within-the-ide.md)
- [Inscrire des extensions du .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [Item, élément (MSBuild)](../msbuild/item-element-msbuild.md)
- [Property, élément (MSBuild)](../msbuild/property-element-msbuild.md)
- [Target, élément (MSBuild)](../msbuild/target-element-msbuild.md)
- [Csc (tâche)](../msbuild/csc-task.md)
- [Vbc (tâche)](../msbuild/vbc-task.md)
