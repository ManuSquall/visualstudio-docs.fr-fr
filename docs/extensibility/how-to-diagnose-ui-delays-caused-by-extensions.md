---
title: Diagnostic des retards de l’interface utilisateur de l’extension dans Visual Studio | Microsoft Docs
description: Visual Studio vous avertit si des retards de l’interface utilisateur peuvent être provoqués par une extension. Découvrez comment diagnostiquer ce qui se passe dans votre code d’extension en raison de retards de l’interface utilisateur.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jmartens
ms.workload: multiple
ms.openlocfilehash: 508fdd44a1c73f66d88317b7ec304e810f5f12e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890797"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Guide pratique pour diagnostiquer les délais de l’interface utilisateur causés par les extensions

Lorsque l’interface utilisateur ne répond pas, Visual Studio examine la pile des appels du thread d’interface utilisateur, en commençant par la feuille et en travaillant vers la base. Si Visual Studio détermine qu’un frame de pile d’appels appartient à un module qui fait partie d’une extension installée et activée, il affiche une notification.

![Notification de délai de l’interface utilisateur (absence de réponse)](media/ui-delay-notification-in-vs.png)

La notification informe l’utilisateur que le délai de l’interface utilisateur (autrement dit, l’absence de réponse dans l’interface utilisateur) peut avoir été le résultat du code d’une extension. Il fournit également aux utilisateurs des options pour désactiver l’extension ou les notifications futures pour cette extension.

Ce document décrit comment vous pouvez diagnostiquer les éléments de votre code d’extension provoquant des notifications de retard de l’interface utilisateur.

> [!NOTE]
> N’utilisez pas l’instance expérimentale de Visual Studio pour diagnostiquer les retards de l’interface utilisateur. Certaines parties de l’analyse de pile d’appels requises pour les notifications de délai de l’interface utilisateur sont désactivées lors de l’utilisation de l’instance expérimentale, ce qui signifie que les notifications de retard de l’interface utilisateur peuvent ne pas être affichées

Une vue d’ensemble du processus de diagnostic est la suivante :
1. Identifiez le scénario de déclenchement.
2. Redémarrez VS avec la journalisation des activités.
3. Démarrez le suivi ETW.
4. Déclenchez la notification pour qu’elle s’affiche à nouveau.
5. Arrêtez le suivi ETW.
6. Examinez le journal d’activité pour connaître l’ID de délai.
7. Analysez le suivi ETW à l’aide de l’ID de délai de l’étape 6.

Dans les sections suivantes, nous allons passer en revue ces étapes plus en détail.

## <a name="identify-the-trigger-scenario"></a>Identifier le scénario de déclencheur

Pour diagnostiquer un retard de l’interface utilisateur, vous devez d’abord identifier ce que (séquence d’actions) entraîne à ce que Visual Studio affiche la notification. Cela vous permet de déclencher la notification ultérieurement lorsque la journalisation est activée.

## <a name="restart-vs-with-activity-logging-on"></a>Redémarrer et avec la journalisation des activités

Visual Studio peut générer un « journal d’activité » qui fournit des informations utiles lors du débogage d’un problème. Pour activer la journalisation des activités dans Visual Studio, ouvrez Visual Studio avec l' `/log` option de ligne de commande. Après le démarrage de Visual Studio, le journal d’activité est stocké à l’emplacement suivant :

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Pour en savoir plus sur la façon dont vous pouvez trouver votre ID VS instance, consultez [outils pour la détection et la gestion des instances de Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Nous utiliserons ce journal d’activité ultérieurement pour obtenir plus d’informations sur les retards de l’interface utilisateur et les notifications associées.

## <a name="starting-etw-tracing"></a>Démarrage du suivi ETW

Vous pouvez utiliser [PerfView](https://github.com/Microsoft/perfview/) pour collecter une trace ETW. PerfView fournit une interface facile à utiliser pour la collecte d’une trace ETW et l’analyse de celle-ci. Pour collecter une trace, utilisez la commande suivante :

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Cela active le fournisseur « Microsoft-VisualStudio », qui est le fournisseur utilisé par Visual Studio pour les événements liés aux notifications de retard de l’interface utilisateur. Il spécifie également le mot clé pour le fournisseur de noyau que PerfView peut utiliser pour générer l’affichage des **piles de temps du thread** .

## <a name="trigger-the-notification-to-appear-again"></a>Déclencher à nouveau l’affichage de la notification

Une fois que PerfView a démarré la collecte de trace, vous pouvez utiliser la séquence d’action de déclenchement (de l’étape 1) pour que la notification s’affiche à nouveau. Une fois la notification affichée, vous pouvez arrêter la collecte de trace pour que PerfView traite et génère le fichier de trace de sortie.

## <a name="stop-etw-tracing"></a>Arrêter le suivi ETW

Pour arrêter la collecte des traces, utilisez simplement le bouton **arrêter la collecte** dans la fenêtre PerfView. Après l’arrêt de la collecte de trace, PerfView traite automatiquement les événements ETW et génère un fichier de trace de sortie.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Examiner le journal d’activité pour connaître l’ID de délai

Comme mentionné précédemment, vous trouverez le journal d’activité sur *%APPDATA%\Microsoft\VisualStudio \<vs_instance_id>\ActivityLog.xml*. Chaque fois que Visual Studio détecte un délai de l’interface utilisateur d’extension, il écrit un nœud dans le journal d’activité avec `UIDelayNotifications` comme source. Ce nœud contient quatre éléments d’informations sur le délai de l’interface utilisateur :

- L’ID de délai de l’interface utilisateur, un numéro séquentiel qui identifie de façon unique un délai de l’interface utilisateur dans une session VS
- L’ID de session, qui identifie de façon unique votre session Visual Studio, du début à la fermeture
- Indique si une notification a été affichée ou non pour le délai de l’interface utilisateur
- L’extension qui a probablement provoqué le retard de l’interface utilisateur

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
> Tous les retards de l’interface utilisateur ne provoquent pas de notification. Par conséquent, vous devez toujours vérifier la **notification indiquée ?** valeur pour identifier correctement le délai d’interface utilisateur approprié.

Une fois que vous avez trouvé le délai d’interface utilisateur correct dans le journal d’activité, notez l’ID de délai de l’interface utilisateur spécifié dans le nœud. Vous utiliserez l’ID pour Rechercher l’événement ETW correspondant à l’étape suivante.

## <a name="analyze-the-etw-trace"></a>Analyser le suivi ETW

Ensuite, ouvrez le fichier de trace. Vous pouvez effectuer cette opération à l’aide de la même instance de PerfView ou en démarrant une nouvelle instance et en définissant le chemin d’accès au dossier actif en haut à gauche de la fenêtre à l’emplacement du fichier de trace.

![Définition du chemin d’accès au dossier dans Perfview](media/perfview-set-path.png)

Ensuite, sélectionnez le fichier de trace dans le volet gauche et ouvrez-le en choisissant **ouvrir** dans le menu contextuel.

> [!NOTE]
> Par défaut, PerfView génère une archive zip. Lorsque vous ouvrez *trace.zip*, il décompresse automatiquement l’archive et ouvre la trace. Vous pouvez ignorer ce code en désactivez la case à cocher **zip** pendant la collecte des traces. Toutefois, si vous envisagez de transférer et d’utiliser des traces sur différents ordinateurs, nous vous recommandons vivement de décocher la case **zip** . Sans cette option, les fichiers PDB requis pour les assemblys Ngen ne sont pas joints à la trace et, par conséquent, les symboles des assemblys Ngen ne sont pas résolus sur l’ordinateur de destination. (Consultez [ce](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) billet de blog pour plus d’informations sur les fichiers PDB pour les assemblys Ngen.)

Le traitement et l’ouverture de la trace peuvent prendre plusieurs minutes. Une fois la trace ouverte, une liste des différents « affichages » s’affiche.

![Vue Résumé de la trace PerfView](media/perfview-summary-view-events-selected.png)

Nous allons tout d’abord utiliser la vue **événements** pour obtenir l’intervalle de temps du délai de l’interface utilisateur :

1. Ouvrez la vue **événements** en sélectionnant `Events` nœud sous la trace et en choisissant **ouvrir** dans le menu contextuel.
2. `Microsoft-VisualStudio/ExtensionUIUnresponsiveness`Dans le volet gauche, sélectionnez «».
3. Appuyez sur entrée

La sélection est appliquée et tous les `ExtensionUIUnresponsiveness` événements s’affichent dans le volet droit.

![Sélection d’événements dans la vue événements](media/perfview-event-selection.png)

Chaque ligne du volet droit correspond à un délai de l’interface utilisateur. L’événement comprend une valeur « ID de délai » qui doit correspondre à l’ID de délai dans le journal d’activité de l’étape 6. Étant donné que `ExtensionUIUnresponsiveness` est déclenché à la fin du délai de l’interface utilisateur, l’horodateur de l’événement (à peu près) marque l’heure de fin du délai de l’interface utilisateur. L’événement contient également la durée du délai. Nous pouvons soustraire la durée de l’horodateur de fin pour obtenir l’horodateur de l’heure de début du retardement de l’interface utilisateur.

![Calcul de l’intervalle de temps de délai de l’interface utilisateur](media/ui-delay-time-range.png)

Dans la capture d’écran précédente, par exemple, l’horodateur de l’événement est 12 125,679 et la durée du délai est 6 143,085 (MS). Donc
* Le début du délai est 12 125,679-6 143,085 = 5 982,594.
* La plage de temps de délai de l’interface utilisateur est comprise entre 5 982,594 et 12 125,679.

Une fois que nous avons l’intervalle de temps, nous pouvons fermer l’affichage des **événements** et ouvrir l’affichage des piles de l' **heure du thread (avec les activités StartStop)** . Cette vue est particulièrement pratique, car souvent les extensions qui bloquent le thread d’interface utilisateur sont simplement en attente sur d’autres threads ou une opération liée aux e/s. Par conséquent, la vue de la pile de l' **UC** , qui est l’option « Go-to » dans la plupart des cas, peut ne pas capturer le temps que le thread passe à bloquer, car il n’utilise pas le processeur pendant ce temps. Les **piles de temps de threads** résolvent ce problème en présentant correctement le temps de blocage.

![Nœud piles de temps de thread (avec activités StartStop) en mode de résumé PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Lors de l’ouverture de la vue **piles de temps du thread** , choisissez le processus **devenv** pour démarrer l’analyse.

![Vue des piles de temps du thread pour l’analyse du délai de l’interface utilisateur](media/ui-delay-thread-time-stacks.png)

Dans l’affichage **piles de temps du thread** , dans l’angle supérieur gauche de la page, vous pouvez définir l’intervalle de temps sur les valeurs calculées à l’étape précédente et appuyer sur **entrée** pour ajuster la plage horaire.

> [!NOTE]
> Déterminer quel thread est le thread d’interface utilisateur (démarrage) peut être non intuitifs si la collecte de trace est démarrée une fois que Visual Studio est déjà ouvert. Toutefois, les premiers éléments de la pile du thread d’interface utilisateur (Startup) sont généralement toujours des dll du système d’exploitation (*ntdll.dll* et *kernel32.dll*) suivis de, `devenv!?` puis `msenv!?` . Cette séquence peut aider à identifier le thread d’interface utilisateur.

 ![Identification du thread de démarrage](media/ui-delay-startup-thread.png)

Vous pouvez également filtrer cette vue en n’incluant que des piles qui contiennent des modules de votre package.

* Définissez **GroupPats** sur un texte vide pour supprimer tout regroupement ajouté par défaut.
* Définissez **IncPats** pour inclure une partie de votre nom d’assembly en plus du filtre de processus existant. Dans ce cas, il doit s’agir de **devenv ; UIDelayR2**.

![Définition de GroupPath et IncPath dans la vue des piles de temps de thread](media/perfview-tts-group-path-inc-path.png)

PerfView dispose de conseils détaillés dans le menu **aide** , qui vous permettent d’identifier les goulots d’étranglement de performances dans votre code. En outre, les liens suivants fournissent plus d’informations sur l’utilisation des API de thread de Visual Studio pour optimiser votre code :

* [https://github.com/Microsoft/vs-threading/blob/master/doc/index.md](https://github.com/Microsoft/vs-threading/blob/master/doc/index.md)
* [https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md)

Vous pouvez également utiliser les nouveaux analyseurs statiques Visual Studio pour les extensions (package NuGet [ici](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), qui fournissent des conseils sur les meilleures pratiques pour l’écriture d’extensions efficaces. Consultez la liste des analyseurs de [Visual Studio SDK](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) et des [analyseurs de thread](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Si vous ne parvenez pas à résoudre la non-réponse en raison des dépendances dont vous n’avez pas le contrôle (par exemple, si votre extension doit appeler les services VS synchrones sur le thread d’interface utilisateur), nous aimerions le savoir. Si vous êtes membre de notre programme partenaires Visual Studio, vous pouvez nous contacter en soumettant une demande de support pour les développeurs. Dans le cas contraire, utilisez l’outil « signaler un problème » pour envoyer vos commentaires et `"Extension UI Delay Notifications"` les inclure dans le titre. Incluez également une description détaillée de votre analyse.
