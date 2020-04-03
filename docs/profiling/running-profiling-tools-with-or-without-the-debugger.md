---
title: Exécuter des outils de profilage avec ou sans le débogueur | Microsoft Docs
ms.date: 04/02/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf544b3bec9b492f1d1669549ba5501a52f7d5f2
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638810"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Exécuter des outils de profilage avec ou sans le débogueur

Visual Studio propose un choix d’outils de mesure et de profilage des performances. Certains outils, tels que **Utilisation de l’UC** et **Utilisation de la mémoire**, peuvent s’exécuter avec ou sans le débogueur et sur des configurations de build Release ou Debug. Les outils du **Profileur de performances** tels que **Chronologie de l’application** peuvent s’exécuter sur des builds Release ou Debug. Les outils intégrés au débogueur tels que la fenêtre **Outils de diagnostic** et l’onglet **Événements** s’exécutent uniquement pendant les sessions de débogage.

>[!NOTE]
>Vous pouvez utiliser les outils de performances non intégrés au débogueur avec Windows 7 et ultérieur. Windows 8 ou ultérieur est nécessaire pour exécuter les outils de profilage intégrés au débogueur.

Le **Profileur de performances** non intégré au débogueur et les **Outils de diagnostic** intégrés au débogueur fournissent des informations et des expériences différentes. Les outils intégrés au débogueur montrent les points d’arrêt et les valeurs des variables. Les outils non intégrés au débogueur offrent des résultats plus proches de l’expérience des utilisateurs finaux.

Pour vous aider à décider quels outils et résultats utiliser, tenez compte des points suivants :

- Les problèmes de performances externes, comme les problèmes de réactivité du réseau ou d’E/S de fichier, se ressembleront dans tous les outils, qu’ils soient intégrés ou non au débogueur.
- Pour les problèmes provoqués par des appels nécessitant une utilisation importante du processeur, il peut exister des différences de performances considérables entre les builds Release et Debug. Vérifiez si le problème existe dans les builds Release.
- Si le problème se produit uniquement pendant les builds Debug, vous n’avez probablement pas besoin d’exécuter les outils non intégrés au débogueur. Pour les problèmes liés aux builds Release, déterminez si les outils du débogueur vous seront d’une aide quelconque pour un examen approfondi.
- Les builds Release fournissent certaines optimisations comme l’incorporation des constantes et des appels de fonction, le nettoyage des chemins de code inutilisés ou encore des modes de stockage de variables inutilisables par le débogueur. Les valeurs de performances mentionnées dans les outils intégrés au débogueur sont moins précises, car les builds Debug n’offrent pas ces optimisations.
- Le débogueur lui-même affecte les performances quand il effectue des opérations de débogage nécessaires telles que l’interception des exceptions et des événements de chargement de module.
- Les valeurs de performances des builds Release fournies dans les outils du **Profileur de performances** sont plus précises. Les résultats fournis par les outils intégrés au débogueur sont plus utiles en comparaison avec d’autres mesures liées au débogage.

Pour l’utilisation du processeur, vous pouvez exécuter l’outil sur une machine à distance à l’aide des outils de ligne de commande.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Collecter les données de profilage pendant le débogage

Lorsque vous commencez à débogage dans Visual Studio en sélectionnant **Debug** > **Start Debugging** ou en appuyant sur **F5**, la fenêtre **Diagnostic Tools** apparaît par défaut. Pour l’ouvrir manuellement, sélectionnez **Debug** > **Windows** > **Show Diagnostic Tools**. La fenêtre **Outils de diagnostic** affiche des informations sur l’utilisation du processeur, la mémoire de traitement et les événements.

![Outils de diagnostic](../profiling/media/diagnostictools-update1.png "Outils de diagnostic")

- Utilisez l’icône **Paramètres** dans la barre d’outils pour sélectionner s’il y a lieu d’afficher **l’utilisation de la mémoire** ou **l’utilisation du processeur**.

- Sélectionnez **Paramètres** dans la liste déroulante **Paramètres** pour ouvrir les **pages de propriétés des outils de diagnostic** avec davantage d’options.

- Si vous exécutez Visual Studio Enterprise, vous pouvez activer ou désactiver IntelliTrace sous Visual Studio **Tools** > **Options** > **IntelliTrace**.

La session de diagnostic se termine quand vous arrêtez le débogage.

### <a name="the-events-tab"></a>Onglet Événements

Pendant une session de débogage, l’onglet **Événements** de la fenêtre **Outils de diagnostic** liste les événements de diagnostic qui se produisent. Les préfixes de catégories (**Point d’arrêt**, **Fichier** et autres) vous permettent de trouver rapidement la catégorie qui vous intéresse dans la liste, ou d’ignorer celles qui ne vous intéressent pas.

Utilisez la liste déroulante **Filtre** pour filtrer les événements en sélectionnant ou en désélectionnant des catégories d’événements spécifiques.

![Filtre d’événement diagnostique](../profiling/media/diagnosticeventfilter.png "Filtre d’événement diagnostique")

Utilisez la zone de recherche pour trouver une chaîne spécifique dans la liste des événements. Voici les résultats de recherche de la chaîne « name » avec mise en correspondance de quatre événements :

![Recherche d’événements diagnostiques](../profiling/media/diagnosticseventsearch.png "Recherche d’événements diagnostiques")

Pour plus d’informations, consultez [Searching and filtering the Events tab of the Diagnostic Tools window](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Collecter les données de profilage sans débogage

Pour recueillir des données de performances sans débogage, vous pouvez exécuter les outils du **Profileur de performances**. L’exécution de certains des outils de profilage nécessite des privilèges d’administrateur. Vous pouvez ouvrir Visual Studio en tant qu’administrateur, ou vous pouvez exécuter les outils en tant qu’administrateur quand vous démarrez la session de diagnostic.

1. Avec un projet ouvert dans Visual Studio, définissez la configuration de la solution pour **libérer** et sélectionnez **Local Windows Debugger** (ou **Local Machine**) comme cible de déploiement.

1. Sélectionnez **Debug** > **Performance Profiler**, ou appuyez sur **Alt**+**F2**.

1. Dans la page de lancement des diagnostics, sélectionnez un ou plusieurs outils à exécuter. Seuls les outils applicables au type de projet, au système d'exploitation et au langage de programmation sont affichés. Sélectionnez **Afficher tous les outils** pour voir aussi les outils qui sont désactivés pour cette session de diagnostic. Vous pourriez effectuer les choix suivants pour une application C# UWP :

   ![Sélectionner les outils de diagnostic](../profiling/media/diag_selecttool.png "DIAG_SelectTool")

1. Pour démarrer la session de diagnostic, sélectionnez **Démarrer**.

   Pendant l’exécution de la session, certains outils affichent des graphes de données en temps réel dans la page des outils de diagnostic.

    ![Recueillir des données sur le Centre de performance et de diagnostic](../profiling/media/pdhub_collectdata.png "Hub collecte des données")

1. Pour terminer la session de diagnostic, sélectionnez **Arrêter la collecte**.

   Les données analysées apparaissent dans la page **Rapport**.

Vous pouvez enregistrer les rapports et les ouvrir à partir de la liste **Sessions récemment ouvertes** dans la page de lancement des outils de diagnostic.

![Ouvrir un fichier de session de diagnostic enregistré](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

### <a name="the-profiling-report"></a>Le rapport de profilage
 ![Rapport d'outils de diagnostic](../profiling/media/diag_report.png "DIAG_Report")

|||
|-|-|
|![Étape 1](../profiling/media/procguid_1.png "ProcGuid_1")|La chronologie indique la durée de la session de profilage, les événements d'activation du cycle de vie de l'application et les marques utilisateur.|
|![Étape 2](../profiling/media/procguid_2.png "ProcGuid_2")|Vous pouvez limiter le rapport à une partie de la chronologie en faisant glisser les barres bleues pour sélectionner une zone de la chronologie.|
|![Étape 3](../profiling/media/procguid_3.png "ProcGuid_3")|Chaque outil de diagnostic affiche un ou plusieurs graphes principaux. Si votre session de diagnostic comportait plusieurs outils, tous leurs graphes principaux sont affichés.|
|![Étape 4](../profiling/media/procguid_4.png "ProcGuid_4")|Vous pouvez réduire ou développer les graphes de chaque outil.|
|![Étape 5](../profiling/media/procguid_6.png "ProcGuid_6")|Quand les données sont tirées de plusieurs outils, les détails des outils sont collectés sous des onglets.|
|![Étape 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|La partie inférieure du rapport contient une ou plusieurs vues de détails pour chaque outil. Vous pouvez filtrer la vue en sélectionnant des régions de la chronologie.|

## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>Exécuter des sessions de diagnostic sur des applications installées ou en cours d’exécution

Outre le démarrage de votre application à partir du projet Visual Studio, vous pouvez également exécuter les sessions de diagnostic sur d'autres cibles. Par exemple, vous souhaiterez peut-être diagnostiquer les problèmes de performances sur une application installée à partir du Windows Store. Dans le Profileur de performance, sélectionnez parmi la liste d’abandon en vertu **de La cible de changement**.

![Choisir la cible d'analyse des outils de diagnostic](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")

Vous pouvez démarrer des applications qui sont déjà installées, ou attacher les outils de diagnostic à des applications et des processus qui sont déjà en cours d’exécution.

Si vous choisissez **Exécutable** comme cible d’analyse, vous pouvez entrer le chemin vers un .exe sur une machine locale ou *distante.* Dans les deux cas, le *.exe* fonctionne localement. Cependant, nous vous recommandons de profiler votre application en ouvrant la solution dans Visual Studio.

Pour une application UWP, lorsque vous **sélectionnez l’application Running App** ou **l’application installée,** vous sélectionnez l’application à partir d’une liste qui trouve les applications sur la cible de déploiement spécifiée. Cette cible peut être un ordinateur local ou distant. Pour profiler une application UWP sur une machine à distance, vous devez sélectionner **Universal (Protocole Non crypté)** dans la boîte de dialogue **Remote Connections.**

![Choisir une application en cours d'exécution ou installée pour le diagnostic](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")

> [!NOTE]
> Pour d’autres scénarios nécessitant une utilisation à distance des outils de profilage, voir [Les performances de l’application Measure de la ligne de commande](../profiling/profile-apps-from-command-line.md). Vous pouvez utiliser les outils de ligne de commande avec L’utilisation de processeur et l’outil d’allocation d’objets .NET.

## <a name="see-also"></a>Voir aussi

Voici quelques billets de blog et articles MSDN de l’équipe de développement Diagnostics :
- [Magazine MSDN : Analyser les performances pendant le débogage dans Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx)

- [Magazine MSDN : IntelliTrace permet de diagnostiquer les problèmes plus rapidement](https://msdn.microsoft.com/magazine/dn973014.aspx)

- [Billet de blog : Diagnosing Event Handler Leaks with the Memory Usage Tool in Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)

- [Vidéo : Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)

- [Vidéo : Debugging Performance Issues Using Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)

- [Conseils sur les performances : Performance Information at-a-glance while Debugging with Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)

- [Diagnostic Tools debugger window in Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)

- [IntelliTrace dans Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
