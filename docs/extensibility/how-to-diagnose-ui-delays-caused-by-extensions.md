---
title: Retarde l’interface utilisateur d’extension de diagnostic dans Visual Studio | Microsoft Docs
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: douge
ms.workload: multiple
ms.openlocfilehash: 1bd09827899000e4f3d1f65fae27da969bcbc107
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887709"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Procédure : Diagnostiquer les délais de l’interface utilisateur causés par les extensions

Lors de l’interface utilisateur cesse de répondre, Visual Studio examine la pile des appels du thread d’interface utilisateur, en commençant par le nœud terminal et en progressant vers la base. Si Visual Studio détermine qu’un frame de pile des appels appartient à un module qui fait partie d’une extension installée et activée, une notification s’affiche.

![Délai d’interface utilisateur (absence de réponse) Notification](media/ui-delay-notification-in-vs.png)

La notification informe l’utilisateur que le délai de l’interface utilisateur (autrement dit, l’absence de réponse dans l’interface utilisateur) est peut-être le résultat du code à partir d’une extension. Il fournit également l’utilisateur avec des options pour désactiver l’extension ou les futures notifications pour cette extension.

Ce document décrit comment vous pouvez diagnostiquer dans votre code d’extension cause des notifications de délai de l’interface utilisateur. 

> [!NOTE]
> N’utilisez pas l’instance expérimentale de Visual Studio pour diagnostiquer les retards de l’interface utilisateur. Certaines parties de l’analyse de la pile des appels requis pour les notifications de délai de l’interface utilisateur sont désactivées lors de l’utilisation de l’instance expérimentale, ce qui signifie que les notifications de délai de l’interface utilisateur ne peuvent pas être affichées.

Une vue d’ensemble du processus de diagnostic est comme suit :
1. Identifier le scénario de déclencheur.
2. Redémarrez Visual Studio avec l’activité de connexion.
3. Démarrer le suivi ETW.
4. Déclencher la notification s’affiche plus.
5. Arrêter le suivi ETW.
6. Examinez le journal d’activité pour obtenir l’ID de délai.
7. Analyser le suivi ETW à l’aide des ID de retard à l’étape 6.

Dans les sections suivantes, nous allons examiner ces étapes plus en détail.

## <a name="identify-the-trigger-scenario"></a>Identifier le scénario de déclencheur

Pour de diagnostiquer un délai de l’interface utilisateur, vous devez d’abord identifier quelles (séquence d’actions) entraîne de Visual Studio afficher la notification. Il s’agit pour puisse vous en mesure de déclencher la notification plus tard avec la journalisation activée.

## <a name="restart-vs-with-activity-logging-on"></a>Redémarrez Visual Studio avec l’activité de journalisation

Visual Studio peut générer un « journal d’activité » qui fournit des informations utiles lors du débogage d’un problème. Pour allumer l’activité de journalisation dans Visual Studio, démarrez Visual Studio avec le `/log` option de ligne de commande. Après le démarrage de Visual Studio, le journal d’activité est stocké dans l’emplacement suivant :

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Pour en savoir plus sur la façon dont vous pouvez trouver votre VS ID d’instance, consultez [outils de détection et la gestion des instances de Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Plus tard, nous utiliserons ce journal d’activité pour obtenir des informations supplémentaires sur les retards de l’interface utilisateur et les notifications associées.

## <a name="starting-etw-tracing"></a>Démarrer le suivi ETW

Vous pouvez utiliser [PerfView](https://github.com/Microsoft/perfview/) pour collecter un suivi ETW. PerfView fournit une interface facile à utiliser pour collecter un suivi ETW et les analyser. Utilisez la commande suivante pour collecter une trace :

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Ainsi, le fournisseur « Microsoft VisualStudio », qui est le fournisseur de que Visual Studio utilise pour les événements liés aux notifications de délai de l’interface utilisateur. Il spécifie également le mot clé pour le fournisseur de noyau PerfView peut utiliser pour générer le **threads des piles de temps** vue.

## <a name="trigger-the-notification-to-appear-again"></a>Déclencher la notification de nouveau l’affichage

Une fois que PerfView a démarré la collecte des traces, vous pouvez utiliser la séquence d’actions de déclencheur (à l’étape 1) pour la notification s’affiche plus. Une fois la notification est affichée, vous pouvez arrêter la collecte de trace pour PerfView traiter et générer le fichier de sortie.

## <a name="stop-etw-tracing"></a>Arrêter le suivi ETW

Pour arrêter la collecte de trace, utilisez simplement le **arrêter la collecte** bouton dans la fenêtre de PerfView. Une fois que vous arrêtez la collecte des traces, PerfView traitera automatiquement les événements ETW et génère un fichier de trace de sortie.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Examinez le journal d’activité pour obtenir l’ID de délai

Comme mentionné précédemment, vous pouvez trouver le journal d’activité à *%APPDATA%\Microsoft\VisualStudio\<vs_instance_id > \ActivityLog.xml*. Chaque fois que Visual Studio détecte une extension du délai d’interface utilisateur, il écrit un nœud dans le journal d’activité avec `UIDelayNotifications` comme source. Ce nœud contient quatre éléments d’information sur le délai de l’interface utilisateur :

- L’ID de délai de l’interface utilisateur, un numéro séquentiel qui identifie de façon unique un délai de l’interface utilisateur dans une session de Visual Studio
- L’ID de session qui identifie de façon unique votre session de Visual Studio à partir du début à la fermer
- Ou non une notification a été indiquée pour le délai de l’interface utilisateur
- L’extension qui est probablement le délai de l’interface utilisateur

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> Pas tous les retards de l’interface utilisateur entraînent une notification. Par conséquent, vous devez toujours vérifier le **Notification indiquée ?** valeur afin d’identifier correctement le délai de l’interface utilisateur de droite.

Après avoir trouvé le délai de l’interface utilisateur correct dans le journal d’activité, notez l’ID de délai de l’interface utilisateur spécifié dans le nœud. Vous allez utiliser l’ID pour rechercher l’événement ETW correspondant à l’étape suivante.

## <a name="analyze-the-etw-trace"></a>Analyser le suivi ETW

Ensuite, ouvrez le fichier de trace. Pour cela, soit à l’aide de la même instance de PerfView ou en démarre une nouvelle instance et en définissant le chemin du dossier actuel dans l’angle supérieur gauche de la fenêtre à l’emplacement du fichier de trace.

![Définir le chemin d’accès du dossier dans Perfview](media/perfview-set-path.png)

Sélectionnez le fichier de trace dans le volet gauche, puis ouvrez-le en choisissant **ouvrir** dans le menu contextuel.

> [!NOTE]
> Par défaut PerfView génère une archive Zip. Lorsque vous ouvrez *trace.zip*, il décompresse l’archive automatiquement et que vous la trace est ouvert. Vous pouvez ignorer cette étape en décochant la **Zip** boîte pendant la collecte de trace. Toutefois, si vous envisagez de transférer et utiliser les traces sur différentes machines, nous recommandons vivement d’en décochant la **Zip** boîte. Sans cette option, les fichiers PDB requis pour les assemblys Ngen seront accompagnent pas la trace et par conséquent, les symboles à partir des assemblys de Ngen ne seront pas résolus sur l’ordinateur de destination. (Consultez [ce billet de blog](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/) pour plus d’informations sur les fichiers PDB pour les assemblys de Ngen.) 

Il peut prendre plusieurs minutes pour PerfView traiter et ouvrir la trace. Une fois que la trace est ouverte, une liste de « vues » différentes s’affichent sous ce dernier.

![Vue Résumé de trace PerfView](media/perfview-summary-view-events-selected.png)

Nous allons tout d’abord utiliser le **événements** afin d’obtenir l’intervalle de temps du délai de l’interface utilisateur :

1. Ouvrez le **événements** vue en sélectionnant `Events` nœud sous la trace et en choisissant **Open** dans le menu contextuel.
2. Sélectionnez «`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`» dans le volet gauche.
3. Appuyez sur entrée

La sélection est appliquée et toutes les `ExtensionUIUnresponsiveness` événements sont affichés dans le volet droit.

![Sélection des événements dans l’affichage des événements](media/perfview-event-selection.png)

Chaque ligne dans le volet droit correspond à un délai de l’interface utilisateur. L’événement inclut une valeur de « Délai ID » qui doit correspondre à l’ID de retard dans le journal d’activité à partir de l’étape 6. Étant donné que `ExtensionUIUnresponsiveness` est déclenché à la fin du délai de l’interface utilisateur, l’horodatage de l’événement (à peu près) marque l’heure de fin du délai de l’interface utilisateur. L’événement contient également la durée du délai. Nous pouvons soustraire la durée entre l’horodatage de fin pour obtenir l’horodatage de lorsque le délai de l’interface utilisateur est démarré.

![Calcul de l’interface utilisateur délai-intervalle de temps](media/ui-delay-time-range.png)

Dans la capture d’écran précédente, par exemple, l’horodatage de l’événement est 12,125.679 et la durée du délai est 6,143.085 (ms). Donc
* Le délai de démarrage est 12,125.679-6,143.085 = 5,982.594.
* L’intervalle de temps de retard de l’interface utilisateur est 5,982.594 à 12,125.679.

Une fois l’intervalle de temps, nous pouvons fermer le **événements** afficher et ouvrir le **piles de threads de temps (avec les activités de StartStop)** vue. Cette vue peut s’avérer utile, car il est souvent les extensions qui bloquent le thread d’interface utilisateur simplement en attente sur d’autres threads ou une opération d’e/S. Par conséquent, le **UC Stack** vue, qui est l’option idéale pour la plupart des cas, ne peut pas capturer le temps du thread dans la mesure où il n’utilise pas l’UC pendant cette période de blocage. Le **threads des piles de temps** résout ce problème en correctement les temps montrant bloqué.

![Nœud de piles de temps (avec des activités de StartStop) de thread dans la vue Résumé PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Lors de l’ouverture **threads des piles de temps** afficher, choisissez la **devenv** processus pour démarrer l’analyse.

![Affichage des piles de temps pour l’analyse de délai de l’interface utilisateur de thread](media/ui-delay-thread-time-stacks.png)

Dans le **threads des piles de temps** afficher, en haut à gauche de la page, vous pouvez définir l’intervalle de temps pour les valeurs que nous avons calculé à l’étape précédente et appuyez sur **entrée** donc les piles sont ajustées pour cet intervalle de temps.

> [!NOTE]
> Détermination de thread qui est l’interface utilisateur de thread de (démarrage) peut être non intuitifs si la collection de trace est démarrée une fois que Visual Studio est déjà ouvert. Toutefois, les premiers éléments sur la pile du thread d’interface utilisateur (démarrage) sont plus probable toujours DLL du système d’exploitation (*ntdll.dll* et *kernel32.dll*) suivie `devenv!?` , puis `msenv!?` . Cette séquence peut aider à identifier le thread d’interface utilisateur.

 ![Qui identifie le thread de démarrage](media/ui-delay-startup-thread.png)

Vous pouvez également filtrer cette vue en incluant uniquement les piles qui contiennent des modules à partir de votre package.

* Définissez **GroupPats** au texte vide à supprimer n’importe quel regroupement ajouté par défaut.
* Définissez **IncPats** à inclure les parties de votre nom de l’assembly en plus de filtre de processus existant. Dans ce cas, il doit être **devenv ; UIDelayR2**.

![Paramètre GroupPath et IncPath dans la vue threads des piles de temps](media/perfview-tts-group-path-inc-path.png)

PerfView propose des conseils sous détaillés le **aide** menu que vous pouvez utiliser pour identifier les goulots d’étranglement dans votre code. En outre, les liens suivants fournissent plus d’informations sur la façon d’utiliser les API pour optimiser votre code de threading de Visual Studio :

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

Vous pouvez également utiliser les nouveaux analyseurs de statique de Visual Studio pour les extensions (package NuGet [ici](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), qui fournissent des conseils sur les meilleures pratiques pour l’écriture d’extensions efficace. Afficher la liste des [analyseurs de kit de développement logiciel Visual Studio](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) et [threading analyseurs](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Si vous ne parvenez pas à résoudre le problème de blocage en raison de dépendances, vous n’avez pas au fil du contrôle (par exemple, si votre extension doit appeler des services VS synchrones sur le thread d’interface utilisateur), nous aimerions en savoir plus. Si vous êtes un membre de notre programme de partenaires Visual Studio, vous pouvez nous contacter en soumettant une demande de support du développeur. Sinon, utilisez l’outil « Signaler un problème » pour envoyer vos commentaires et inclure `"Extension UI Delay Notifications"` dans le titre. Veuillez également inclure une description détaillée de votre analyse.
