---
title: Utiliser le contexte de l’interface utilisateur basée sur des règles pour les extensions Visual Studio
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: fc24fe3f5b27b3c92f0629ed378c1a97c820cd0a
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037105"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Comment : utiliser le contexte de l’interface utilisateur basé sur des règles pour les extensions Visual Studio

Visual Studio permet le chargement de VSPackages lorsque certains s connus <xref:Microsoft.VisualStudio.Shell.UIContext> sont activés. Toutefois, ces contextes d’interface utilisateur ne sont pas granulaires, ce qui laisse les auteurs d’extension non choisis, mais sélectionne un contexte d’interface utilisateur disponible qui s’active avant le point où ils voulaient vraiment que le VSPackage se charge. Pour obtenir la liste des contextes d’interface utilisateur connus, consultez <xref:Microsoft.VisualStudio.Shell.KnownUIContexts> .

Le chargement des packages peut avoir un impact sur les performances et le chargement plus tôt que nécessaire n’est pas la meilleure pratique. Visual Studio 2015 a introduit le concept de contextes d’interface utilisateur basés sur des règles, un mécanisme qui permet aux auteurs d’extensions de définir les conditions précises sous lesquelles un contexte d’interface utilisateur est activé et les VSPackages associés sont chargés.

## <a name="rule-based-ui-context"></a>Contexte de l’interface utilisateur basée sur des règles

Une « règle » se compose d’un nouveau contexte d’interface utilisateur (GUID) et d’une expression booléenne qui fait référence à un ou plusieurs « termes » associés à des opérations logiques « and », « or », « not ». Les « termes » sont évalués de manière dynamique au moment de l’exécution et l’expression est réévaluée chaque fois que l’un de ses termes change. Lorsque l’expression prend la valeur true, le contexte d’interface utilisateur associé est activé. Dans le cas contraire, le contexte de l’interface utilisateur est désactivé.

Le contexte de l’interface utilisateur basé sur des règles peut être utilisé de différentes manières :

1. Spécifiez les contraintes de visibilité pour les commandes et les fenêtres outil. Vous pouvez masquer les fenêtres commandes/outils jusqu’à ce que la règle de contexte d’interface utilisateur soit remplie.

2. Pour les contraintes de chargement automatique : charge automatiquement les packages uniquement lorsque la règle est remplie.

3. En tant que tâche retardée : Retardez le chargement jusqu’à ce qu’un intervalle spécifié se soit écoulé et que la règle soit toujours remplie.

   Le mécanisme peut être utilisé par n’importe quelle extension Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Créer un contexte d’interface utilisateur basé sur des règles
 Supposons que vous avez une extension appelée TestPackage, qui offre une commande de menu qui s’applique uniquement aux fichiers avec l’extension *. config* . Avant VS2015, la meilleure option consistait à charger TestPackage lorsque le <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> contexte de l’interface utilisateur était activé. Le chargement de TestPackage de cette façon n’est pas efficace, car la solution chargée ne peut même pas contenir un fichier *. config* . Ces étapes montrent comment utiliser le contexte de l’interface utilisateur basé sur des règles pour activer un contexte d’interface utilisateur uniquement lorsqu’un fichier avec l’extension *. config* est sélectionné, et charger TestPackage quand ce contexte d’interface utilisateur est activé.

1. Définissez un nouveau GUID UIContext et ajoutez à la classe VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> et à <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> .

    Supposons, par exemple, qu’un nouveau UIContext « UIContextGuid » soit ajouté. Le GUID créé (vous pouvez créer un GUID en cliquant sur **Outils**  >  **créer un GUID**) est « 8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B ». Vous ajoutez ensuite la déclaration suivante à l’intérieur de votre classe de package :

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Pour les attributs, ajoutez les valeurs suivantes : (les détails de ces attributs seront expliqués plus tard)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Ces métadonnées définissent le nouveau GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) et une expression faisant référence à un terme unique, « DotConfig ». Le terme « DotConfig » prend la valeur true chaque fois que la sélection actuelle dans la hiérarchie Active a un nom qui correspond au modèle d’expression régulière « \\ . config $ » (se termine par *. config*). La valeur (par défaut) définit un nom facultatif pour la règle utile pour le débogage.

    Les valeurs de l’attribut sont ajoutées à l’attribut pkgdef généré au moment de la génération par la suite.

2. Dans le fichier VSCT pour les commandes de TestPackage, ajoutez l’indicateur « DynamicVisibility » aux commandes appropriées :

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. Dans la section de visibilité de VSCT, liez les commandes appropriées au nouveau GUID UIContext défini dans #1 :

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Dans la section Symbols, ajoutez la définition de UIContext :

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Désormais, les commandes de menu contextuel pour les fichiers * \* . config* sont visibles uniquement lorsque l’élément sélectionné dans l’Explorateur de solutions est un fichier *. config* et que le package n’est pas chargé tant que l’une de ces commandes n’est pas sélectionnée.

   Ensuite, utilisez un débogueur pour confirmer que le package se charge uniquement quand vous l’attendez. Pour déboguer TestPackage :

5. Définissez un point d’arrêt dans la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode.

6. Générez le TestPackage et démarrez le débogage.

7. Créez un projet ou ouvrez-en un.

8. Sélectionnez un fichier portant une extension autre que *. config*. Le point d’arrêt ne doit pas être atteint.

9. Sélectionnez le fichier *App.Config* .

   Le TestPackage se charge et s’arrête au point d’arrêt.

## <a name="add-more-rules-for-ui-context"></a>Ajouter d’autres règles pour le contexte de l’interface utilisateur
 Étant donné que les règles de contexte d’interface utilisateur sont des expressions booléennes, vous pouvez ajouter des règles restreintes pour un contexte d’interface utilisateur. Par exemple, dans le contexte de l’interface utilisateur ci-dessus, vous pouvez spécifier que la règle s’applique uniquement quand une solution avec un projet est chargée. De cette façon, les commandes ne s’affichent pas si vous ouvrez un fichier *. config* en tant que fichier autonome, et non dans le cadre d’un projet.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT.SolutionHasSingleProject_string , VSConstants.UICONTEXT.SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 À présent, l’expression fait référence à trois termes. Les deux premiers termes, « SingleProject » et « MultipleProjects », font référence à d’autres contextes d’interface utilisateur connus (par leurs GUID). Le troisième terme « DotConfig » est le contexte de l’interface utilisateur basé sur les règles défini précédemment dans cet article.

## <a name="delayed-activation"></a>Activation différée
 Les règles peuvent avoir un « délai » facultatif. Le délai est exprimé en millisecondes. S’il est présent, le délai entraîne le report de l’activation ou de la désactivation du contexte d’interface utilisateur d’une règle par cet intervalle de temps. Si la règle est de nouveau modifiée avant l’intervalle de délai, rien ne se produit. Ce mécanisme peut être utilisé pour « échelonner » les étapes d’initialisation, en particulier l’initialisation unique sans compter sur les minuteurs ou l’inscription pour les notifications inactives.

 Par exemple, vous pouvez spécifier votre règle de charge de test pour avoir un délai de 100 millisecondes :

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Types de terme

Voici les différents types de termes pris en charge :

|Terme|Description|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Le GUID fait référence à un contexte d’interface utilisateur. Le terme est vrai chaque fois que le contexte de l’interface utilisateur est actif et false dans le cas contraire.|
|HierSingleSelectionName:\<pattern>|Le terme est vrai chaque fois que la sélection dans la hiérarchie Active est un élément unique et que le nom de l’élément sélectionné correspond à l’expression régulière .net donnée par « Pattern ».|
|UserSettingsStoreQuery:\<query>|« requête » représente un chemin d’accès complet dans le magasin des paramètres utilisateur, qui doit correspondre à une valeur différente de zéro. La requête est fractionnée en « collection » et « propertyName » à la dernière barre oblique.|
|ConfigSettingsStoreQuery:\<query>|« requête » représente un chemin d’accès complet dans le magasin des paramètres de configuration, qui doit correspondre à une valeur différente de zéro. La requête est fractionnée en « collection » et « propertyName » à la dernière barre oblique.|
|ActiveProjectFlavor:\<projectTypeGuid>|Le terme sera vrai chaque fois que le projet actuellement sélectionné est aromatisé (agrégé) et qu’un parfum correspond au GUID du type de projet donné.|
|ActiveEditorContentType:\<contentType>|Le terme est true lorsque le document sélectionné est un éditeur de texte avec le type de contenu donné. Remarque : lorsque le document sélectionné est renommé, ce terme n’est pas actualisé tant que le fichier n’est pas fermé et rouvert.|
|ActiveProjectCapability:\<Expression>|Le terme est true lorsque les fonctionnalités de projet actives correspondent à l’expression fournie. Une expression peut être telle que VB &#124; CSharp.|
|SolutionHasProjectCapability:\<Expression>|Semblable à ci-dessus, mais term a la valeur true lorsque la solution a un projet chargé qui correspond à l’expression.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Le terme sera vrai chaque fois qu’une solution a un projet qui est aromatisé (agrégé) et dont le parfum correspond au GUID du type de projet donné.|
|ProjectAddedItem:\<pattern>| Le terme est true lorsqu’un fichier correspondant au « modèle » est ajouté à un projet dans le soluion qui est ouvert.|
|ActiveProjectOutputType:\<outputType>|Le terme est true lorsque le type de sortie pour le projet actif correspond exactement.  Le outputType peut être un entier ou un <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> type.|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|Le terme est true lorsque le projet actif a la propriété de build spécifiée et que la valeur de propriété correspond au filtre Regex fourni. Pour plus d’informations sur les propriétés de build, reportez-vous à [persistance des données dans les fichiers projet MSBuild](internals/persisting-data-in-the-msbuild-project-file.md) .|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|Le terme est true lorsque la solution a un projet chargé avec la propriété de build spécifiée et que la valeur de propriété correspond au filtre Regex fourni.|

## <a name="compatibility-with-cross-version-extension"></a>Compatibilité avec l’extension Cross-version

Les contextes d’interface utilisateur basés sur des règles sont une nouvelle fonctionnalité de Visual Studio 2015 et ne sont pas portées vers des versions antérieures. Le portage vers des versions antérieures crée un problème avec les extensions/packages qui ciblent plusieurs versions de Visual Studio. Ces versions devraient être chargées automatiquement dans Visual Studio 2013 et versions antérieures, mais peuvent tirer parti des contextes d’interface utilisateur basés sur des règles pour empêcher leur chargement automatique dans Visual Studio 2015.

Pour prendre en charge de tels packages, les entrées AutoLoadPackages dans le registre peuvent désormais fournir un indicateur dans le champ valeur pour indiquer que l’entrée doit être ignorée dans Visual Studio 2015 et versions ultérieures. Pour ce faire, vous pouvez ajouter une option Flags à <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> . Les VSPackages peuvent maintenant ajouter l’option **SkipWhenUIContextRulesActive** à leur <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attribut pour indiquer que l’entrée doit être ignorée dans Visual Studio 2015 et versions ultérieures.
## <a name="extensible-ui-context-rules"></a>Règles de contexte d’interface utilisateur extensible

Parfois, les packages ne peuvent pas utiliser de règles de contexte d’interface utilisateur statiques. Par exemple, supposons que vous disposiez d’un package prenant en charge l’extensibilité, de sorte que l’état de la commande est basé sur les types d’éditeur pris en charge par les fournisseurs MEF importés. La commande est activée si une extension prend en charge le type d’édition actuel. Dans ce cas, le package lui-même ne peut pas utiliser une règle de contexte d’interface utilisateur statique, car les termes changent en fonction des extensions MEF disponibles.

Pour prendre en charge de tels packages, les contextes d’interface utilisateur basés sur des règles prennent en charge une expression codée en dur « * » qui indique que tous les termes ci-dessous seront joints avec ou. Cela permet au package principal de définir un contexte d’interface utilisateur basé sur des règles connu et de lier son état de commande à ce contexte. Par la suite, toute extension MEF ciblée pour le package maître peut ajouter ses termes aux éditeurs pris en charge sans affecter d’autres termes ou l’expression principale.

La documentation du constructeur <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> illustre la syntaxe des règles de contexte d’interface utilisateur extensible.
