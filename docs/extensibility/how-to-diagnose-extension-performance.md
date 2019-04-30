---
title: 'Procédure : Diagnostiquer les performances de l’extension | Microsoft Docs'
ms.date: 11/08/2016
ms.topic: conceptual
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 3d8fb5de23cbc4664ea322a9149653598956aed7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863290"
---
# <a name="measuring-extension-impact-in-startup"></a>Mesurer l’impact d’extension dans le démarrage

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Vous concentrer sur les performances des extensions dans Visual Studio 2017

En fonction des commentaires des clients, les zones de focus pour la version de Visual Studio 2017 a été performances de chargement de solution et de démarrage. En tant que l’équipe de plateforme Visual Studio, nous avons travaillé sur l’amélioration des performances de chargement de solution et de démarrage. En règle générale, nos mesures suggèrent extensions installées peuvent avoir également un impact considérable sur ces scénarios.

Pour aider les utilisateurs à comprendre cet impact, nous avons ajouté une nouvelle fonctionnalité dans Visual Studio pour informer les utilisateurs des extensions lentes. Parfois, Visual Studio détecte une nouvelle extension ralentit le chargement de solution ou de démarrage. Lorsqu’un ralentissement est détecté, les utilisateurs verront une notification dans l’IDE pointées vers la nouvelle boîte de dialogue « Gérer les performances de Visual Studio ». Cette boîte de dialogue est également toujours accessible par le menu d’aide pour parcourir les extensions détectées précédemment.

![gérer les performances de Visual Studio](media/manage-performance.png)

Ce document vise à aider les développeurs d’extensions en décrivant la façon dont l’impact de l’extension est calculée. Ce document décrit également comment impact d’extension peut être analysé localement. Analyse de localement l’impact de l’extension détermine si une extension peut-être s’afficher comme une extension d’ayant un impact sur des performances.

> [!NOTE]
> Ce document se concentre sur l’impact des extensions lors du chargement de solution et de démarrage. Extensions également avoir un impact sur les performances de Visual Studio lorsqu’elles entraînent l’interface utilisateur de ne plus répondre. Pour plus d’informations sur ce sujet, consultez [Comment : L’interface utilisateur de diagnostiquer des retards causés par les extensions](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Impact par des extensions du démarrage

Une des méthodes plus courantes pour les extensions à avoir un impact sur les performances de démarrage est en choisissant de charge automatique à un des contextes d’interface utilisateur démarrage connus tels que NoSolutionExists ou ShellInitialized. Ces contextes d’interface utilisateur être activés lors du démarrage. Tous les packages qui incluent le `ProvideAutoLoad` attribut dans leur définition avec ces contextes est chargé et initialisé à ce moment-là.

Lorsque nous évaluons l’impact d’une extension, nous mettons l’accent sur le temps passé par ces extensions choisir de chargement automatique dans les contextes ci-dessus. Mesuré fois seraient incluent, mais se limite ne pas à :

* Chargement des assemblys d’extension pour les packages synchrones
* Temps passé dans le constructeur de classe de package pour les packages synchrones
* Temps passé dans la méthode Initialize (ou SetSite) de package pour les packages synchrones
* Pour les packages asynchrones, les opérations ci-dessus s’exécuter sur le thread d’arrière-plan.  Par conséquent, les opérations sont exclues de l’analyse.
* Temps passé dans n’importe quel travail asynchrone planifiée pendant l’initialisation du package pour s’exécuter sur le thread principal
* Temps passé dans les gestionnaires d’événements, en particulier l’activation de contexte shell initialisé ou la modification d’état zombie shell
* À partir de Visual Studio 2017 Update 3, nous allons également commencer analyse le temps passé dans lors des appels d’inactivité avant l’initialisation de shell. Les opérations longues dans les gestionnaires d’inactivité également provoquent l’IDE ne répond pas et contribuent au temps de démarrage perçu par l’utilisateur.

Nous avons ajouté de nombreuses fonctionnalités à partir de Visual Studio 2015. Ces fonctionnalités permettent de supprimer la nécessité pour les packages à charge d’automatique. Les fonctionnalités de reporter également la nécessité de packages pour charger des cas plus spécifiques. Ces cas incluent des exemples où les utilisateurs peuvent y à utiliser l’extension ou réduire un impact de l’extension lors du chargement automatiquement.

Vous trouverez plus d’informations sur ces fonctionnalités dans les documents suivants :

[Contextes d’interface utilisateur basée sur la règle](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): Un moteur basé sur une règle plus riche construit autour des contextes d’interface utilisateur vous permet de créer des contextes personnalisés basés sur les attributs, les versions et les types de projets. Contextes personnalisés peuvent être utilisés pour charger un package lors de scénarios plus spécifiques. Ces scénarios spécifiques incluent la présence d’un projet avec une fonctionnalité spécifique au lieu de démarrage. Les contextes personnalisés permettent également [commande visibilité d’être associé à un contexte personnalisé](visibilityconstraints-element.md) basé sur les composants d’un projet ou d’autres termes disponibles. Cette fonctionnalité élimine la nécessité de charger un package pour inscrire un gestionnaire de requête de statut de commande.

[Prise en charge asynchrone package](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): La nouvelle classe de base AsyncPackage dans Visual Studio 2015 permet des packages Visual Studio à charger dans l’arrière-plan de façon asynchrone si le chargement du package a été demandé par un attribut de charge automatique ou d’une requête de service asynchrone. Ce chargement en arrière-plan permet à l’IDE de rester réactive. L’IDE est réactif pendant que l’extension est initialisée en arrière-plan et des scénarios critiques comme charge de démarrage et de la solution ne sont pas affectées.

[Les services asynchrones](how-to-provide-an-asynchronous-visual-studio-service.md): Avec prise en charge asynchrone de package, nous avons également ajouté de prise en charge de l’interrogation des services de façon asynchrone et ne pourrez plus inscrire les services asynchrones. Plus important encore, nous travaillons sur la conversion des services de Visual Studio core pour prendre en charge de la requête asynchrone afin que la majorité du travail dans une requête asynchrone se produit dans les threads d’arrière-plan. SComponentModel (hôte de MEF de Visual Studio) est un des principaux services qui prend désormais en charge une requête asynchrone pour autoriser les extensions prendre en charge le chargement asynchrone complètement.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Réduisant l’impact des auto extensions chargées

Si un package doit toujours être automatiquement chargé au démarrage, il est important de réduire le travail effectué pendant l’initialisation du package. En réduisant le travail de l’initialisation du package permet de réduire les risques de l’extension ayant un impact sur démarrage.

Quelques exemples qui pourrait s’avérer coûteuse de l’initialisation de package sont :

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Utilisation de chargement du package synchrone au lieu de chargement du package asynchrone

Étant donné que les packages synchrones sont chargés sur le thread principal par défaut, nous encourageons les propriétaires d’extension qui ont chargé automatiquement les packages à utiliser la classe de base du package asynchrone au lieu de cela comme mentionné précédemment. Modification d’un package chargé automatiquement pour prendre en charge le chargement asynchrone également rend plus facile à résoudre les problèmes ci-dessous.

### <a name="synchronous-filenetwork-io-requests"></a>Demandes d’e/s de fichier synchrones/réseau

Dans l’idéal, toute demande d’e/s réseau ou de fichier synchrone doit être évitée dans le thread principal. Leur impact varie selon l’état de l’ordinateur et peut bloquer pendant de longues périodes de temps dans certains cas.

À l’aide de chargement du package asynchrone et les API d’e/s asynchrones devez vous assurer que l’initialisation de package ne bloque pas le thread principal dans de tels cas. Les utilisateurs peuvent également continuer à interagir avec Visual Studio, tandis que les demandes d’e/s se produisent en arrière-plan.

### <a name="early-initialization-of-services-components"></a>Initialisation anticipée des services, composants

Un des modèles courants dans l’initialisation des packages consiste à initialiser les services fournis par ce package dans le package soit utilisé par `constructor` ou `initialize` (méthode). Bien que cela garantit que les services sont prêtes à être utilisées, il peut également ajouter les coûts inutiles pour empaqueter le chargement si ces services ne servent pas immédiatement. Au lieu de cela, ces services doivent être initialisés à la demande afin de minimiser le travail effectué dans l’initialisation des packages.

Pour les services globaux fournis par un package, vous pouvez utiliser `AddService` méthodes qui prennent une fonction pour initialiser tardivement le service uniquement lorsque cela est demandé par un composant. Pour les services utilisés dans le package, vous pouvez utiliser le mode différé\<T > ou AsyncLazy\<T > pour vous assurer que les services sont initialisés ou interrogée à la première utilisation.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Mesurer l’impact auto chargé des extensions à l’aide du journal d’activité

À compter de Visual Studio 2017 Update 3, journal d’activité de Visual Studio maintenant contient des entrées pour l’impact sur les performances des packages au cours du chargement de solution et de démarrage. Pour afficher ces mesures, vous devez ouvrir Visual Studio avec le commutateur /log et ouvrez *ActivityLog.xml* fichier.

Dans le journal d’activité, les entrées se trouvent sous la source de « Gérer les performances de Visual Studio » et ressemblent à l’exemple suivant :

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Cet exemple montre qu’un package avec le GUID « 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c » passé à 2008 ms dans le démarrage de Visual Studio. Notez que Visual Studio prend en compte coût de niveau supérieur comme numéro principal lors du calcul de l’impact d’un package car ce serait que les utilisateurs d’économies voient quand ils désactivent l’extension de ce package.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Mesurer l’impact auto chargé des extensions à l’aide de PerfView

Bien que l’analyse du code permet d’identifier les chemins de code qui peuvent ralentir l’initialisation des packages, vous pouvez également utiliser le suivi à l’aide d’applications telles que PerfView pour comprendre l’impact d’une charge de package dans le démarrage de Visual Studio.

PerfView est un outil de suivi de l’échelle du système. Cet outil vous aidera à comprendre les chemins d’accès à chaud dans une application en raison de l’utilisation du processeur ou de blocage d’appels système. Voici un exemple rapide sur l’analyse d’un exemple d’extension à l’aide de PerfView disponible à la [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Exemple de code :**

Cet exemple est basé sur l’exemple de code ci-dessous, qui est conçu pour afficher les cas certaines causes courantes de délai :

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**Enregistrement d’une trace avec PerfView :**

Une fois que vous définissez votre environnement Visual Studio avec votre extension installée, vous pouvez enregistrer une trace de démarrage en ouvrant PerfView et en ouvrant le **collecter** boîte de dialogue de la **collecter** menu.

![menu collecter perfview](media/perfview-collect-menu.png)

Les options par défaut fournira des piles d’appels pour la consommation du processeur, mais étant donné que nous sommes intéressés à durée de blocage, ainsi, vous devez également activer **temps Thread** piles. Une fois que les paramètres sont prêts, vous pouvez cliquer sur **démarrer la collecte** puis ouvrez Visual Studio après l’enregistrement de démarrage.

Avant d’arrêter la collection, vous souhaitez vous assurer que Visual Studio soit entièrement initialisé, la fenêtre principale est complètement visible et si votre extension possède des interface utilisateur qui affiche automatiquement, ils sont également visibles. Lorsque Visual Studio est complètement chargé et que votre extension est initialisée, vous pouvez arrêter l’enregistrement pour analyser la trace.

**Analyse une trace avec PerfView :**

Une fois l’enregistrement terminé PerfView automatiquement ouvrir la trace et développez les options.

Dans le cadre de cet exemple, nous nous intéressons principalement le **threads des piles de temps** vue que vous pouvez trouver sous **groupe avancé**. Cette vue affiche le temps total passé sur un thread par une méthode, y compris le temps processeur et le temps bloqué, telles que les e/s disque ou en attente sur les handles.

 ![piles des threads](media/perfview-thread-time-stacks.png)

 Lors de l’ouverture **threads des piles de temps** afficher, vous devez choisir le **devenv** processus pour démarrer l’analyse.

PerfView a conseils détaillés sur la lecture des piles de temps sous son propre menu d’aide pour une analyse plus détaillée de thread. Pour les besoins de cet exemple, nous voulons filtrer davantage cette vue en incluant uniquement les piles avec notre thread de démarrage et le nom de module packages.

1. Définissez **GroupPats** au texte vide à supprimer n’importe quel regroupement ajouté par défaut.
2. Définissez **IncPats** à inclure les parties de votre nom d’assembly et le démarrage de Thread en plus de filtre de processus existant. Dans ce cas, il doit être **devenv ; Thread de démarrage ; MakeVsSlowExtension**.

Maintenant la vue n’affiche que les coûts qui est associé avec les assemblys liés à l’extension. Dans cette vue, tout moment répertoriés sous la **Inc (coût inclusif)** colonne du thread de démarrage est liée à notre extension filtrée et un impact sur démarrage.

Pour l’exemple ci-dessus certains appel intéressante piles serait :

1. À l’aide de l’e/s `System.IO` classe : Tandis que le coût inclusif de ces images peut ne pas être trop coûteux dans la trace, ils sont une cause potentielle d’un problème dans la mesure où la vitesse d’e/s de fichier varie d’un ordinateur à l’autre.

   ![trames de système d’e/s](media/perfview-system-io-frames.png)

2. Blocage des appels en attente sur un autre travail asynchrone : Dans ce cas, temps inclusif représentent le temps que le thread principal est bloqué sur l’achèvement du travail asynchrone.

   ![frames d’appels bloquants](media/perfview-blocking-call-frames.png)

Une des vues dans la trace qui seront utiles pour déterminer l’impact sera le **piles de chargement d’Image**. Vous pouvez appliquer les mêmes filtres appliqués à **threads des piles de temps** afficher et Découvrez tous les assemblys chargés en raison du code exécuté par votre package chargé automatiquement.

Il est important de réduire le nombre d’assemblys chargés à l’intérieur d’une routine d’initialisation de package comme chaque assembly supplémentaire implique d’e/s disque supplémentaire qui peut ralentir le démarrage considérablement sur des machines plus lents.

## <a name="summary"></a>Récapitulatif

Démarrage de Visual Studio a été une des zones sur que nous rendre en permanence des commentaires. Notre objectif comme indiqué précédemment est pour tous les utilisateurs d’avoir un démarrage cohérent avec tous les composants et extensions que dont ils disposent. Nous souhaitons travailler avec les propriétaires d’extension pour les aider à nous aider à atteindre cet objectif. Les instructions ci-dessus devraient être utiles pour comprendre un impact sur les extensions au démarrage et soit éviter la nécessité d’auto charge ou de charger de façon asynchrone pour réduire l’impact sur la productivité des utilisateurs.
