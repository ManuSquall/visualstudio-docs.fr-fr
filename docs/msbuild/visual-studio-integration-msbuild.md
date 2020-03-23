---
title: Intégration de Visual Studio (MSBuild)
titleSuffix: ''
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3468ab5a6a185a759ab43229758c0ff4e9d00e35
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631196"
---
# <a name="visual-studio-integration-msbuild"></a>Intégration de Visual Studio (MSBuild)

Visual Studio héberge MSBuild pour charger et construire des projets gérés. Parce que MSBuild est responsable du projet, presque n’importe quel projet dans le format MSBuild peut être utilisé avec succès dans Visual Studio, même si le projet a été écrit par un outil différent et a un processus de construction personnalisé.

 Cet article décrit des aspects spécifiques de l’hébergement MSBuild de Visual Studio qui doivent être pris en considération lors de la personnalisation des projets et *.cibles* fichiers que vous souhaitez charger et construire dans Visual Studio. Ceux-ci vous aideront à vous assurer que Visual Studio fonctionnalités comme IntelliSense et de débogage de travail pour votre projet personnalisé.

 Pour plus d’informations sur les projets C, consultez [les fichiers du projet](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Extensions de nom de fichier projet

 *MSBuild.exe* reconnaît toute extension de nom de fichier de projet correspondant au modèle *.\* proj*. Toutefois, Visual Studio ne reconnaît qu’un sous-ensemble de ces extensions de noms de fichiers de projet, qui déterminent le système de projet spécifique à la langue qui chargera le projet. Visual Studio n’a pas de système de projet basé sur le MSBuild neutre en langue.

 Par exemple, le système de projet Cmd charge les fichiers *.csproj,* mais Visual Studio n’est pas en mesure de charger un fichier *.xxproj.* Un fichier de projet pour les fichiers sources dans un langage arbitraire doit utiliser la même extension que visual Basic ou les fichiers de projet C pour être chargés dans Visual Studio.

## <a name="well-known-target-names"></a>Noms de cibles connus

 En cliquant sur la commande **Build** dans Visual Studio, la cible par défaut du projet sera mise en compte. Dans de nombreux cas, cette cible est également nommée `Build`. La sélection de la commande **Régénérer** ou **Nettoyer** entraîne une tentative d'exécution d'une cible du même nom dans le projet. Un clic sur **Publier** se traduit par l'exécution d'une cible nommée `PublishOnly` dans le projet.

## <a name="configurations-and-platforms"></a>Configurations et plateformes

 Les configurations sont représentées dans les projets `PropertyGroup` MSBuild `Condition` par des propriétés regroupées dans un élément qui contient un attribut. Visual Studio examine ces conditions afin de créer une liste de configurations de projet et de plates-formes à afficher. Pour réussir à extraire cette liste, les conditions doivent avoir un format similaire à ce qui suit :

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio examine les `PropertyGroup` `ItemGroup`conditions `Import`sur , , , la propriété, et les éléments de l’élément à cette fin.

## <a name="additional-build-actions"></a>Actions de génération supplémentaires

 Visual Studio vous permet de modifier le nom de type élément d’un fichier dans un projet avec la propriété **Build Action** de la fenêtre **des propriétés Fichier.** Les noms des types d'éléments **Compiler**, **EmbeddedResource**, **Contenu** et **Aucun** sont toujours répertoriés dans ce menu, avec tous les autres noms de types d'éléments figurant déjà dans votre projet. Pour garantir la disponibilité permanente de tous les noms de types d'éléments personnalisés dans ce menu, vous pouvez ajouter les noms à un type d'élément nommé `AvailableItemName`. Par exemple, en ajoutant ce qui suit à votre fichier projet, le type personnalisé **JScript** est ajouté à ce menu pour tous les projets qui l'importent :

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Certains noms de type article sont spéciaux pour Visual Studio, mais pas répertoriés dans ce dropdown.

## <a name="in-process-compilers"></a>Compilateurs in-process

 Dans la mesure du possible, Visual Studio tentera d’utiliser la version en cours du compilateur Visual Basic pour augmenter les performances. (Non applicable à C.) Pour que cela fonctionne correctement, les conditions suivantes doivent être remplies :

- Dans une cible du projet, il `Vbc` doit y avoir une tâche nommée pour les projets Visual Basic.

- Le paramètre `UseHostCompilerIfAvailable` de la tâche doit avoir la valeur true.

## <a name="design-time-intellisense"></a>IntelliSense au moment du design

 Pour obtenir le soutien d’IntelliSense dans Visual Studio avant qu’une build n’ait généré un assemblage de sortie, les conditions suivantes doivent être remplies :

- Il doit exister une cible nommée `Compile`.

- La cible `Compile` ou l'une de ses dépendances doit appeler la tâche du compilateur du projet, par exemple `Csc` ou `Vbc`.

- La cible `Compile` ou l'une de ses dépendances doit faire en sorte que le compilateur reçoive tous les paramètres nécessaires à IntelliSense, en particulier toutes les références.

- Les conditions énumérées dans la section [des compilateurs en cours](#in-process-compilers) doivent être remplies.

## <a name="build-solutions"></a>Créer des solutions

 Au sein de Visual Studio, le fichier de solution et la commande de construction de projets sont contrôlés par Visual Studio lui-même. Lors de la construction d’une solution avec *msbuild.exe* sur la ligne de commande, MSBuild analyse le fichier de solution et ordonne la construction du projet. Dans les deux cas, les projets sont générés individuellement en fonction de l'ordre des dépendances et les références entre projets ne sont pas parcourues. En revanche, lorsque des projets individuels sont construits avec *msbuild.exe*, le projet de références de projet sont parcourus.

 Lors de la construction `$(BuildingInsideVisualStudio)` à l’intérieur Visual Studio, la propriété est définie à `true`. Cela peut être utilisé dans votre projet ou *.cibles* fichiers pour provoquer la construction de se comporter différemment.

## <a name="display-properties-and-items"></a>Afficher des propriétés et des éléments

 Visual Studio reconnaît certains noms et valeurs de propriété. Par exemple, la présence de la propriété suivante dans un projet entraîne l'affichage de **Application Windows** dans la zone **Type d'application** du **Concepteur de projets**.

```xml
<OutputType>WinExe</OutputType>
```

 La valeur de la propriété peut être modifiée dans le **Concepteur de projets** et enregistrée dans le fichier projet. Si une telle propriété reçoit une valeur invalide par l’édition à la main, Visual Studio affichera un avertissement lorsque le projet est chargé et remplacera la valeur invalide par une valeur par défaut.

 Visual Studio comprend les défauts de paiement pour certaines propriétés. Ces propriétés ne sont pas rendues persistantes dans le fichier projet sauf si elles possèdent des valeurs non définies par défaut.

 Les propriétés avec des noms arbitraires ne sont pas affichées dans Visual Studio. Pour modifier les propriétés arbitraires de Visual Studio, vous devez ouvrir le fichier de projet dans l’éditeur XML et les modifier à la main. Pour plus d’informations, consultez la section [Modifier les fichiers projet dans Visual Studio](#edit-project-files-in-visual-studio) plus loin dans cette rubrique.

 Les éléments définis dans le projet avec des noms arbitraires de type élément sont par défaut affichés dans la **Solution Explorer** sous leur nœud de projet. Pour masquer un élément, attribuez la valeur `Visible` aux métadonnées `false`. Par exemple, l’élément suivant participera au processus de construction mais ne sera pas affiché dans **Solution Explorer**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> Les `Visible` métadonnées sont ignorées par **Solution Explorer** pour les projets C. Les articles seront toujours `Visible` affichés même s’ils sont mis à faux.

 Les éléments déclarés dans les fichiers importés dans le projet ne sont pas affichés par défaut. Les éléments créés pendant le processus de construction ne sont jamais affichés dans **Solution Explorer**.

## <a name="conditions-on-items-and-properties"></a>Conditions appliquées aux éléments et aux propriétés

 Pendant une génération, toutes les conditions sont respectées pleinement.

 Lors de la détermination des valeurs de propriété à afficher, les propriétés que Visual Studio considère comme dépendantes de la configuration sont évaluées différemment des propriétés qu’il considère comme indépendantes de configuration. Pour les propriétés qu’il `Configuration` considère `Platform` comme dépendantes de la configuration, Visual Studio définit les propriétés et les propriétés de manière appropriée et demande à MSBuild de réévaluer le projet. Pour les propriétés indépendantes de la configuration, le mode d'évaluation des conditions n'est pas déterminé.

 Les expressions conditionnelles sur des éléments sont toujours ignorées aux fins de décider si l’élément doit être affiché dans **Solution Explorer**.

## <a name="debugging"></a>Débogage

 Afin de trouver et de lancer l’assemblage de sortie et `OutputPath`d’attacher le débbugger, Visual Studio a besoin des propriétés, `AssemblyName`et `OutputType` correctement défini. Le débagénaire ne se fixe pas si le processus de construction n’a pas causé le compilateur de générer un fichier *.pdb.*

## <a name="design-time-target-execution"></a>Exécution des cibles au moment du design

 Visual Studio tente d’exécuter des cibles avec certains noms quand il charge un projet. Il s'agit notamment des cibles `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths` et `CopyRunEnvironmentFiles`. Visual Studio exécute ces cibles afin que le compilateur puisse être paralé pour fournir IntelliSense, le débbuggeur peut être initialisé, et les références affichées dans Solution Explorer peuvent être résolues. Si ces cibles ne sont pas présentes, le projet se chargera et se construira correctement, mais l’expérience de conception-temps dans Visual Studio ne sera pas entièrement fonctionnelle.

## <a name="edit-project-files-in-visual-studio"></a>Modifier des fichiers projet dans Visual Studio

 Pour modifier directement un projet MSBuild, vous pouvez ouvrir le fichier de projet dans l’éditeur Visual Studio XML.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Pour décharger et modifier un fichier projet dans Visual Studio

1. Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Décharger le projet**.

     Le projet est alors marqué **(non disponible)**.

2. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet indisponible et choisissez **Modifier \<Fichier projet>**.

     Le fichier projet s'ouvre dans l'Éditeur XML de Visual Studio.

3. Modifiez, enregistrez, puis fermez le fichier projet.

4. Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet indisponible et choisissez **Recharger le projet**.

## <a name="intellisense-and-validation"></a>IntelliSense et validation

 Lors de l’utilisation de l’éditeur XML pour modifier les fichiers de projet, IntelliSense et validation est pilotée par les fichiers schémas MSBuild. Ceux-ci sont installés dans le cache schéma, qui peut être trouvé dans * \<visual Studio répertoire d’installation> Xml-Schemas-1033-MSBuild*.

 Les types DE base MSBuild sont définis dans *Microsoft.Build.Core.xsd* et les types communs utilisés par Visual Studio sont définis dans *Microsoft.Build.CommonTypes.xsd*. Pour personnaliser les schémas de sorte que vous avez IntelliSense et la validation pour les noms de type d’article personnalisé, les propriétés et les tâches, vous pouvez soit modifier *Microsoft.Build.xsd*, ou créer votre propre schéma qui comprend les commonTypes ou schémas de base. Si vous créez votre propre schéma, vous devez indiquer à l'Éditeur XML de l'utiliser à l'aide de la fenêtre **Propriétés** .

## <a name="edit-loaded-project-files"></a>Modifier des fichiers projet chargés

 Visual Studio cache le contenu des fichiers de projet et des fichiers importés par les fichiers de projet. Si vous modifiez un fichier de projet chargé, Visual Studio vous incitera automatiquement à recharger le projet afin que les modifications prennent effet. Toutefois, si vous modifiez un fichier importé par un projet chargé, aucune invite de rechargement ne s'affiche et vous devez décharger et recharger manuellement le projet pour que les modifications prennent effet.

## <a name="output-groups"></a>Groupes de sortie

 Plusieurs cibles définies dans *Microsoft.Common.targets* ont des noms se terminant dans `OutputGroups` ou `OutputGroupDependencies`. Visual Studio appelle ces cibles pour obtenir des listes spécifiques de sorties de projet. Ainsi, la cible `SatelliteDllsProjectOutputGroup` crée une liste de tous les assemblys satellites créés par une génération. Ces groupes de sorties sont utilisés par des fonctionnalités, telles que la publication, le déploiement et les références entre projets. Les projets qui ne les définissent pas se chargeront et s’accumulent dans Visual Studio, mais certaines fonctionnalités peuvent ne pas fonctionner correctement.

## <a name="reference-resolution"></a>Résolution de référence

 La résolution des références est le processus consistant à utiliser des éléments de référence stockés dans un fichier projet pour localiser les assemblys actifs. Visual Studio doit déclencher la résolution de référence afin d’afficher des propriétés détaillées pour chaque référence dans la fenêtre **Propriétés.** La liste suivante décrit les trois types de références et leur mode de résolution.

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

 Si vous utilisez l’IDE Visual Studio pour commencer à débogage (soit en choisissant la clé F5 ou en choisissant **Debug** > **Start Debugging** sur la barre de menu) ou pour construire votre projet (par exemple, **Build** > **Build Solution**), le processus de construction utilise une vérification de mise à jour rapide pour améliorer les performances. Dans les cas où les générations personnalisées créent les fichiers qui sont générés à leur tour, la vérification de mise à jour rapide n'identifie pas correctement les fichiers modifiés. Les projets qui ont besoin de vérifications de mise à jour plus complètes peuvent désactiver la vérification rapide en définissant la variable d'environnement `DISABLEFASTUPTODATECHECK=1`. Les projets peuvent également définir cela comme une propriété MSBuild dans le projet ou dans un fichier que le projet importe.

 Pour des builds classiques dans Visual Studio, la vérification des mises à jour rapide ne s'applique pas, et le projet est généré comme si vous appeliez la build dans une invite de commandes.

## <a name="see-also"></a>Voir aussi

- [Comment : Étendre le processus de construction visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Démarrer une build à partir de l’IDE](../msbuild/starting-a-build-from-within-the-ide.md)
- [Inscrire des extensions du .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [Item, élément (MSBuild)](../msbuild/item-element-msbuild.md)
- [Élément de propriété (MSBuild)](../msbuild/property-element-msbuild.md)
- [Target, élément (MSBuild)](../msbuild/target-element-msbuild.md)
- [Tâche Csc](../msbuild/csc-task.md)
- [Tâche Vbc](../msbuild/vbc-task.md)
