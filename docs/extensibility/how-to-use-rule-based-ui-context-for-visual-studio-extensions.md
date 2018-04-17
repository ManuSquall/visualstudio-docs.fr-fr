---
title: 'Comment : utiliser le contexte de l’interface utilisateur basée sur une règle pour les Extensions Visual Studio | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 8597c413c899b54e61e848649c3c524cbdb20724
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Comment : utiliser le contexte de l’interface utilisateur basée sur une règle pour les Extensions Visual Studio
Visual Studio permet le chargement des VSPackages lorsque certaines connue <xref:Microsoft.VisualStudio.Shell.UIContext>s sont activés. Toutefois, les contextes d’interface utilisateur ne sont pas très fines précise, en laissant auteurs d’extensions aucun choix mais permettant de sélectionner un contexte de l’interface utilisateur disponibles qui active avant le point, ils voulaient réellement le VSPackage à charger. Pour obtenir la liste des contextes d’interface utilisateur bien connus, consultez <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Le chargement de packages peut avoir un impact sur les performances et de leur chargement plus tôt qu’ils sont requis n’est pas la meilleure pratique. Visual Studio 2015 a introduit le concept de contextes d’interface utilisateur basée sur des règles, un mécanisme qui permet aux auteurs d’extension définir les conditions précises sous lequel un contexte de l’interface utilisateur est activé et chargé de VSPackages associés.  
  
## <a name="rule-based-ui-context"></a>Contexte de l’interface utilisateur basée sur la règle  
 Une « règle » se compose d’un nouveau contexte de l’interface utilisateur (GUID) et une expression booléenne qui fait référence à un ou plusieurs « termes » combiné avec logique « et », « ou », « not » des opérations. « Termes » sont dynamiquement évaluées lors de l’exécution et l’expression est réévaluée chaque fois qu’une de ses modifications termes du contrat. Lorsque l’expression a la valeur true, le contexte de l’interface utilisateur associée est activé. Sinon, le contexte de l’interface utilisateur est désactivé.  
  
 Basée sur une règle de contexte de l’interface utilisateur peut être utilisé de plusieurs façons :  
  
1.  Spécifier des contraintes de visibilité pour les commandes et les fenêtres Outil. Vous pouvez masquer les commandes/outils windows jusqu'à ce que la règle du contexte de l’interface utilisateur est remplie.  
  
2.  Contraintes de charge en tant qu’automatique : de charge automatique des packages uniquement lorsque la règle est remplie.  
  
3.  Tâche différée : retarder le chargement jusqu'à ce qu’un intervalle spécifié est écoulé et la règle est toujours respectée.  
  
 Le mécanisme peut être utilisé par n’importe quelle extension de Visual Studio.  
  
## <a name="create-a-rule-based-ui-context"></a>Créer un contexte de l’interface utilisateur basée sur la règle  
 Supposons que vous disposez d’une extension appelée TestPackage, qui offre une commande de menu qui s’applique uniquement aux fichiers avec l’extension de « .config ». Avant de VS2015, la meilleure option a été charger TestPackage lorsque <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> contexte d’interface utilisateur a été activé. Ceci n’est pas efficace, car la solution chargée ne contienne pas même un fichier .config. Nous voir comment basée sur les règles de contexte de l’interface utilisateur peut être utilisé pour activer un contexte d’interface utilisateur uniquement lorsqu’un fichier avec une extension .config est sélectionné et charger TestPackage lorsque ce contexte de l’interface utilisateur est activé.  
  
1.  Définir un nouveau GUID UIContext et ajouter à la classe VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> et <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
     Par exemple, supposons un nouveau UIContext « UIContextGuid » doit être ajouté. Le GUID créé (vous pouvez créer un GUID en cliquant sur Outils -> créer un guid) est « 8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B ». Vous ajoutez ensuite le code suivant à l’intérieur de votre classe de package :  
  
    ```csharp  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Pour les attributs, ajoutez le code suivant : (les détails de ces attributs seront abordées plus loin)  
  
    ```csharp  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Ces métadonnées définir le nouveau GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) et une expression faisant référence à un terme unique, « DotConfig ». Le terme « DotConfig » a la valeur true lorsque la sélection actuelle dans la hiérarchie active porte un nom qui correspond au modèle d’expression régulière «\\.config$ » (qui se termine par « .config »). La valeur (valeur par défaut) définit un nom pour la règle utile pour le débogage.  
  
     Les valeurs de l’attribut sont ajoutées au pkgdef généré pendant le moment de la génération par la suite.  
  
2.  Dans le fichier VSCT pour les commandes de la TestPackage, ajoutez l’indicateur « DynamicVisibility » pour les commandes appropriées :  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  Dans la section de la visibilité de la VSCT, lier les commandes appropriées pour le nouveau UIContext GUID défini dans #1 :  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  Dans la section de symboles, ajoutez la définition de la UIContext :  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     Désormais, les commandes de menu contextuel pour les fichiers *.config sera visibles uniquement lorsque l’élément sélectionné dans l’Explorateur de solutions est un fichier de « .config » et le package ne sera pas chargé tant qu’un de ces commandes est sélectionné.  
  
 Ensuite, nous allons utiliser un débogueur pour confirmer que le package est chargé uniquement quand nous prévu. Pour déboguer TestPackage :  
  
1.  Définir un point d’arrêt dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (méthode).  
  
2.  Générer le TestPackage et démarrer le débogage.  
  
3.  Créez un projet ou ouvrez un.  
  
4.  Sélectionnez un fichier avec une extension autre que .config. Le point d’arrêt ne doit pas être atteint.  
  
5.  Sélectionnez le fichier App.Config.  
  
 Le TestPackage charge et s’arrête au point d’arrêt.  
  
## <a name="adding-more-rules-for-ui-context"></a>Ajout de plusieurs règles pour le contexte de l’interface utilisateur  
 Étant donné que les règles de contexte d’interface utilisateur sont des expressions booléennes, vous pouvez ajouter des règles plus restreintes pour un contexte de l’interface utilisateur. Par exemple, dans le contexte de l’interface utilisateur ci-dessus, vous pouvez spécifier que la règle s’applique uniquement lorsqu’une solution avec un projet est chargée. De cette façon, les commandes n’apparaîtront pas si vous ouvrez un fichier de « .config » en tant que fichier autonome, et non comme partie d’un projet.  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Maintenant, l’expression fait référence à trois termes. Les deux premiers termes du contrat, « SingleProject » et « MultipleProjects », faire référence à d’autres contextes d’interface utilisateur bien connu (par leur GUID). Le terme, « DotConfig » est le contexte de l’interface utilisateur basée sur une règle définie précédemment.  
  
## <a name="delayed-activation"></a>Délai d’Activation  
 Les règles peuvent avoir un délai « facultatif ». Le délai d’attente est spécifié en millisecondes. Le cas échéant, le délai d’attente entraîne l’activation ou la désactivation du contexte de l’interface utilisateur d’une règle peut être différé par cet intervalle de temps. Si les modifications de règle sauvegarder avant l’intervalle de délai, puis rien ne se produit. Ce mécanisme permet de « échelonner les étapes d’initialisation - en particulier une initialisation unique sans compter sur les minuteurs ou inscription aux notifications inactives ».  
  
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
 Voici les différents types de termes qui sont prises en charge :  
  
|||  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Le GUID fait référence à un contexte de l’interface utilisateur. Chaque fois que le contexte de l’interface utilisateur est actif et false dans le cas contraire, le terme sera true.|  
|HierSingleSelectionName :\<modèle >|Le terme sera true chaque fois que la sélection dans la hiérarchie active est un élément unique et le nom de l’élément sélectionné correspond à l’expression régulière .net donnée par « pattern ».|  
|UserSettingsStoreQuery :\<requête >|« requête » représente un chemin d’accès complet dans le magasin de paramètres utilisateur qui doit correspondre à une valeur différente de zéro. La requête est fractionnée en « collection » et « propertyName » à la dernière barre oblique.|  
|ConfigSettingsStoreQuery :\<requête >|« requête » représente un chemin d’accès complet dans le magasin de paramètres de configuration qui doit correspondre à une valeur différente de zéro. La requête est fractionnée en « collection » et « propertyName » à la dernière barre oblique.|  
|ActiveProjectFlavor :\<projectTypeGuid >|La durée de true à chaque fois que le projet sélectionné actuellement est flavored (agrégé) et a une version de mise en correspondance du GUID du type de projet donné.|  
|ActiveEditorContentType :\<contentType >|Le terme aura la valeur true lorsque le document sélectionné est un éditeur de texte avec le type de contenu donné.|  
|ActiveProjectCapability :\<Expression >|Le terme a la valeur true lorsque les fonctionnalités de projet actif correspond à l’expression fournie. Une expression peut être un nom tel que VB &#124; CSharp|  
|SolutionHasProjectCapability :\<Expression >|Similaire à ce qui précède, mais terme a la valeur true lorsque la solution a un projet chargé qui correspond à l’expression.|  
|SolutionHasProjectFlavor :\<projectTypeGuid >|Le terme sera true chaque fois qu’une solution de projet qui est flavored (agrégé) et a une version de mise en correspondance du GUID du type de projet donné.|


  
## <a name="compatibility-with-cross-version-extension"></a>Compatibilité avec les extension entre les versions  
 La règle en fonction des contextes de l’interface utilisateur est une nouvelle fonctionnalité dans Visual Studio 2015 et ne serait pas être déplacée vers les versions antérieures. Cela crée un problème avec les extensions/packages qui ciblent plusieurs versions de Visual Studio qui doivent être chargés automatiquement dans Visual Studio 2013 et versions antérieures, mais qui peuvent tirer parti de contextes d’interface utilisateur basé sur une règle afin d’éviter d’être chargé automatiquement dans Visual Studio 2015.  
  
 Pour prendre en charge ces packages, AutoLoadPackages dans le Registre peuvent maintenant fournir un indicateur dans son champ de valeur pour indiquer que l’entrée doit être ignorée dans Visual Studio 2015 et versions ultérieures. Cela est possible en ajoutant une option d’indicateurs pour <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Les VSPackages peuvent maintenant ajouter **SkipWhenUIContextRulesActive** option leurs <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attribut pour indiquer l’entrée doit être ignorée dans Visual Studio 2015 et versions ultérieures.  
  
## <a name="extensible-ui-context-rules"></a>Règles de contexte de l’interface utilisateur extensible  
 Parfois, les packages ne pouvez pas utiliser les règles de contexte de l’interface utilisateur statiques. Par exemple, supposons que vous avez un package d’extensibilité de la prise en charge telles que l’état de la commande est basée sur les types de l’éditeur qui sont pris en charge par les fournisseurs MEF importés. La commande est activée s’il existe une prise en charge le type de modification en cours d’extension. Dans ce cas le package lui-même ne peut pas utiliser une règle de contexte de l’interface utilisateur statique, étant donné que les termes du contrat pourrait être modifié selon le MEF extensions sont disponibles.  
  
 Pour prendre en charge ces packages, les contextes d’interface utilisateur basé sur une règle prend en charge une expression codé en dur « * » qui indique tous les termes ci-dessous il sera joint à ou. Cela permet le package principal définir une règle connue en fonction de contexte de l’interface utilisateur et lier son état de commande pour ce contexte. Par la suite n’importe quelle extension MEF ciblée pour le package principal peut ajouter ses conditions d’utilisation des éditeurs, qu'il prend en charge sans affecter les autres conditions ou l’expression de référence.  
  
 Le constructeur <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> de documentation illustre la syntaxe pour les règles de contexte de l’interface utilisateur extensibles.