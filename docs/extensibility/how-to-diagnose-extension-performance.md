---
title: 'Comment : diagnostiquer les performances des extensions | Microsoft Docs'
ms.date: 11/08/2016
ms.topic: how-to
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 542d8a6d6d90091aa7a800ef18f847fea6b1a81c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905908"
---
# <a name="measuring-extension-impact-in-startup"></a>Mesure de l’impact des extensions au démarrage

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Focus sur les performances des extensions dans Visual Studio 2017

Suite aux commentaires des clients, l’un des domaines de la mise en service de Visual Studio 2017 est le démarrage et les performances de chargement de la solution. En tant qu’équipe de la plateforme Visual Studio, nous avons travaillé sur l’amélioration des performances de démarrage et de chargement des solutions. En général, nos mesures suggèrent que les extensions installées peuvent également avoir un impact considérable sur ces scénarios.

Pour aider les utilisateurs à comprendre cet impact, nous avons ajouté une nouvelle fonctionnalité dans Visual Studio pour informer les utilisateurs des extensions lentes. Parfois, Visual Studio détecte une nouvelle extension qui ralentit le chargement ou le démarrage de la solution. Lorsqu’un ralentissement est détecté, les utilisateurs voient une notification dans l’IDE qui les pointe vers la boîte de dialogue « gérer les performances de Visual Studio ». Cette boîte de dialogue est également accessible par le menu aide pour parcourir les extensions détectées précédemment.

![gérer les performances de Visual Studio](media/manage-performance.png)

Ce document vise à aider les développeurs d’extensions en décrivant le mode de calcul de l’impact des extensions. Ce document décrit également comment l’impact de l’extension peut être analysé localement. L’analyse locale de l’impact des extensions détermine si une extension peut être affichée en tant qu’extension d’impact sur les performances.

> [!NOTE]
> Ce document se concentre sur l’impact des extensions sur le démarrage et le chargement de la solution. Les extensions ont également un impact sur les performances de Visual Studio quand elles empêchent la réponse de l’interface utilisateur. Pour plus d’informations sur cette rubrique, consultez [Comment : diagnostiquer des retards de l’interface utilisateur provoqués par des extensions](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Impact des extensions sur le démarrage

L’une des méthodes les plus courantes pour les extensions qui affectent les performances de démarrage consiste à choisir de charger automatiquement dans l’un des contextes d’interface utilisateur de démarrage connus, tels que NoSolutionExists ou ShellInitialized. Ces contextes d’interface utilisateur sont activés au démarrage. Tous les packages qui incluent l' `ProvideAutoLoad` attribut dans leur définition avec ces contextes seront chargés et initialisés à ce moment-là.

Lorsque nous mesurons l’impact d’une extension, nous nous concentrons principalement sur le temps passé par ces extensions qui choisissent le chargement automatique dans les contextes ci-dessus. Les temps mesurés incluent, mais ne sont pas limités à :

* Chargement des assemblys d’extension pour les packages synchrones
* Temps passé dans le constructeur de classe de package pour les packages synchrones
* Temps passé dans la méthode d’initialisation (ou SetSite) du package pour les packages synchrones
* Pour les packages asynchrones, les opérations ci-dessus s’exécutent sur le thread d’arrière-plan.  Par conséquent, les opérations sont exclues de l’analyse.
* Temps passé dans tout travail asynchrone planifié pendant l’initialisation du package à exécuter sur le thread principal
* Temps passé dans les gestionnaires d’événements, en particulier l’activation du contexte initialisé par l’interpréteur de commandes ou la modification de l’État Zombie du shell
* À partir de Visual Studio 2017 Update 3, nous commençons également à surveiller le temps passé dans les appels inactifs avant l’initialisation de l’interpréteur de commandes. Les opérations longues dans les gestionnaires inactifs provoquent également un IDE qui ne répond pas et contribuent au temps de démarrage perçu par l’utilisateur.

Nous avons ajouté de nombreuses fonctionnalités à partir de Visual Studio 2015. Ces fonctionnalités permettent de supprimer le besoin de chargement automatique des packages. Les fonctionnalités diffèrent également de la nécessité de charger des packages à des cas plus spécifiques. Ces cas incluent des exemples où les utilisateurs sont plus à même d’utiliser l’extension ou de réduire l’impact d’une extension lors du chargement automatique.

Vous trouverez plus d’informations sur ces fonctionnalités dans les documents suivants :

[Contextes d’interface utilisateur basés sur des règles](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): un moteur plus riche basé sur des règles, basé sur des contextes d’interface utilisateur, vous permet de créer des contextes personnalisés basés sur des types de projets, des versions et des attributs. Les contextes personnalisés peuvent être utilisés pour charger un package pendant des scénarios plus spécifiques. Ces scénarios spécifiques incluent la présence d’un projet avec une fonctionnalité spécifique au lieu du démarrage. Les contextes personnalisés permettent également [à la visibilité de la commande d’être liée à un contexte personnalisé](visibilityconstraints-element.md) en fonction des composants du projet ou d’autres termes disponibles. Cette fonctionnalité élimine le besoin de charger un package pour inscrire un gestionnaire de requêtes d’état de commande.

[Prise en charge des packages asynchrones](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): la nouvelle classe de base AsyncPackage dans visual studio 2015 permet de charger les packages Visual Studio en arrière-plan de manière asynchrone si la charge du package a été demandée par un attribut de chargement automatique ou une requête de service asynchrone. Ce chargement en arrière-plan permet à l’IDE de rester réactif. L’IDE est réactif même lorsque l’extension est initialisée en arrière-plan et les scénarios critiques tels que le démarrage et le chargement de solution ne seraient pas affectés.

[Services asynchrones](how-to-provide-an-asynchronous-visual-studio-service.md): avec la prise en charge des packages asynchrones, nous avons également ajouté la prise en charge de l’interrogation des services de façon asynchrone et la possibilité d’inscrire des services asynchrones. Plus important encore, nous travaillons sur la conversion des services de base de Visual Studio pour prendre en charge la requête asynchrone afin que la majorité du travail dans une requête asynchrone se produise dans les threads d’arrière-plan. SComponentModel (hôte MEF de Visual Studio) est l’un des principaux services qui prend désormais en charge la requête asynchrone pour permettre aux extensions de prendre entièrement en charge le chargement asynchrone.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Réduction de l’impact des extensions auto-chargées

Si un package doit encore être chargé automatiquement au démarrage, il est important de réduire le travail effectué pendant l’initialisation du package. La réduction du travail d’initialisation des packages réduit le risque d’impact de l’extension sur le démarrage.

Voici quelques exemples qui peuvent entraîner l’échec de l’initialisation d’un package :

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Utilisation du chargement synchrone des packages au lieu du chargement asynchrone des packages

Étant donné que les packages synchrones sont chargés par défaut sur le thread principal, nous encourageons les propriétaires d’extension qui ont des packages chargés automatiquement à utiliser la classe de base de package asynchrone, comme mentionné précédemment. La modification d’un package chargé automatiquement pour prendre en charge le chargement asynchrone permet également de résoudre plus facilement les autres problèmes ci-dessous.

### <a name="synchronous-filenetwork-io-requests"></a>Demandes d’e/s de fichier/réseau synchrones

Idéalement, toute requête d’e/s de fichier ou de réseau synchrone doit être évitée dans le thread principal. Leur impact dépend de l’état de la machine et peut se bloquer pendant de longues périodes dans certains cas.

L’utilisation du chargement de package asynchrone et des API d’e/s asynchrones doit s’assurer que l’initialisation du package ne bloque pas le thread principal dans de tels cas. Les utilisateurs peuvent également continuer à interagir avec Visual Studio pendant que les demandes d’e/s se produisent en arrière-plan.

### <a name="early-initialization-of-services-components"></a>Initialisation précoce des services, composants

L’un des modèles courants de l’initialisation des packages consiste à initialiser les services utilisés par ou fournis par ce package dans le package `constructor` ou la `initialize` méthode. Bien que cela garantisse que les services sont prêts à être utilisés, il peut également ajouter des coûts inutiles au chargement des packages si ces services ne sont pas utilisés immédiatement. Au lieu de cela, ces services doivent être initialisés à la demande pour réduire le travail effectué lors de l’initialisation du package.

Pour les services globaux fournis par un package, vous pouvez utiliser des `AddService` méthodes qui prennent une fonction pour initialiser tardivement le service uniquement lorsqu’il est demandé par un composant. Pour les services utilisés dans le package, vous pouvez utiliser Lazy \<T> ou AsyncLazy \<T> pour vous assurer que les services sont initialisés/interrogés lors de la première utilisation.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Mesure de l’impact des extensions chargées automatiquement à l’aide du journal d’activité

À compter de Visual Studio 2017 Update 3, le journal d’activité Visual Studio contient maintenant des entrées pour l’impact sur les performances des packages lors du démarrage et de la charge de la solution. Pour afficher ces mesures, vous devez ouvrir Visual Studio avec/log Switch et ouvrir *ActivityLog.xml* fichier.

Dans le journal d’activité, les entrées se trouvent sous la source « gérer les performances de Visual Studio » et se présentent comme dans l’exemple suivant :

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Cet exemple montre qu’un package avec le GUID « 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c » a passé 2008 ms dans le démarrage de Visual Studio. Notez que Visual Studio considère le coût de niveau supérieur comme étant le nombre principal lors du calcul de l’impact d’un package, car il s’agit des économies que les utilisateurs voient lorsqu’ils désactivent l’extension pour ce package.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Mesure de l’impact des extensions chargées automatiquement à l’aide de PerfView

Tandis que l’analyse du code peut aider à identifier les chemins de code susceptibles de ralentir l’initialisation des packages, vous pouvez également utiliser le suivi à l’aide d’applications telles que PerfView pour comprendre l’impact d’une charge de package dans le démarrage de Visual Studio.

PerfView est un outil de suivi à l’ensemble du système. Cet outil vous permet de comprendre les chemins d’accès à chaud dans une application en raison de l’utilisation du processeur ou des appels système bloquants. Vous trouverez ci-dessous un exemple rapide d’analyse d’un exemple d’extension à l’aide de PerfView disponibles dans le [Centre de téléchargement Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Exemple de code :**

Cet exemple est basé sur l’exemple de code ci-dessous, qui est conçu pour illustrer le cas de retard courant :

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

Une fois que vous avez configuré votre environnement Visual Studio avec votre extension installée, vous pouvez enregistrer une trace de démarrage en ouvrant PerfView et en ouvrant la boîte de dialogue **collecter** dans le menu **collecter** .

![menu perfview collecter](media/perfview-collect-menu.png)

Les options par défaut fournissent des piles d’appels pour la consommation du processeur, mais étant donné que nous sommes intéressés par le temps de blocage, vous devez également activer les piles de **temps de thread** . Une fois les paramètres prêts, vous pouvez cliquer sur **Démarrer la collecte** , puis ouvrir Visual Studio après le démarrage de l’enregistrement.

Avant d’arrêter la collecte, vous souhaitez vous assurer que Visual Studio est entièrement initialisé, que la fenêtre principale est complètement visible et que si votre extension contient des éléments d’interface utilisateur qui s’affichent automatiquement, ils sont également visibles. Lorsque Visual Studio est entièrement chargé et que votre extension est initialisée, vous pouvez arrêter l’enregistrement pour analyser la trace.

**Analyse d’une trace avec PerfView :**

Une fois l’enregistrement terminé, PerfView ouvre automatiquement les options de suivi et de développement.

Dans le cadre de cet exemple, nous sommes principalement intéressés par l’affichage des **piles de temps du thread** , que vous pouvez trouver sous **groupe avancé**. Cette vue indique le temps total passé sur un thread par une méthode, notamment le temps processeur et le temps bloqué, tels que l’e/s disque ou l’attente de handles.

 ![piles de temps de thread](media/perfview-thread-time-stacks.png)

 Lors de l’ouverture de la vue **piles de temps de thread** , vous devez choisir le processus **devenv** pour démarrer l’analyse.

PerfView a des conseils détaillés sur la façon de lire des piles de temps de thread dans son propre menu d’aide pour une analyse plus détaillée. Dans le cadre de cet exemple, nous voulons filtrer cette vue plus en incluant uniquement les piles avec le nom et le thread de démarrage du module packages.

1. Définissez **GroupPats** sur un texte vide pour supprimer tout regroupement ajouté par défaut.
2. Définissez **IncPats** pour inclure une partie du nom de votre assembly et du thread de démarrage en plus du filtre de processus existant. Dans ce cas, il doit s’agir de **devenv ; Thread de démarrage ; MakeVsSlowExtension**.

À présent, la vue affiche uniquement le coût associé aux assemblys liés à l’extension. Dans cette vue, chaque fois que la colonne **Inc (coût inclusif)** du thread de démarrage est associée à notre extension filtrée, elle aura un impact sur le démarrage.

Dans l’exemple ci-dessus, certaines piles d’appels intéressantes seraient :

1. Les e/s à l’aide `System.IO` de la classe : même si le coût inclusif de ces trames n’est pas trop onéreux dans la trace, il s’agit d’une cause potentielle d’un problème, car la vitesse des e/s de fichier varie d’un ordinateur à l’ordinateur.

   ![trames d’e/s système](media/perfview-system-io-frames.png)

2. Appels de blocage en attente sur un autre travail asynchrone : dans ce cas, le temps inclusif représente le temps pendant lequel le thread principal est bloqué à l’achèvement du travail asynchrone.

   ![frames d’appels de blocage](media/perfview-blocking-call-frames.png)

L’une des autres vues de la trace qui seront utiles pour déterminer l’impact sera les **piles de chargement**de l’image. Vous pouvez appliquer les mêmes filtres que ceux appliqués à la vue **piles de temps de thread** et rechercher tous les assemblys chargés en raison du code exécuté par votre package chargé automatiquement.

Il est important de réduire le nombre d’assemblys chargés au sein d’une routine d’initialisation de package, car chaque assembly supplémentaire implique des e/s de disque supplémentaires, ce qui peut ralentir considérablement le démarrage sur des ordinateurs plus lents.

## <a name="summary"></a>Résumé

Le démarrage de Visual Studio a été l’un des éléments sur lesquels nous avons continuellement des commentaires. Notre objectif, comme indiqué précédemment, est que tous les utilisateurs disposent d’une expérience de démarrage cohérente, quels que soient les composants et extensions qu’ils ont installés. Nous aimerions travailler avec les propriétaires d’extensions pour nous aider à atteindre cet objectif. L’aide ci-dessus doit être utile pour comprendre l’impact des extensions au démarrage et éviter d’avoir à les charger ou les charger automatiquement de manière asynchrone afin de réduire l’impact sur la productivité des utilisateurs.
