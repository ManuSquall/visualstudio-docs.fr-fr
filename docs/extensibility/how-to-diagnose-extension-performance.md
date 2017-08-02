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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f1226c9bd42476acc9fb57be0a6df8058174fd4d
ms.lasthandoff: 02/22/2017

---
# <a name="measuring-extension-impact-in-startup"></a>Mesurer l’impact d’extension dans le démarrage

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Se concentrer sur les performances de l’extension de Visual Studio 2017

En fonction des commentaires des clients, un des domaines d’intérêt pour la version de Visual Studio 2017 a été performances de chargement de démarrage et de la solution. Bien que, en tant qu’équipe de plate-forme de Visual Studio, nous avons travaillé sur l’amélioration des performances de chargement de démarrage et de la solution en général, nos résultats de télémétrie suggère extensions installées peuvent avoir également un impact considérable sur ces scénarios.

Pour aider les utilisateurs à comprendre cet impact, nous avons ajouté une nouvelle fonctionnalité dans Visual Studio pour informer les utilisateurs des extensions lentes. Lorsque Visual Studio détecte une nouvelle extension qui ralentit la charge de la solution ou de démarrage, les utilisateurs verront une notification dans l’IDE à la nouvelle boîte de dialogue « Gérer des performances Visual Studio ». Cette boîte de dialogue est toujours accessible par menu d’aide pour parcourir les extensions détectées précédemment.

![gérer les performances de Visual Studio](~/docs/extensibility/media/manage-performance.png)

Ce document vise à aider les développeurs d’extensions en décrivant comment l’impact de l’extension est calculée et comment il peut être analysé en local pour tester si une extension peut s’afficher comme une extension aient un impact sur des performances.

## <a name="how-extensions-can-impact-startup"></a>Impact extensions de démarrage

Une des façons plus courantes pour les extensions de l’impact sur les performances de démarrage est en choisissant de chargement automatique à un des contextes d’interface utilisateur démarrage connus tels que NoSolutionExists ou ShellInitialized. Les contextes d’interface utilisateur activation lors du démarrage et tous les packages qui incluent l’attribut « ProvideAutoLoad » dans leur définition avec ces contextes sont chargées et initialisées à ce moment-là.

Lorsque nous mesurons l’impact d’une extension, nous concentrer principalement sur le temps passé par les extensions de choisir de chargement automatique dans les contextes ci-dessus. Mesuré fois seraient incluent, mais ne pas être limités à :

* Chargement des assemblys d’extension pour les packages synchrone
* Temps passé dans le constructeur de classe de package pour les packages synchrone
* Temps passé dans la méthode Initialize (ou SetSite) de package pour les packages synchrone
* Pour les packages asynchrones les opérations s’exécutent sur le thread d’arrière-plan et sont donc exclues de l’analyse
* Temps passé dans n’importe quel travail asynchrone prévu lors de l’initialisation du package à exécuter sur le thread principal
* Temps passé dans les gestionnaires d’événements, en particulier l’activation de contexte shell initialisé ou la modification d’état zombie shell

Nous avons ajouté plusieurs fonctionnalités à partir de Visual Studio 2015 pour aider à supprimer la nécessité pour les packages de charge automatique, reporter leur charge cas plus spécifiques où les utilisateurs seront à l’utilisation de l’extension ou de réduire un impact de l’extension lors du chargement automatiquement.

Vous trouverez plus d’informations sur ces fonctionnalités dans les documents suivants :

[Contextes d’interface utilisateur basée sur des règles](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): un moteur basé sur une règle plus riche construit autour des contextes d’interface utilisateur permettent de créer des contextes personnalisés basés sur les fonctionnalités de versions et types de projet. Les contextes personnalisés peuvent servir à charger un package au cours des scénarios plus spécifiques telles que la présence d’un projet à une fonctionnalité spécifique au lieu de démarrage ; ou autoriser [commande visibilité d’être rattachés à un contexte personnalisé](https://msdn.microsoft.com/en-us/library/bb166512.aspx) basé sur les fonctionnalités de projet ou d’autres termes disponibles afin d’éviter de charger un package pour inscrire un gestionnaire de requête de statut de commande.

[Prise en charge asynchrone package](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): packages Visual Studio doit être chargé dans l’arrière-plan de façon asynchrone si le chargement du package a été demandé par un attribut de chargement automatique ou d’une requête de service asynchrone permet à la nouvelle classe de base AsyncPackage dans Visual Studio 2015. Ce chargement en arrière-plan permet à l’IDE de rester réactif pendant que l’extension est initialisée en arrière-plan et des scénarios critiques comme charge de solution et de démarrage ne seraient pas affectées.

[Les services asynchrones](how-to-provide-an-asynchronous-visual-studio-service.md): prise en charge asynchrone package, nous avons également ajouté la prise en charge pour l’interrogation des services de manière asynchrone et vous pouvez inscrire des services asynchrones. Plus important encore, nous travaillons sur la conversion de services Visual Studio de base pour prendre en charge la requête asynchrone afin que la majorité du travail dans une requête asynchrone se produit dans les threads d’arrière-plan. SComponentModel (hôte Visual Studio MEF) est un des principaux services qui prend désormais en charge une requête asynchrone pour autoriser des extensions prendre en charge le chargement asynchrone complètement.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Réduction de l’impact auto extensions chargées

Si un package doit toujours être automatiquement chargé au démarrage, il est important de réduire le travail effectué pendant l’initialisation de package pour réduire les risques de l’extension d’un impact sur le démarrage.

Certains exemples susceptible d’être coûteux de l’initialisation de package sont :

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Utilisation du chargement du package synchrone au lieu de chargement du package asynchrone

Étant donné que les packages synchrones sont chargés sur le thread principal par défaut, nous encourageons les propriétaires d’extension qui ont chargé automatiquement les packages à utiliser la classe de base du package asynchrone à la place comme indiqué précédemment. Modification d’un package chargé automatiquement pour prendre en charge le chargement asynchrone également rend plus facile à résoudre les problèmes ci-dessous.

### <a name="synchronous-filenetwork-io-requests"></a>Requêtes d’e/s de fichier synchrones/réseau

Dans l’idéal, toute demande d’e/s réseau ou de fichier synchrone doit être évité dans le thread principal comme leur impact varie selon l’état de l’ordinateur et peut se bloquer pendant de longues périodes de temps dans certains cas.

À l’aide des API d’e/s asynchrones et chargement du package asynchrone doit s’assurer que l’initialisation du package ne bloque pas le thread principal dans ce cas, et les utilisateurs peuvent continuer à interagir avec Visual Studio pendant que les demandes d’e/s se produisent en arrière-plan.

### <a name="early-initialization-of-services-components"></a>Initialisation anticipée des services, composants

Un des modèles courants dans l’initialisation du package consiste à initialiser les services fournis par ce package dans la méthode de constructeur ou d’initialisation du package soit utilisé par. Alors que les services sont prêtes à être utilisées, ainsi il peut également ajouter des coûts inutiles pour empaqueter le chargement si ces services ne sont pas utilisées immédiatement. À la place de ces services doivent être initialisés à la demande afin de minimiser le travail effectué dans l’initialisation du package.

Pour les services globaux fournis par un package, vous pouvez utiliser les méthodes de AddService qui prend une fonction d’initialisation différée du service uniquement lorsque cela est demandé par un composant. Pour les services utilisés dans le package, vous pouvez utiliser Lazy<T> ou AsyncLazy<T> pour assurer les services sont initialisés ou interrogée à la première utilisation.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Mesurer l’impact auto chargé des extensions à l’aide de PerfView

Pendant l’analyse du code peut aider à identifier les chemins de code qui peuvent ralentir l’initialisation du package, vous pouvez également utiliser le suivi à l’aide d’applications telles que PerfView pour comprendre l’impact d’une charge de package dans le démarrage de Visual Studio.

PerfView est un outil de suivi large de système qui vous aideront à comprendre les chemins d’accès à chaud dans une application en raison de l’utilisation du processeur ou le blocage des appels système. Voici un exemple rapide sur l’analyse d’un exemple d’extension à l’aide disponible à l’adresse PerfView le [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Exemple de code :**

Cet exemple est basé sur l’exemple de code ci-dessous, qui est conçu pour afficher les cas de certaines causes courantes de délai :

```c#
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

Une fois que vous configurez votre environnement Visual Studio avec votre extension installée, vous pouvez enregistrer une trace de démarrage en ouvrant PerfView et en ouvrant le dialogue collecter à partir du menu « Collecter ».

![menu collecter perfview](~/docs/extensibility/media/perfview-collect-menu.png)

Les options par défaut fournit les piles d’appels pour l’utilisation du processeur, mais puisque nous sommes intéressés à temps de blocage, ainsi, vous devez également activer des piles de « Temps de Thread ». Une fois que les paramètres sont prêts, vous pouvez cliquez sur « Démarrer la collecte » et démarrez Visual Studio une fois l’enregistrement est démarré.

Avant d’arrêter la collection, vous souhaitez vous assurer que Visual Studio est entièrement initialisé, la fenêtre principale est complètement visible et si votre extension a des parties de l’interface utilisateur s’affiche automatiquement, ils sont également visibles. Une fois que Visual Studio est complètement chargée et que votre extension est initialisée, pour arrêter l’enregistrement pour analyser la trace.

**Analyse une trace avec PerfView :**

Une fois l’enregistrement terminé PerfView automatiquement ouvrir la trace et développez les options.

Dans le cadre de cet exemple, nous nous intéressons principalement la vue « Threads des piles de temps » qui se trouve sous « Groupe avancé ». Cette vue affiche le temps total passé sur un thread par une méthode, y compris le temps processeur et le temps bloqué, telles que les e/s disque ou en attendant des handles.

 ![piles des threads](~/docs/extensibility/media/perfview-thread-time-stacks.png)

 Lors de l’ouverture de vue « Threads des piles de temps », vous devez choisir le processus « devenv » pour démarrer l’analyse.

PerfView a conseils détaillés sur la lecture de thread piles fois sous son propre menu d’aide pour une analyse plus détaillée. Pour les besoins de cet exemple, nous voulons filtrer davantage cet affichage en incluant uniquement les piles avec notre thread de démarrage et le nom de module packages.

1. Texte vide à supprimer n’importe quel regroupement ajouté par défaut la valeur « GroupPats ».
2. Ensemble « IncPats » pour inclure la partie de votre nom de l’assembly et le démarrage du Thread en plus de filtre de processus existant. Dans ce cas, il doit être « devenv ; Démarrage du Thread. MakeVsSlowExtension ».

La vue n’affiche désormais coût est associé avec les assemblys liés à l’extension. Dans cette vue, n’importe quel moment indiqué sous la colonne « Inc. » (coût inclus) du thread de démarrage est liée à notre extension filtrée et un impact sur démarrage.

Pour l’exemple ci-dessus certains appel intéressante piles serait :

1. E/s à l’aide de la classe de System.IO : tandis que le coût inclusif de ces images peut ne pas être très coûteux dans la trace, ils sont une cause potentielle d’un problème dans la mesure où la vitesse d’e/s de fichier varie d’un ordinateur à un autre.

  ![trames de système d’e/s](~/docs/extensibility/media/perfview-system-io-frames.png)

2. Blocage des appels en attente sur une autre tâche asynchrone : dans ce cas temps inclusif représentent le temps que le thread principal est bloqué sur l’achèvement du travail asynchrone.

  ![frames d’appels bloquants](~/docs/extensibility/media/perfview-blocking-call-frames.png)

Une des vues dans la trace qui seront utiles pour déterminer l’impact sera les piles « charge de l’Image ». Vous pouvez appliquer les mêmes filtres appliqués à la vue « Threads des piles de temps » et Découvrez tous les assemblys chargés en raison du code exécuté par votre package chargé automatiquement.

Il est important de réduire le nombre d’assemblys chargés à l’intérieur d’une routine d’initialisation de package que chaque assembly supplémentaire implique l’e/s de disque supplémentaire qui peut ralentir le démarrage considérablement sur les ordinateurs plus lents.

## <a name="summary"></a>Résumé

Démarrage de Visual Studio a été parmi les zones que nous continuellement d’obtenir des commentaires. Notre objectif comme indiqué plus haut est pour tous les utilisateurs aient un démarrage cohérent avec tous les composants et extensions qu’ils ont installé et nous souhaitons travailler avec les propriétaires d’extension pour les aider à atteindre cet objectif. Les instructions ci-dessus devraient être utiles pour comprendre un impact extensions au démarrage et en évitant d’automatiquement la charge ou les charger asynchrone pour réduire l’impact sur la productivité des utilisateurs.
