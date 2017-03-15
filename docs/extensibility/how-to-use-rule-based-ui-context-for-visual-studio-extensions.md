---
title: "Comment&#160;: utiliser le contexte de l’interface utilisateur bas&#233;e sur la r&#232;gle des Extensions Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 7
ms.author: "gregvanl"
caps.handback.revision: 7
---
# Comment&#160;: utiliser le contexte de l’interface utilisateur bas&#233;e sur la r&#232;gle des Extensions Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio permet de charger des VSPackages lorsque certains connu <xref:Microsoft.VisualStudio.Shell.UIContext>s sont activés. Toutefois, les contextes d’interface utilisateur ne sont pas très grains, ne laissant les auteurs d’extensions aucun choix mais permettant de sélectionner un contexte de l’interface utilisateur disponible qui active avant le point, ils voulaient réellement le VSPackage à charger. Pour obtenir la liste des contextes d’interface utilisateur bien connus, consultez <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Le chargement de packages peut avoir un impact sur les performances et leur chargement plus tôt qu’ils sont requis n’est pas la meilleure pratique. Visual Studio 2015 introduit le concept de contextes d’interface utilisateur basée sur des règles, un mécanisme qui permet aux auteurs d’extension définir les conditions précises sous lequel un contexte de l’interface utilisateur est activé et chargé VSPackages associés.  
  
## Contexte de l’interface utilisateur basée sur la règle  
 Une « règle » se compose d’un nouveau contexte de l’interface utilisateur \(GUID\) et une expression booléenne qui fait référence à un ou plusieurs « termes » associé logique « et », « or » et « non » les opérations. « Termes » sont évalués dynamiquement lors de l’exécution et l’expression est réévaluée à chaque fois que des modifications de son contrat. Lorsque l’expression prend la valeur true, le contexte de l’interface utilisateur associée est activé. Sinon, le contexte de l’interface utilisateur est désactivé.  
  
 Basée sur des règles de contexte de l’interface utilisateur peut être utilisé de plusieurs façons :  
  
1.  Spécifier des contraintes de visibilité pour les commandes et les fenêtres Outil. Vous pouvez masquer les commandes\/outils windows jusqu'à ce que la règle du contexte de l’interface utilisateur est remplie.  
  
2.  Charger des contraintes comme automatique : de charge automatique des packages uniquement lorsque la règle est remplie.  
  
3.  Tâche différée : retarder le chargement jusqu'à ce qu’un intervalle spécifié est écoulé et que la règle est toujours respectée.  
  
 Le mécanisme peut être utilisé par n’importe quelle extension de Visual Studio.  
  
## Créer un contexte de l’interface utilisateur basée sur la règle  
 Si que vous avez une extension appelée TestPackage, qui offre une commande de menu qui s’applique uniquement aux fichiers avec l’extension « .config ». Avant de VS2015, a été la meilleure option pour charger TestPackage lorsque <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> contexte d’interface utilisateur a été activé. Cela n’est pas efficace, puisque la solution chargée ne contienne pas même un fichier .config. Nous voir comment le contexte de l’interface utilisateur basée sur des règles peut être utilisé pour activer un contexte d’interface utilisateur uniquement lorsqu’un fichier avec l’extension .config est sélectionné et charger TestPackage lorsque ce contexte de l’interface utilisateur est activé.  
  
1.  Définir un nouveau GUID UIContext et ajouter à la classe VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> et <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
     Par exemple, supposons qu’un nouveau UIContext « UIContextGuid » doit être ajouté. Le GUID créé \(vous pouvez créer un GUID en cliquant sur Outils \-\> créer un guid\) est « 8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B ». Vous ajoutez ensuite le code suivant à l’intérieur de votre classe de package :  
  
    ```c#  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Pour les attributs, ajoutez le code suivant : \(les détails de ces attributs seront décrite ultérieurement\)  
  
    ```c#  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Ces métadonnées définir le nouveau GUID UIContext \(8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B\) et une expression faisant référence à un terme unique, « DotConfig ». Le terme « DotConfig » a la valeur true lorsque la sélection actuelle dans la hiérarchie active a un nom qui correspond au modèle d’expression régulière « \\.config$ » \(se termine par « .config »\). La valeur \(par défaut\) définit un nom facultatif pour la règle utile pour le débogage.  
  
     Les valeurs de l’attribut sont ajoutées à pkgdef générée au moment de la génération par la suite.  
  
2.  Dans le fichier VSCT pour les commandes de la TestPackage, ajoutez l’indicateur « DynamicVisibility » pour les commandes appropriées :  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  Dans la section de la visibilité de la VSCT, lier les commandes appropriées pour le nouveau UIContext GUID défini dans \#1 :  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  Dans la section de symboles, ajoutez la définition de la UIContext :  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     À présent, les commandes de menu contextuel pour les fichiers \*.config sera visibles uniquement lorsque l’élément sélectionné dans l’Explorateur de solutions est un fichier « .config » et le package ne sera pas chargé tant qu’un de ces commandes est sélectionné.  
  
 Ensuite, nous allons utiliser un débogueur pour vérifier que le package est chargé lorsque nous attendons uniquement à. Pour déboguer TestPackage :  
  
1.  Définir un point d’arrêt dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> \(méthode\).  
  
2.  Générez le TestPackage et démarrer le débogage.  
  
3.  Créez un projet ou ouvrez un.  
  
4.  Sélectionnez un fichier avec une extension autre que .config. Le point d’arrêt ne doit pas être atteint.  
  
5.  Sélectionnez le fichier App.Config.  
  
 Le TestPackage se charge et s’arrête au point d’arrêt.  
  
## Ajout de plusieurs règles pour le contexte de l’interface utilisateur  
 Étant donné que les règles de contexte de l’interface utilisateur sont des expressions booléennes, vous pouvez ajouter des règles plus restreints pour un contexte de l’interface utilisateur. Par exemple, dans le contexte de l’interface utilisateur ci\-dessus, vous pouvez spécifier que la règle s’applique uniquement lorsqu’une solution avec un projet est chargée. De cette façon, les commandes n’apparaîtront pas si vous ouvrez un fichier « .config » en tant que fichier autonome, pas dans le cadre d’un projet.  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Désormais, l’expression fait référence à trois termes. Les deux premières conditions, « SingleProject » et « MultipleProjects », reportez\-vous aux autres contextes d’interface utilisateur bien connu \(par GUID\). Le troisième « DotConfig » est le contexte de l’interface utilisateur basée sur une règle définie précédemment.  
  
## Délai d’Activation  
 Elles peuvent disposer d’un délai « facultatif ». Le délai est exprimé en millisecondes. Le cas échéant, le délai entraîne l’activation ou la désactivation du contexte de l’interface utilisateur d’une règle pour être retardé de cet intervalle de temps. Si les modifications de règle dans avant l’intervalle de délai, puis rien ne se produit. Ce mécanisme peut servir à « échelonner les étapes d’initialisation \- en particulier l’initialisation unique sans compter sur les minuteurs ou l’inscription aux notifications inactives ».  
  
 Par exemple, vous pouvez spécifier votre règle de charge de test pour avoir un délai de 100 millisecondes :  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## Types de terme  
 Voici les différents types de terme qui sont prises en charge :  
  
|||  
|-|-|  
|{nnnnnnnn\-nnnn\-nnnn\-nnnn\-nnnnnnnnnnnn}|Le GUID fait référence à un contexte de l’interface utilisateur. Chaque fois que le contexte de l’interface utilisateur est actif et false dans le cas contraire, le terme est vrai.|  
|HierSingleSelectionName : \< modèle \>|Le terme aura la valeur true lorsque la sélection dans la hiérarchie active est un élément unique et le nom de l’élément sélectionné correspond à l’expression régulière .net donnée par « modèle ».|  
|UserSettingsStoreQuery : \< query \>|« requête » représente un chemin d’accès complet dans le magasin de paramètres utilisateur qui doit correspondre à une valeur différente de zéro. La requête est fractionnée en « collection » et « propertyName » à la dernière barre oblique.|  
|ConfigSettingsStoreQuery : \< query \>|« requête » représente un chemin d’accès complet dans le magasin de paramètres de configuration qui doit correspondre à une valeur différente de zéro. La requête est fractionnée en « collection » et « propertyName » à la dernière barre oblique.|  
|ActiveProjectFlavor : \< projectTypeGuid \>|Le terme sera true chaque fois que le projet sélectionné actuellement est versionné \(agrégé\) et a une version de mise en correspondance du GUID du type de projet donné.|  
|ActiveEditorContentType : \< contentType \>|Le terme aura la valeur true lorsque le document sélectionné est un éditeur de texte avec le type de contenu.|  
|ActiveProjectCapability : \< Expression \>|Le terme est true lorsque les fonctionnalités du projet actif correspond à l’expression fournie. Une expression peut être quelque chose comme VB &#124; CSharp|  
|SolutionHasProjectCapability : \< Expression \>|Similaire aux ci\-dessus, mais terme est true lorsque la solution a n’importe quel projet chargé qui correspond à l’expression.|  
  
## Compatibilité entre les versions extension  
 La règle en fonction de contextes d’interface utilisateur est une nouvelle fonctionnalité dans Visual Studio 2015 et ne serait pas être déplacée vers les versions antérieures. Cela crée un problème avec les extensions\/packages qui ciblent plusieurs versions de Visual Studio qui doivent être chargées automatiquement dans Visual Studio 2013 et versions antérieures, mais peuvent tirer parti de contextes d’interface utilisateur basé sur une règle pour empêcher d’être chargées automatiquement dans Visual Studio 2015.  
  
 Pour prendre en charge ces packages, AutoLoadPackages dans le Registre peuvent maintenant fournir un indicateur dans son champ de valeur pour indiquer que l’entrée doit être ignorée dans Visual Studio 2015 et versions ultérieures. Cela est possible en ajoutant une option d’indicateurs à <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Les VSPackages peuvent maintenant ajouter **SkipWhenUIContextRulesActive** option leurs <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attribut pour indiquer l’entrée doit être ignorée dans Visual Studio 2015 et versions ultérieures.  
  
## Règles de contexte de l’interface utilisateur extensible  
 Parfois, les packages Impossible d’utiliser les règles de contexte de l’interface utilisateur statiques. Par exemple, supposons que vous disposez d’un package d’extensibilité de la prise en charge telles que l’état de la commande est basé sur les types d’éditeur qui sont pris en charge par les fournisseurs de MEF importés. La commande est activée s’il existe une prise en charge le type de modification en cours d’extension. Dans ce cas le package lui\-même ne peut pas utiliser une règle de l’interface utilisateur contexte statique, étant donné que les termes du contrat pourrait être modifié selon le MEF extensions sont disponibles.  
  
 Pour prendre en charge ces packages, les contextes d’interface utilisateur basé sur une règle prend en charge une expression codé en dur « \* » qui indique tous les termes ci\-dessous appartiendront avec ou. Cela permet le package principal définir une règle connue en fonction de contexte de l’interface utilisateur et lier son état de commande pour ce contexte. Par la suite n’importe quelle extension MEF ciblée pour le package principal peut ajouter ses conditions pour les éditeurs, qu'il prend en charge sans affecter d’autres conditions ou l’expression de référence.  
  
 Le constructeur <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> documentation illustre la syntaxe pour les règles de contexte de l’interface utilisateur extensibles.