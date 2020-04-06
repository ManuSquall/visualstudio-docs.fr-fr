---
title: 'Comment : Utiliser le contexte de l’interface utilisateur basé sur les règles pour visualiser les extensions de studio (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: de1a1e0a2022482433f81b0b2810b0d201ab7b8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710597"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Comment : Utiliser le contexte de l’interface utilisateur basée sur les règles pour les extensions Visual Studio

Visual Studio permet le chargement de VSPackages lorsque certains s bien connus <xref:Microsoft.VisualStudio.Shell.UIContext>sont activés. Cependant, ces contextes d’interface utilisateur ne sont pas fin grainé, ce qui laisse les auteurs d’extension pas d’autre choix que de choisir un contexte d’interface utilisateur disponible qui s’active avant le point qu’ils voulaient vraiment le VSPackage à charger. Pour une liste de contextes d’interface utilisateur bien connus, voir <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.

Le chargement des paquets peut avoir un impact sur les performances et les charger plus tôt que nécessaire n’est pas la meilleure pratique. Visual Studio 2015 a introduit le concept de contextes d’interface utilisateur basés sur des règles, un mécanisme qui permet aux auteurs d’extension de définir les conditions précises dans lesquelles un contexte d’interface utilisateur est activé et les VSPackages associés sont chargés.

## <a name="rule-based-ui-context"></a>Contexte de l’interface utilisateur fondé sur des règles

Une «règle» consiste en un nouveau contexte d’interface utilisateur (un GUID) et une expression Boolean qui fait référence à un ou plusieurs "Termes" combinés à des opérations logiques "et", "ou" "non". Les « termes » sont évalués de façon dynamique au moment de l’exécution et l’expression est réévaluée chaque fois que l’un de ses termes change. Lorsque l’expression s’évalue à vrai, le contexte d’interface utilisateur associé est activé. Dans le cas contraire, le contexte de l’interface utilisateur est désactivé.

Le contexte de l’interface utilisateur fondé sur des règles peut être utilisé de diverses façons :

1. Spécifier des contraintes de visibilité pour les commandes et les fenêtres d’outils. Vous pouvez masquer les commandes/fenêtres d’outils jusqu’à ce que la règle du contexte de l’interface utilisateur soit respectée.

2. En tant que contraintes de charge automatique : les paquets de charge automatique seulement lorsque la règle est respectée.

3. Comme tâche retardée : retarder le chargement jusqu’à ce qu’un intervalle spécifié soit passé et que la règle soit toujours respectée.

   Le mécanisme peut être utilisé par n’importe quelle extension Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Créer un contexte d’interface utilisateur fondé sur des règles
 Supposons que vous avez une extension appelée TestPackage, qui offre une commande de menu qui ne s’applique qu’aux fichiers avec extension *.config.* Avant VS2015, la meilleure option était <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> de charger TestPackage lorsque le contexte de l’interface utilisateur a été activé. Le chargement de TestPackage de cette façon n’est pas efficace, puisque la solution chargée peut même ne pas contenir un fichier *.config.* Ces étapes montrent comment le contexte de l’interface utilisateur basé sur des règles peut être utilisé pour activer un contexte d’interface utilisateur uniquement lorsqu’un fichier avec extension *.config* est sélectionné, et charger TestPackage lorsque ce contexte d’interface utilisateur est activé.

1. Définissez un nouveau GUID UIContext et <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> ajoutez <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>à la classe VSPackage et .

    Supposons, par exemple, qu’un nouveau UIContext "UIContextGuid" doit être ajouté. Le GUID créé (vous pouvez créer un GUID en cliquant sur **Tools** > **Create GUID**) est "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Vous ajoutez ensuite la déclaration suivante à l’intérieur de votre classe de colis :

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Pour les attributs, ajoutez les valeurs suivantes : (Les détails de ces attributs seront expliqués plus tard)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Ces métadonnées définissent le nouveau GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) et une expression faisant référence à un seul terme, "DotConfig". Le terme "DotConfig" s’évalue à vrai chaque fois que la sélection actuelle\\dans la hiérarchie active a un nom qui correspond au modèle d’expression régulière ".config$" (se termine par *.config*). La valeur (par défaut) définit un nom facultatif pour la règle utile pour le débogage.

    Les valeurs de l’attribut sont ajoutées au pkgdef généré pendant le temps de construction par la suite.

2. Dans le fichier VSCT pour les commandes du TestPackage, ajoutez le drapeau « DynamicVisibility » aux commandes appropriées :

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. Dans la section Visibilities du VSCT, lier les commandes appropriées au nouveau GUID UIContext défini en #1 :

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Dans la section Symboles, ajoutez la définition de l’interface utilisateur :

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Maintenant, les commandes de * \** menu contextuelle pour les fichiers .config ne seront visibles que lorsque l’élément sélectionné dans l’explorateur de la solution est un fichier *.config* et le paquet ne sera pas chargé jusqu’à ce que l’une de ces commandes est sélectionnée.

   Ensuite, utilisez un débbuggeur pour confirmer que le paquet ne se charge que lorsque vous vous y attendez. Pour déboiffer TestPackage:

5. Définissez un point <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> d’arrêt dans la méthode.

6. Construisez le TestPackage et commencez à débogage.

7. Créez un projet ou ouvrez-en un.

8. Sélectionnez n’importe quel fichier avec une extension autre que *.config*. Le point d’arrêt ne doit pas être touché.

9. Sélectionnez le fichier *App.Config.*

   Le TestPackage se charge et s’arrête au point d’arrêt.

## <a name="add-more-rules-for-ui-context"></a>Ajouter plus de règles pour le contexte de l’assurance-chômage
 Étant donné que les règles de contexte d’interface utilisateur sont des expressions Boolean, vous pouvez ajouter des règles plus restreintes pour un contexte d’interface utilisateur. Par exemple, dans le contexte de l’interface utilisateur ci-dessus, vous pouvez spécifier que la règle ne s’applique que lorsqu’une solution avec un projet est chargée. De cette façon, les commandes ne se présenteront pas si vous ouvrez un fichier *.config* comme un fichier autonome, pas dans le cadre d’un projet.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Maintenant, l’expression fait référence à trois termes. Les deux premiers termes, "SingleProject" et "MultipleProjects", se réfèrent à d’autres contextes d’interface utilisateur bien connus (par leurs GUID). Le troisième terme, "DotConfig" est le contexte d’interface utilisateur fondé sur des règles défini plus tôt dans cet article.

## <a name="delayed-activation"></a>Activation retardée
 Les règles peuvent avoir un «retard» facultatif. Le délai est spécifié en millisecondes. Si c’est le cas, le retard entraîne le retard d’activation ou de désactivation du contexte d’interface utilisateur d’une règle d’ici. Si la règle change avant l’intervalle de retard, alors rien ne se passe. Ce mécanisme peut être utilisé pour « échelonner » les étapes de initialisation - en particulier l’initialisation ponctuelle sans compter sur les minuteries ou l’enregistrement des notifications inactives.

 Par exemple, vous pouvez spécifier votre règle de charge d’essai pour avoir un délai de 100 millisecondes :

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Types de termes

Voici les différents types de terme qui sont soutenus :

|Terme|Description|
|-|-|
|Nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnnnn|Le GUID fait référence à un contexte d’interface utilisateur. Le terme sera vrai chaque fois que le contexte de l’interface utilisateur est actif et faux autrement.|
|HierSingleSelectionName:\<modèle>|Le terme sera vrai chaque fois que la sélection dans la hiérarchie active est un seul élément et le nom de l’élément sélectionné correspond à l’expression régulière .Net donnée par "modèle".|
|UserSettingsStoreQuery:\<requête>|La « requête » représente un chemin complet dans le magasin de paramètres de l’utilisateur, qui doit évaluer à une valeur non nulle. La requête est divisée en une "collection" et "propertyName" à la dernière barre oblique.|
|ConfigSettingsStoreQuery:\<requête>|La « requête » représente un chemin complet dans le magasin de paramètres config, qui doit évaluer à une valeur non nulle. La requête est divisée en une "collection" et "propertyName" à la dernière barre oblique.|
|ActiveProjectFlavor:\<projectTypeGuid>|Le terme sera vrai chaque fois que le projet actuellement sélectionné est aromatisé (agrégé) et a une saveur correspondant au type de projet donné GUID.|
|ActiveEditorContentType:\<contentType>|Le terme sera vrai lorsque le document sélectionné est un éditeur de texte avec le type de contenu donné. Remarque : lorsque le document sélectionné est renommé, ce terme ne se rafraîchit pas tant que le fichier n’est pas fermé et rouvert.|
|ActiveProjectCapability:\<Expression>|Le terme est vrai lorsque les capacités actives du projet correspondent à l’expression fournie. Une expression peut être quelque chose comme VB &#124; CSharp.|
|SolutionHasProjectCapability:\<Expression>|Semblable à ci-dessus, mais terme est vrai lorsque la solution a un projet chargé qui correspond à l’expression.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Le terme sera vrai chaque fois qu’une solution a un projet qui est aromatisé (agrégé) et a une saveur correspondant au type de projet donné GUID.|
|ProjectAddedItem:\<modèle>| Le terme est vrai lorsqu’un fichier correspondant au « modèle » est ajouté à un projet dans la soluion qui est ouverte.|
|ActiveProjectOutputType:\<outputType>|Le terme est vrai lorsque le type de sortie pour le projet actif correspond exactement.  Le outputType pourrait être un <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> intégrant ou un type.|
|ActiveProjectBuildProperty:\<buildProperty>'\<regex>|Le terme est vrai lorsque le projet actif a la propriété de construction spécifiée et la valeur de la propriété correspond à filtre regex fourni. Consultez [les données persistantes dans les fichiers de projets MSBuild](internals/persisting-data-in-the-msbuild-project-file.md) pour plus de détails sur les propriétés de construction.|
|SolutionHasProjectBuildProperty:\<buildProperty>'\<regex>|Le terme est vrai lorsque la solution a un projet chargé avec la propriété de construction spécifiée et la valeur de la propriété correspond au filtre regex fourni.|

## <a name="compatibility-with-cross-version-extension"></a>Compatibilité avec extension multi-version

UI Contexts, basé sur des règles, est une nouvelle fonctionnalité de Visual Studio 2015 et ne serait pas porté à des versions antérieures. Ne pas porter à des versions antérieures crée un problème avec les extensions / paquets qui ciblent plusieurs versions de Visual Studio. Ces versions devraient être autochargées dans Visual Studio 2013 et plus tôt, mais peuvent bénéficier de contextes d’interface utilisateur basés sur des règles pour éviter d’être auto-chargé dans Visual Studio 2015.

Afin de prendre en charge ces paquets, autoLoadPackages entrées dans le registre peut maintenant fournir un drapeau dans son champ de valeur pour indiquer que l’entrée doit être ignorée dans Visual Studio 2015 et plus. Cela peut être fait en <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>ajoutant une option de drapeaux à . VSPackages peut maintenant ajouter **SkipWhenUIContextRulesActive** option à leur <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attribut pour indiquer que l’entrée doit être ignorée dans Visual Studio 2015 et ci-dessus.
## <a name="extensible-ui-context-rules"></a>Règles extensibles de contexte d’interface utilisateur

Parfois, les paquets ne peuvent pas utiliser des règles statiques de contexte d’interface utilisateur. Supposons, par exemple, que vous ayez un paquet soutenant l’exténuabilité de telle sorte que l’état de commande soit basé sur les types d’éditeurs qui sont pris en charge par les fournisseurs de MEF importés. La commande est activée s’il y a une extension à l’appui du type de modification en cours. Dans de tels cas, le paquet lui-même ne peut pas utiliser une règle statique de contexte d’interface utilisateur, puisque les termes changeraient en fonction des extensions MEF disponibles.

Afin de prendre en charge ces paquets, les contextes d’interface utilisateur fondés sur des règles prennent en charge une expression codée en dur « » qui indique que tous les termes ci-dessous seront joints à la RO. Cela permet au paquet principal de définir un contexte d’interface utilisateur fondé sur des règles et de lier son état de commande à ce contexte. Ensuite, toute extension MEF ciblée pour le paquet maître peut ajouter ses termes pour les éditeurs qu’il prend en charge sans avoir d’impact sur d’autres termes ou l’expression principale.

La <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> documentation du constructeur montre la syntaxe pour les règles extensibles du contexte de l’interface utilisateur.
