---
title: 'Procédure : Utiliser le contexte de l’interface utilisateur basée sur une règle pour les Extensions Visual Studio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: madskristensen
ms.author: madsk
ms.workload:
- vssdk
ms.openlocfilehash: c3075ca5092dd1b8a69aa4b34c0e507505cf7123
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67309676"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Procédure : Utiliser le contexte d’interface utilisateur basée sur une règle pour les extensions Visual Studio

Visual Studio permet le chargement de VSPackages lorsque certains connu <xref:Microsoft.VisualStudio.Shell.UIContext>s sont activés. Toutefois, ces contextes d’interface utilisateur ne sont pas bien plus précis, ce qui ne laisse les auteurs de l’extension aucun choix mais permettant de sélectionner un contexte d’interface utilisateur disponible qui active avant la virgule, ils voulaient réellement le VSPackage à charger. Pour obtenir la liste des contextes d’interface utilisateur bien connus, consultez <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.

Le chargement de packages peut avoir un impact sur les performances et leur chargement plus tôt que nécessaire n’est pas la meilleure pratique. Visual Studio 2015 introduit le concept de contextes d’interface utilisateur basée sur des règles, un mécanisme qui permet aux auteurs d’extension définir les conditions précises sous lesquelles un contexte d’interface utilisateur est activé et VSPackages associés sont chargés.

## <a name="rule-based-ui-context"></a>Contexte de l’interface utilisateur basée sur la règle

Une « règle » se compose d’un nouveau contexte de l’interface utilisateur (un GUID) et une expression booléenne qui fait référence à un ou plusieurs « conditions » associé logique « et », « ou », « non » les opérations. « Conditions » sont évaluées de manière dynamique lors de l’exécution et l’expression est réévaluée chaque fois qu’un de ses modifications des termes du contrat. Lorsque l’expression a la valeur true, le contexte de l’interface utilisateur associée est activé. Sinon, le contexte de l’interface utilisateur est désactivé.

En fonction des règles de contexte de l’interface utilisateur peut être utilisé de différentes manières :

1. Spécifier des contraintes de visibilité pour les commandes et fenêtres Outil. Vous pouvez masquer les commandes/outils windows jusqu'à ce que la règle du contexte d’interface utilisateur est remplie.

2. Contraintes de charge en tant qu’automatique : de charge automatique des packages uniquement lorsque la règle est remplie.

3. Comme une tâche différée : retarder le chargement jusqu'à ce qu’un intervalle spécifié écoulé et la règle est toujours respectée.

   Le mécanisme peut être utilisé par n’importe quelle extension de Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Créer un contexte d’interface utilisateur basée sur la règle
 Supposons que vous avez une extension appelée TestPackage, qui offre une commande de menu qui s’applique uniquement aux fichiers avec *.config* extension. Avant de VS2015, la meilleure option a été charger TestPackage lorsque <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> contexte d’interface utilisateur a été activé. Le chargement de TestPackage de cette façon n’est pas efficace, étant donné que la solution chargée ne peut pas contenir de même un *.config* fichier. Ces étapes indiquent le contexte d’interface utilisateur basée sur les règles peuvent être utilisées pour activer un contexte d’interface utilisateur uniquement quand un fichier avec *.config* extension est sélectionné, puis charger TestPackage lorsque ce contexte d’interface utilisateur est activé.

1. Définir un nouveau GUID UIContext et ajouter à la classe VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> et <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.

    Par exemple, supposons un nouveau UIContext « UIContextGuid » doit être ajoutée. Le GUID créé (vous pouvez créer un GUID en cliquant sur **outils** > **créer un GUID**) est « 8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B ». Ensuite, vous ajoutez la déclaration suivante à l’intérieur de votre classe de package :

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Pour les attributs, ajoutez les valeurs suivantes : (Les détails de ces attributs seront expliquées plus loin)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Ces métadonnées définir le nouveau GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) et une expression faisant référence à un terme unique, « DotConfig ». Le terme « DotConfig » a la valeur true lorsque la sélection actuelle dans la hiérarchie active a un nom qui correspond au modèle d’expression régulière «\\.config$ » (se termine par *.config*). La valeur (valeur par défaut) définit un nom facultatif pour la règle utile pour le débogage.

    Les valeurs de l’attribut sont ajoutées à pkgdef généré pendant la génération par la suite.

2. Dans le fichier VSCT pour les commandes de la TestPackage, ajoutez l’indicateur « DynamicVisibility » pour les commandes appropriées :

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. Dans la section de la visibilité de la VSCT, lier les commandes appropriées pour le nouveau UIContext GUID défini dans #1 :

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Dans la section Symbols, ajoutez la définition de la UIContext :

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    À présent, les commandes du menu contextuel pour  *\*.config* fichiers seront visibles uniquement lorsque l’élément sélectionné dans l’Explorateur de solutions est un *.config* fichier et le package ne seront pas chargés tant qu’un de ceux les commandes est activée.

   Ensuite, utilisez un débogueur pour confirmer que le package est chargé uniquement lorsque vous attendez. Pour déboguer TestPackage :

5. Définir un point d’arrêt dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (méthode).

6. Générer le TestPackage et démarrer le débogage.

7. Créez un projet ou ouvrez un.

8. Sélectionnez n’importe quel fichier avec une extension autre que *.config*. Le point d’arrêt ne doit pas être atteint.

9. Sélectionnez le *App.Config* fichier.

   Le TestPackage charge et s’arrête au point d’arrêt.

## <a name="add-more-rules-for-ui-context"></a>Ajouter des règles pour le contexte d’interface utilisateur
 Étant donné que les règles de contexte d’interface utilisateur sont des expressions booléennes, vous pouvez ajouter des règles plus restreintes pour un contexte d’interface utilisateur. Par exemple, dans le contexte de l’interface utilisateur ci-dessus, vous pouvez spécifier que la règle s’applique uniquement quand une solution avec un projet est chargée. De cette façon, les commandes ne s’afficheront si vous ouvrez un *.config* fichier comme un fichier autonome, et non comme partie d’un projet.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Maintenant l’expression fait référence à trois termes. Les deux premiers termes, « SingleProject » et « MultipleProjects », font référence à d’autres contextes d’interface utilisateur bien connue (par leurs GUID). Le troisième « DotConfig » est le contexte d’interface utilisateur de base de règles définis précédemment dans cet article.

## <a name="delayed-activation"></a>Délai d’activation
 Règles peuvent avoir un délai « facultatif ». Le délai spécifié en millisecondes. Le cas échéant, le délai provoque l’activation ou la désactivation de contexte d’interface utilisateur d’une règle peut être différé par cet intervalle de temps. Si les modifications de règle au avant l’intervalle du délai, puis rien ne se produit. Ce mécanisme peut être utilisé pour « échelonner les étapes d’initialisation - en particulier l’initialisation unique sans s’appuyer sur les minuteurs ou de l’inscription aux notifications inactives ».

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

Voici les différents types de terme qui sont prises en charge :

|Terme|Description|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Le GUID fait référence à un contexte d’interface utilisateur. Le terme sera true chaque fois que le contexte de l’interface utilisateur est active et false sinon.|
|HierSingleSelectionName:\<pattern>|Le terme sera true chaque fois que la sélection dans la hiérarchie active est un élément unique et le nom de l’élément sélectionné correspond à l’expression régulière .net donnée par « pattern ».|
|UserSettingsStoreQuery:\<query>|« query » représente un chemin d’accès complet dans la banque de paramètres utilisateur, qui doit correspondre à une valeur différente de zéro. La requête est divisée en une « collection » et le « propertyName » à la dernière barre oblique.|
|ConfigSettingsStoreQuery:\<query>|« query » représente un chemin d’accès complet dans le magasin de paramètres de configuration, qui doit correspondre à une valeur différente de zéro. La requête est divisée en une « collection » et le « propertyName » à la dernière barre oblique.|
|ActiveProjectFlavor:\<projectTypeGuid>|Le terme sera true chaque fois que le projet actuellement sélectionné est versionné (agrégé) et a une version de mise en correspondance du GUID du type de projet donné.|
|ActiveEditorContentType:\<contentType>|Le terme aura la valeur true lorsque le document sélectionné est un éditeur de texte avec le type de contenu donné.|
|ActiveProjectCapability :\<Expression >|Le terme est true lorsque les fonctionnalités de projet actif correspond à l’expression fournie. Une expression peut être quelque chose comme VB &#124; CSharp.|
|SolutionHasProjectCapability :\<Expression >|Similaire à ci-dessus mais terme a la valeur true lorsque la solution a n’importe quel projet chargé qui correspond à l’expression.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Le terme sera true chaque fois qu’une solution de projet qui est versionnés (agrégé) et a une version de mise en correspondance du GUID du type de projet donné.|
|ProjectAddedItem :\<modèle >| Le terme est vrai lorsqu’un fichier correspondant au modèle « » est ajouté à un projet dans le soluion est ouvert.|
|ActiveProjectOutputType:\<outputType>|Le terme a la valeur true de sortie lorsque le type de projet actif correspond exactement.  OutputType peut être un entier ou un <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> type.|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|Le terme a la valeur true lorsque le projet actif a la propriété de build spécifiée et la valeur de propriété correspond au filtre d’expression régulière fournie. Reportez-vous à [persistance des données dans les fichiers projet MSBuild](internals/persisting-data-in-the-msbuild-project-file.md) pour plus d’informations sur les propriétés de build.|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|Le terme est true lorsque la solution a un projet chargé avec la propriété de build spécifiée et la valeur de propriété correspond au filtre d’expression régulière fournie.|

## <a name="compatibility-with-cross-version-extension"></a>Compatibilité avec l’extension d’entre versions

Contextes d’interface utilisateur basée sur la règle est une nouvelle fonctionnalité dans Visual Studio 2015 et ne serait pas être déplacée vers les versions antérieures. Ne pas de portage vers des versions antérieures crée un problème avec les extensions/packages qui ciblent plusieurs versions de Visual Studio. Ces versions doivent être chargées automatiquement dans Visual Studio 2013 et versions antérieures, mais peuvent tirer parti des contextes d’interface utilisateur basée sur la règle afin d’éviter d’être chargées automatiquement dans Visual Studio 2015.

Pour prendre en charge ces packages, AutoLoadPackages dans le Registre peuvent maintenant fournir un indicateur dans son champ de valeur pour indiquer que l’entrée doit être ignorée dans Visual Studio 2015 et versions ultérieures. Cela est possible en ajoutant une option d’indicateurs pour <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Les VSPackages peuvent maintenant ajouter **SkipWhenUIContextRulesActive** option leurs <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attribut pour indiquer l’entrée doit être ignorée dans Visual Studio 2015 et versions ultérieures.
## <a name="extensible-ui-context-rules"></a>Règles de contexte d’interface utilisateur extensibles

Parfois, les packages ne pouvez pas utiliser les règles de contexte d’interface utilisateur statiques. Par exemple, supposons que vous disposez d’un package prenant en charge d’extensibilité, telles que l’état de la commande est basée sur les types d’éditeur qui sont pris en charge par les fournisseurs MEF importés. La commande est activée s’il existe une extension prenant en charge le type de modification actuelle. Dans ce cas, le package lui-même ne peut pas utiliser une règle de contexte d’interface utilisateur statique, dans la mesure où les termes du contrat pourrait être modifié selon le MEF extensions sont disponibles.

Pour prendre en charge ces packages, contextes d’interface utilisateur basée sur la règle prend en charge une expression codée en dur « * » qui indique tous les termes ci-dessous il sera joint avec ou. Ainsi, le package principal définir un contexte d’interface utilisateur basée sur la règle connus et de lier son état de la commande à ce contexte. Par la suite n’importe quelle extension MEF ciblée pour le package principal peut ajouter ses termes du contrat pour les éditeurs, qu'il prend en charge sans affecter les autres conditions ou l’expression de référence.

Le constructeur <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> documentation illustre la syntaxe pour les règles de contexte d’interface utilisateur extensibles.
