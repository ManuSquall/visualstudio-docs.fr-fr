---
title: "Comment : diagnostiquer les performances de l’extension | Documents Microsoft"
ms.custom: 
ms.date: 11/08/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
caps.latest.revision: 1
author: BertanAygun
ms.author: bertaygu
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b78a02b9d780b9556cbbf42fce04b1da06e22833
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="measuring-extension-impact-in-startup"></a>Mesurer l’impact d’extension de démarrage

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Concentrez-vous sur les performances d’extension dans Visual Studio 2017

En fonction des commentaires des clients, une des zones de focus pour cette version de Visual Studio 2017 a été performances de chargement de démarrage et de la solution. Pendant que l’équipe de plateforme Visual Studio, nous avons travaillé sur l’amélioration des performances de chargement de démarrage et de la solution en général, nos données de télémétrie suggère des extensions installées peuvent avoir également un impact considérable sur ces scénarios.

Pour aider les utilisateurs à comprendre cet impact, nous avons ajouté une nouvelle fonctionnalité dans Visual Studio pour avertir les utilisateurs des extensions lentes. Lorsque Visual Studio détecte une nouvelle extension ralentit de charge de la solution ou de démarrage, les utilisateurs verront une notification dans l’IDE de les utiliser pour la nouvelle boîte de dialogue « Gérer des performances Visual Studio ». Cette boîte de dialogue est également toujours accessible par le menu d’aide pour parcourir les extensions précédemment détectées.

![gérer les performances de Visual Studio](media/manage-performance.png)

Ce document vise à aider les développeurs d’extensions en décrivant comment l’impact de l’extension est calculée et comment il peut être analysé localement pour tester si une extension peut s’afficher à l’extension de compromettre des performances.

## <a name="how-extensions-can-impact-startup"></a>Impact extensions de démarrage

Une des utilisations plus courantes pour les extensions à l’impact sur les performances de démarrage est en choisissant de charge automatique à un des contextes d’interface utilisateur tels que NoSolutionExists ou ShellInitialized démarrage connus. Activation lors du démarrage de ces contextes d’interface utilisateur et tous les packages qui incluent l’attribut « ProvideAutoLoad » dans leur définition avec ces contextes seront chargés et initialisés à ce moment-là.

Lorsque nous mesurer l’impact d’une extension, nous nous concentrer principalement sur le temps passé par les extensions de choisir de chargement automatique dans les contextes ci-dessus. Mesurée fois sont incluent, mais ne pas être limités à :

* Chargement des assemblys d’extension pour les packages synchrones
* Temps passé dans le constructeur de classe de package pour les packages synchrones
* Temps passé dans la méthode d’initialisation (ou SetSite) package pour les packages synchrones
* Pour les packages asynchrones les opérations s’exécutent sur le thread d’arrière-plan et par conséquent sont exclues de l’analyse
* Temps passé dans n’importe quel travail asynchrone planifiée pendant l’initialisation du package à exécuter sur le thread principal
* Temps passé dans les gestionnaires d’événements, en particulier l’activation de contexte shell initialisé ou le changement d’état zombie shell
* Démarrer à partir de Visual Studio 2017 Update 3, nous allons également commencer analyse le temps passé dans lors des appels d’inactivité avant l’initialisation du shell. Opérations longues dans les gestionnaires d’inactivité également provoquent l’IDE ne répond pas et contribuent au temps de démarrage perçu par l’utilisateur.

Nous avons ajouté plusieurs fonctionnalités à partir de Visual Studio 2015 pour aider à supprimer la nécessité pour les packages de charge automatique, reporter leur charge à des cas plus spécifiques où les utilisateurs serait plus certaines utiliser l’extension ou de réduire un impact de l’extension lors du chargement automatiquement.

Vous trouverez plus d’informations sur ces fonctionnalités dans les documents suivants :

[Contextes d’interface utilisateur basée sur des règles](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): un moteur basé sur une règle plus riche basé sur les contextes d’interface utilisateur permettent de créer des contextes personnalisés basés sur les types de projets, les versions et les fonctionnalités. Les contextes personnalisés peuvent servir à charger un package durant les scénarios plus spécifiques telles que la présence d’un projet avec une fonctionnalité spécifique au lieu de démarrage ; ou autoriser [commande visibilité à un contexte personnalisé](https://msdn.microsoft.com/en-us/library/bb166512.aspx) basé sur les fonctionnalités de projet ou d’autres termes disponibles, éliminant ainsi la nécessité de charger un package pour inscrire un gestionnaire de requête de statut de commande.

[Prise en charge asynchrone package](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): packages de Visual Studio être chargé dans l’arrière-plan de façon asynchrone si le chargement du package a été demandé par un attribut de charge automatique ou d’une requête de service asynchrone permet à la nouvelle classe de base AsyncPackage dans Visual Studio 2015 . Ce chargement en arrière-plan permet à l’IDE à rester réactif pendant que l’extension est initialisée en arrière-plan et des scénarios critiques comme charge de solution et de démarrage n’affectées.

[Services asynchrones](how-to-provide-an-asynchronous-visual-studio-service.md): avec prise en charge du package asynchrone, nous avons également ajouté la prise en charge pour l’interrogation des services de façon asynchrone et la possibilité d’inscrire des services asynchrones. Plus important encore, nous travaillons sur la conversion des services de Visual Studio principaux pour prendre en charge de la requête asynchrone afin que la majorité du travail dans une requête asynchrone se produit dans les threads d’arrière-plan. SComponentModel (hôte Visual Studio MEF) est un des principaux services qui prend désormais en charge la requête asynchrone pour autoriser les extensions prendre en charge le chargement asynchrone de complètement.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Réduire l’impact d’auto extensions chargées

Si un package doit toujours être automatiquement chargé au démarrage, il est important de réduire le travail effectué lors de l’initialisation du package pour réduire les risques de l’extension ayant un impact sur démarrage.

Quelques exemples qui peuvent provoquer l’initialisation du package à être coûteux sont :

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Utilisation du chargement du package synchrone au lieu de chargement du package asynchrone

Étant donné que les packages synchrones sont chargées sur le thread principal par défaut, nous encourageons les propriétaires d’extension qui ont automatiquement chargé packages utilisent la classe de base du package asynchrone à la place comme indiqué précédemment. La modification d’un package chargé automatiquement pour prendre en charge le chargement asynchrone également rend plus facile à résoudre les problèmes ci-dessous.

### <a name="synchronous-filenetwork-io-requests"></a>Requêtes d’e/s de fichier synchrones/réseau

Dans l’idéal, toute demande d’e/s réseau ou de fichier synchrone doit être évité dans le thread principal comme leur impact dépendront de l’état de l’ordinateur et peut se bloquer pendant de longues périodes de temps dans certains cas.

À l’aide des API d’e/s asynchrones et de chargement du package asynchrone doit s’assurer que l’initialisation du package ne bloque pas le thread principal dans de tels cas, et les utilisateurs peuvent continuer à interagir avec Visual Studio, alors que les demandes d’e/s se produisent en arrière-plan.

### <a name="early-initialization-of-services-components"></a>Initialisation anticipée de services, composants

Un des modèles dans l’initialisation de package communs consiste à initialiser les services fournis par ce package dans la méthode de constructeur ou d’initialisation du package soit utilisé par. Alors que cela garantit que les services sont prêts à être utilisés, il peut également ajouter des coûts inutiles pour créer un package du chargement si ces services ne servent pas immédiatement. À la place de ces services doivent être initialisés à la demande afin de réduire le travail effectué dans l’initialisation du package.

Pour les services globaux fournis par un package, vous pouvez utiliser les méthodes de AddService qui prend une fonction tardivement initialiser le service uniquement quand il est demandé par un composant. Pour les services utilisés dans le package, vous pouvez utiliser Lazy<T> ou AsyncLazy<T> pour vous assurer les services sont initialisés ou interrogée à la première utilisation.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Mesurer l’impact d’auto chargé des extensions à l’aide du journal d’activité

À compter de Visual Studio 2017 Update 3, le journal d’activité Visual Studio maintenant contient des entrées pour l’impact sur les performances des packages lors du chargement du démarrage et de la solution. Pour voir ces mesures, vous devez démarrer Visual Studio avec le commutateur /log et ouvrir le fichier de ActivityLog.xml.

Dans le journal d’activité, les entrées sous la source « Gérer des performances Visual Studio » et doit ressembler à la suivante :

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Cela signifie que ce package avec le GUID « 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c » passé à ms 2008 dans le démarrage de Visual Studio. Notez que Visual Studio tient compte des coûts de niveau supérieur en tant que numéro de téléphone principal lors du calcul de l’impact d’un package comme ce serait l’utilisateur savigs, consultez quand ils désactivent l’extension de ce package.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Mesurer l’impact d’auto chargé des extensions à l’aide de PerfView

Lors de l’analyse du code peut aider à identifier les chemins de code qui risque de ralentir l’initialisation du package, vous pouvez également utiliser le suivi à l’aide d’applications telles que PerfView pour comprendre l’impact d’une charge de package dans le démarrage de Visual Studio.

PerfView est un outil de suivi large système qui vous aideront à comprendre les chemins d’accès à chaud dans une application en raison de l’utilisation de l’UC ou le blocage des appels système. Voici un exemple rapide sur l’analyse d’un exemple d’extension à l’aide de PerfView disponible sur le [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Exemple de code :**

Cet exemple est basé sur l’exemple de code ci-dessous, qui est conçue pour afficher les cas de certaines causes courantes de délai :

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

Une fois que vous configurez votre environnement Visual Studio avec votre extension installée, vous pouvez enregistrer une trace de démarrage en ouvrant PerfView et en ouvrant le dialogue collecter à partir du menu de « Collecte ».

![menu de collecter perfview](media/perfview-collect-menu.png)

Les options par défaut fournit les piles d’appels de la consommation du processeur, mais étant donné que nous sommes intéressés par temps de blocage, ainsi, vous devez également activer piles de « Thread Time ». Une fois les paramètres prêt, vous pouvez cliquez sur « Démarrer la collecte » et démarrez Visual Studio une fois l’enregistrement est démarré.

Avant d’arrêter la collection, vous souhaitez vous assurer que Visual Studio soit entièrement initialisé, la fenêtre principale est totalement visible et si votre extension a n’importe quel nombre d’éléments de l’interface utilisateur qui affiche automatiquement, ils sont également visibles. Une fois que Visual Studio est complètement chargé et que votre extension est initialisée, pour arrêter l’enregistrement pour analyser la trace.

**Analyser une trace avec PerfView :**

Une fois que l’enregistrement est terminé PerfView automatiquement ouvrir la trace et développez les options.

Dans le cadre de cet exemple, nous intéresse principalement dans la vue « Threads des piles de temps » que vous pouvez trouver sous « Groupe avancé ». Cette vue affiche le temps total passé sur un thread par une méthode, y compris le temps processeur et le temps bloqué, telles que les e/s disque ou en attente sur les handles.

 ![piles des threads](media/perfview-thread-time-stacks.png)

 Lors de l’ouverture de vue « Threads des piles de temps », vous devez choisir le processus « devenv » pour démarrer l’analyse.

PerfView détaille comment lire des piles de temps sous son propre menu d’aide pour une analyse plus détaillée de thread. Pour des raisons de cet exemple, si vous souhaitez filtrer davantage cet affichage en incluant uniquement les piles avec notre thread de démarrage et le nom de module packages.

1. Texte vide à supprimer n’importe quel regroupement ajouté par défaut la valeur « GroupPats ».
2. Ensemble de « IncPats » pour inclure la partie de votre nom d’assembly et de démarrage du Thread en plus de filtre de processus existant. Dans ce cas, il doit être « devenv ; Démarrage du Thread ; MakeVsSlowExtension ».

La vue n’affiche maintenant coût est associé avec les assemblys associés à l’extension. Dans cette vue, n’importe quel moment indiqué sous la colonne « Inc. » (coût inclus) du thread de démarrage est liée à l’extension de notre filtrée et avec incidence sur démarrage.

Pour l’exemple ci-dessus certains appel intéressante piles serait :

1. E/s à l’aide de la classe de System.IO : lors de coût inclusive de ces images n’est peut-être pas très coûteux dans la trace, ils sont une cause potentielle d’un problème, car la vitesse d’e/s de fichier varie d’un ordinateur.

  ![trames de système d’e/s](media/perfview-system-io-frames.png)

2. Blocage des appels en attente sur un autre travail asynchrone : dans ce cas temps inclusif représente le temps que le thread principal est bloqué sur l’achèvement du travail asynchrone.

  ![cadres d’appel de blocage](media/perfview-blocking-call-frames.png)

Une des vues dans la trace qui seront utiles pour déterminer l’impact sera les piles « chargement de l’Image ». Vous pouvez appliquer les mêmes filtres appliqués à la vue « Threads des piles de temps » et découvrir tous les assemblys chargés en raison du code exécuté par votre package chargé automatiquement.

Il est important de réduire le nombre d’assemblys chargés à l’intérieur d’une routine d’initialisation de package que chaque assembly supplémentaire implique d’e/s disque supplémentaire qui peut ralentir le démarrage considérablement sur les ordinateurs plus lents.

## <a name="summary"></a>Résumé

Démarrage de Visual Studio a été un des domaines en permanence, nous obtenons des commentaires sur. Notre objectif, comme indiqué plus haut est pour tous les utilisateurs ont un démarrage cohérent avec tous les composants et qu’ils ont installé des extensions et nous souhaitons travailler avec les propriétaires d’extension pour les aider à atteindre cet objectif. Les instructions ci-dessus doivent être utiles pour comprendre un impact extensions au démarrage et soit évitant automatiquement la charge ou de charger de façon asynchrone pour réduire l’impact sur la productivité des utilisateurs.

