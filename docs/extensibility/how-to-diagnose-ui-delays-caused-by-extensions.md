---
title: "Diagnostic d’extension de l’interface utilisateur de retards dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
author: PooyaZv
ms.author: pozandev
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9dede2f30a9d91e94bda3183deaae337e4c556dc
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Comment : diagnostiquer l’interface utilisateur des retards causés par des extensions

Lorsque l’interface utilisateur cesse de répondre, Visual Studio examine la pile des appels du thread d’interface utilisateur, en commençant par la feuille et progresse vers la base. Si Visual Studio détermine qu’un frame de pile des appels appartienne à un module qui fait partie d’une extension installée et activée, il affiche une notification.

![Délai d’interface utilisateur (problème de blocage) Notification](media/ui-delay-notification-in-vs.png)

La notification informe l’utilisateur que le délai de l’interface utilisateur (par exemple, le problème de blocage dans l’interface utilisateur) est peut-être le résultat du code à partir d’une extension. Il fournit également l’utilisateur avec des options pour désactiver l’extension ou les futures notifications pour cette extension.

Ce document décrit comment vous pouvez diagnostiquer dans votre code d’extension de l’origine des notifications de délai de l’interface utilisateur. 

> [!NOTE]
> N’utilisez pas l’instance expérimentale de Visual Studio pour diagnostiquer les retards d’interface utilisateur. Certaines parties de l’analyse de la pile des appels requis pour les notifications de délai de l’interface utilisateur sont désactivées lors de l’utilisation de l’instance expérimentale, c'est-à-dire que les notifications de délai de l’interface utilisateur ne peuvent pas être affichées.

Une vue d’ensemble du processus de diagnostic est la suivante :
1. Identifiez le scénario de déclencheur.
2. Redémarrez Visual Studio avec l’activité d’ouverture de session.
3. Démarrer le suivi ETW.
4. Déclencher la notification s’affiche plus.
5. Arrêter le suivi ETW.
6. Examinez le journal d’activité pour obtenir l’ID de délai.
7. Analyser le suivi ETW à l’aide des ID de délai à l’étape 6.

Dans les sections suivantes, nous verrons ces étapes plus en détail.

## <a name="identifying-the-trigger-scenario"></a>Identifier le scénario de déclencheur

Pour de diagnostiquer un délai de l’interface utilisateur, vous devez d’abord idetify (séquence d’actions) provoque Visual Studio pour afficher la notification. Il s’agit afin de vous en mesure de déclencher la notification ultérieurement avec la journalisation activée.

## <a name="restarting-vs-with-activity-logging-on"></a>Le redémarrage de Visual Studio avec l’activité d’ouverture de session

Visual Studio peut générer un journal d’activité « » qui fournit des informations utiles lors du débogage d’un problème. Pour activer sur l’activité de journalisation dans Visual Studio, démarrez Visual Studio avec le `/log` option de ligne de commande. Après le démarrage de Visual Studio, le journal d’activité est stocké dans l’emplacement suivant :

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Pour en savoir plus sur la façon dont vous pouvez trouver votre VS ID d’instance, consultez [outils de détection et la gestion des instances de Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Plus tard, nous utiliserons ce journal d’activité pour obtenir plus d’informations sur les retards d’interface utilisateur et notifications relatives.

## <a name="starting-etw-tracing"></a>Démarrer le suivi ETW

Vous pouvez utiliser [PerfView](https://github.com/Microsoft/perfview/) pour collecter un suivi ETW. PerfView fournit une interface facile à utiliser pour collecter un suivi ETW et pour les analyser. Utilisez la commande suivante pour recueillir une trace :

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Ainsi, le fournisseur de « Microsoft-VisualStudio », qui est le fournisseur de que Visual Studio utilise pour les événements associés aux notifications de délai de l’interface utilisateur. Il spécifie également le mot clé pour le fournisseur de noyau PerfView peut utiliser pour générer la vue « Threads des piles de temps ».

## <a name="triggering-the-notification-to-appear-again"></a>Déclenche la notification s’affiche plus

Une fois que PerfView a démarré la collection de la trace, vous pouvez utiliser la séquence d’actions de déclencheur (à l’étape 1) pour la notification s’affiche plus. Une fois la notification est affichée, vous pouvez arrêter la collection de PerfView traiter et générer le fichier de sortie de trace.

## <a name="stopping-etw-tracing"></a>Arrêter le suivi ETW

Pour arrêter la collecte de trace, utilisez simplement le `Stop collection` bouton dans la fenêtre PerfView. Après avoir arrêté la collection de la trace, PerfView traitera automatiquement les événements ETW et génère un fichier de sortie.

## <a name="examining-the-activity-log-to-get-the-delay-id"></a>Examiner le journal d’activité pour obtenir l’ID de délai

Comme mentionné précédemment, vous pouvez trouver le journal d’activité à `%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml`. Chaque fois que Visual Studio détecte une extension du délai de l’interface utilisateur, il écrit un nœud dans le journal d’activité avec `UIDelayNotifications` comme source. Ce nœud contient quatre éléments d’information sur le délai de l’interface utilisateur :

- L’ID de délai de l’interface utilisateur, un numéro séquentiel qui identifie de façon unique un délai de l’interface utilisateur dans une session Visual Studio
- L’ID de session, qui identifie de façon unique votre session Visual Studio à partir du début à la fermeture
- Indique si une notification a été indiquée pour le délai de l’interface utilisateur
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
> Pas de tous les retards d’interface utilisateur génère une notification. Par conséquent, vous devez toujours vérifier la « Notification indiquée ? » valeur à identifier correctement le délai de l’interface utilisateur de droite.

Après avoir trouvé le délai de l’interface utilisateur correct dans le journal d’activité, notez l’ID de délai de l’interface utilisateur spécifié dans le nœud. L’ID vous permet de rechercher l’événement ETW correspondant à l’étape suivante.

## <a name="analyzing-the-etw-trace"></a>Analyse le suivi ETW

Ensuite, ouvrez le fichier de trace. Pour cela, soit à l’aide de la même instance de PerfView ou en démarre une nouvelle instance et en définissant le chemin d’accès du dossier en cours en haut à gauche de la fenêtre à l’emplacement du fichier de trace.

![Définir le chemin d’accès du dossier dans Perfview](media/perfview-set-path.png)

Ensuite, sélectionnez le fichier de trace dans le volet gauche et ouvrez-le en choisissant Ouvrir dans le menu contextuel ou le contexte.

> [!NOTE]
> Par défaut, PerfView génère une archive Zip. Lorsque vous ouvrez trace.zip, elle automatiquement décompresse l’archive et ouvre la trace. Vous pouvez ignorer cette en désactivant la case « Zip » pendant la collecte de la trace. Toutefois, si vous souhaitez transférer et utiliser les traces sur différentes machines, nous déconseillons fortement décochez la case « Zip ». Sans cette option, les fichiers PDB requis pour les assemblys de Ngen seront accompagnent pas la trace et par conséquent, les symboles à partir des assemblys de Ngen ne seront pas résolus sur l’ordinateur de destination. (Consultez [ce billet de blog](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/) pour plus d’informations sur les fichiers PDB pour les assemblys de Ngen.) 

Il peut prendre plusieurs minutes avant que PerfView traiter et ouvrir la trace. Une fois que la trace est ouverte, une liste de différents « vues » s’affichent dans cette section.

![Affichage de résumé de trace PerfView](media/perfview-summary-view-events-selected.png)

Nous allons tout d’abord utiliser l’affichage « Événements » pour obtenir la plage de temps du délai de l’interface utilisateur :

1. Ouvrez l’affichage « Événements » en sélectionnant le nœud « Événements » dans la trace, ouvrir dans le menu contextuel ou le contexte.
2. Sélectionnez «`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`» dans le volet gauche.
3. Appuyez sur entrée

La sélection est appliquée et toutes les `ExtensionUIUnresponsiveness` événements sont affichés dans le volet droit.

![Sélection des événements dans l’affichage des événements](media/perfview-event-selection.png)

Chaque ligne dans le volet droit correspond à un délai de l’interface utilisateur. L’événement contient une valeur de « Délai ID » qui doit correspondre à l’ID de retard dans le journal d’activité de l’étape 6. Étant donné que `ExtensionUIUnresponsiveness` est déclenché à la fin du délai de l’interface utilisateur, l’horodatage de l’événement (environ) marque l’heure de fin du délai de l’interface utilisateur. L’événement contient également la durée du délai. Nous pouvons soustraire la durée de l’horodatage de fin pour obtenir l’horodatage de lorsque le délai de l’interface utilisateur a démarré.

![Calcul de la plage horaire délai de l’interface utilisateur](media/ui-delay-time-range.png)

Dans la capture d’écran précédente, par exemple, l’horodatage de l’événement est 12,125.679 et la durée du délai est 6,143.085 (ms). Donc
* Le délai de démarrage est 12,125.679-6,143.085 = 5,982.594.
* La période de délai de l’interface utilisateur est 5,982.594 à 12,125.679.

Une fois l’intervalle de temps, nous pouvons fermer l’affichage des événements et ouvrez la vue de « Piles de threads heure (avec les activités de StartStop) ». Cette vue est particulièrement utile, car il est souvent les extensions qui bloquent le thread d’interface utilisateur sont en attente simplement sur les autres threads ou d’une opération d’e/S. Par conséquent, la vue « Pile du processeur », qui est l’option incontournable pour la plupart des cas, ne peut pas capturer le temps du thread, car il n’utilise pas l’UC pendant cette période de blocage. Les piles de threads de temps « » résout ce problème en correctement montrant bloqué heure.

![Nœud de piles de temps (avec les activités de StartStop) de thread dans la vue Résumé de PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Lors de l’ouverture de « Threads des piles de temps » afficher, sélectionnez le processus de « devenv » pour démarrer l’analyse.

![Affichage des piles de temps pour l’analyse de délai de l’interface utilisateur de thread](media/ui-delay-thread-time-stacks.png)

Dans la vue « Threads des piles de temps », en haut à gauche de la page, vous pouvez définir l’intervalle de temps pour les valeurs que nous avons calculé dans l’étape précédente et appuyez sur ENTRÉE pour les piles sont ajustées à cette plage de temps.

> [!NOTE]
> Déterminer le thread est l’interface utilisateur de thread de (démarrage) peut être non intuitive si la collection de la trace est démarrée une fois Visual Studio est déjà ouvert. Toutefois, les premiers éléments sur la pile du thread d’interface utilisateur (démarrage) sont plus probable toujours les DLL système d’exploitation (ntdll.dll et kernel32.dll) suivies de devenv ! ? et puis msenv ! ?. Cette séquence peut aider à identifier le thread d’interface utilisateur.

 ![Qui identifie le thread de démarrage](media/ui-delay-startup-thread.png)

Vous pouvez aussi filtrer cet affichage en incluant uniquement les piles qui contiennent des modules à partir de votre package.

* Texte vide à supprimer n’importe quel regroupement ajouté par défaut la valeur « GroupPats ».
* Ensemble « IncPats » pour inclure la partie de votre nom de l’assembly en plus de filtre de processus existant. Dans ce cas, il doit être « devenv ; UIDelayR2 ».

![Paramètre GroupPath et IncPath dans la vue threads des piles de temps](media/perfview-tts-group-path-inc-path.png)

PerfView détaille les instructions dans le menu d’aide que vous pouvez utiliser pour identifier les goulots d’étranglement de performances dans votre code. En outre, les liens suivants fournissent plus d’informations sur la façon d’utiliser Visual Studio threading API pour optimiser votre code :

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

