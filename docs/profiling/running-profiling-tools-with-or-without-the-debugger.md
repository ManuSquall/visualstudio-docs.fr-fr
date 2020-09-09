---
title: Exécuter des outils de profilage avec ou sans le débogueur | Microsoft Docs
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 147a7dbc029ae894a0054837e92feb0108dc19b4
ms.sourcegitcommit: f8d14fab194fcb30658f23f700da07d35ffc9d4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89561586"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Exécuter des outils de profilage avec ou sans le débogueur

Visual Studio propose un choix d’outils de mesure et de profilage des performances. Certains outils, tels que l’utilisation de l’UC et l’utilisation de la mémoire, peuvent s’exécuter avec ou sans le débogueur, ainsi que pour les configurations de build de mise en version ou de débogage. Les outils qui s’affichent dans la [fenêtre outils de diagnostic](../profiling/profiling-feature-tour.md#view-performance-while-debugging) s’exécutent uniquement pendant une session de débogage. Les outils qui s’affichent dans le [profileur de performances](../profiling/profiling-feature-tour.md#post_mortem) s’exécutent sans le débogueur et vous analysez les résultats une fois que vous avez choisi d’arrêter et de collecter des données (pour l’analyse après mortem).

>[!NOTE]
>Vous pouvez utiliser les outils de performances non intégrés au débogueur avec Windows 7 et ultérieur. Windows 8 ou ultérieur est nécessaire pour exécuter les outils de profilage intégrés au débogueur.

Le Profileur de performances non intégré au débogueur et les Outils de diagnostic intégrés au débogueur fournissent des informations et des expériences différentes. Les outils intégrés au débogueur montrent les points d’arrêt et les valeurs des variables. Les outils non intégrés au débogueur offrent des résultats plus proches de l’expérience des utilisateurs finaux.

Pour déterminer les outils et les résultats à utiliser, prenez en compte les éléments suivants :

- Les problèmes de performances externes, comme les problèmes de réactivité du réseau ou d’E/S de fichier, se ressembleront dans tous les outils, qu’ils soient intégrés ou non au débogueur.
- Pour les problèmes provoqués par les appels nécessitant une utilisation intensive du processeur, il peut y avoir des différences de performances considérables entre les versions release et Debug. Vérifiez si le problème existe dans les versions release.
- Si le problème se produit uniquement pendant les versions de débogage, vous n’avez probablement pas besoin d’exécuter les outils de non-débogage. Pour les problèmes de version Release, déterminez si les outils du débogueur vous aideront à approfondir l’investigation.
- Les builds Release fournissent certaines optimisations comme l’incorporation des constantes et des appels de fonction, le nettoyage des chemins de code inutilisés ou encore des modes de stockage de variables inutilisables par le débogueur. Les nombres de performances dans les outils intégrés au débogueur sont moins précis, car les versions de débogage n’ont pas ces optimisations.
- Le débogueur lui-même modifie les performances, car il effectue des opérations de débogueur telles que l’interception des événements d’exception et de chargement de module.
- Les valeurs de performances des builds Release fournies dans les outils du Profileur de performances sont plus précises. Les résultats fournis par les outils intégrés au débogueur sont plus utiles en comparaison avec d’autres mesures liées au débogage.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Collecter les données de profilage pendant le débogage

Quand vous démarrez le débogage dans Visual Studio en sélectionnant **Déboguer**  >  **Démarrer**le débogage, ou en appuyant sur **F5**, la fenêtre de **outils de diagnostic** s’affiche par défaut. Pour l’ouvrir manuellement, sélectionnez **Déboguer**  >  **fenêtres**  >  **afficher les outils de diagnostic**. La fenêtre **Outils de diagnostic** affiche des informations sur l’utilisation du processeur, la mémoire de traitement et les événements.

![Capture d’écran de la fenêtre Outils de diagnostic](../profiling/media/diagnostictoolswindow.png " Fenêtre Outils de diagnostic")

- Utilisez l’icône **Paramètres** dans la barre d’outils pour sélectionner si vous souhaitez afficher **Utilisation de la mémoire**, **Analyse de l’IU** ou **Utilisation de l’UC**.

- Sélectionnez **paramètres** dans la liste déroulante **paramètres** pour ouvrir les **pages de propriétés outils de diagnostic** avec davantage d’options.

- Si vous exécutez Visual Studio Enterprise, vous pouvez activer ou désactiver IntelliTrace en accédant à **Outils**  >  **options**  >  **IntelliTrace**.

La session de diagnostic se termine quand vous arrêtez le débogage.

Pour plus d'informations, consultez les pages suivantes :

- [Mesurer les performances d’application en analysant l’utilisation de l’UC](../profiling/beginners-guide-to-performance-profiling.md)
- [Mesurer l’utilisation de la mémoire dans Visual Studio](../profiling/memory-usage.md)

### <a name="the-events-tab"></a>Onglet Événements

Pendant une session de débogage, l’onglet Événements de la fenêtre Outils de diagnostic liste les événements de diagnostic qui se produisent. Le *point d’arrêt*des préfixes de catégorie, le *fichier*, etc. vous permettent d’analyser rapidement la liste d’une catégorie, ou d’ignorer les catégories qui ne vous intéressent pas.

Utilisez la liste déroulante **filtre** pour filtrer les événements dans et hors de l’affichage, en sélectionnant ou en effaçant des catégories spécifiques d’événements.

![Capture d’écran du filtre des événements de diagnostic](../profiling/media/diagnosticeventfilter.png "Filtre d’événement de diagnostic")

Utilisez la zone de recherche pour trouver une chaîne spécifique dans la liste des événements. Voici les résultats d’une recherche portant sur le *nom* de chaîne qui correspond à quatre événements :

![Capture d’écran de la recherche d’événements de diagnostic](../profiling/media/diagnosticseventsearch.png "Recherche d’événements de diagnostic")

Pour plus d’informations, consultez [Searching and filtering the Events tab of the Diagnostic Tools window](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Collecter les données de profilage sans débogage

Pour recueillir des données de performances sans débogage, vous pouvez exécuter les outils du Profileur de performances.

1. Avec un projet ouvert dans Visual Studio, définissez la configuration de solution sur **Release**, puis sélectionnez **débogueur Windows local**   (ou **ordinateur local**) comme cible de déploiement.

1. Sélectionnez **Déboguer**le  >  **profileur de performances**ou appuyez sur **ALT** + **F2**.

1. Sur la page lancement des outils de diagnostic, sélectionnez un ou plusieurs outils à exécuter. Seuls les outils applicables au type de projet, au système d’exploitation et au langage de programmation sont affichés. Sélectionnez **Afficher tous les outils** pour voir aussi les outils qui sont désactivés pour cette session de diagnostic.

   ![Capture d’écran des outils de diagnostic](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Pour démarrer la session de diagnostic, sélectionnez **Démarrer**.

   Pendant l’exécution de la session, certains outils affichent des graphiques de données en temps réel sur la page outils de diagnostic, ainsi que des contrôles pour suspendre et reprendre la collecte des données.

    ![Capture d’écran de la collecte de données sur le Hub performances et diagnostics](../profiling/media/diaghubcollectdata.png "Collecte de données par le Hub")

1. Pour terminer la session de diagnostic, sélectionnez **Arrêter la collecte**.

   Les données analysées s’affichent sur la page du **rapport** .

Vous pouvez enregistrer les rapports et les ouvrir à partir de la liste **sessions récemment ouvertes** sur la page de lancement de outils de diagnostic.

![Capture d’écran de Outils de diagnostic liste des sessions récemment ouvertes](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

Pour plus d'informations, consultez les pages suivantes :

- [Analyser l’utilisation de l’UC](../profiling/cpu-usage.md)
- [Analyser l’utilisation de la mémoire pour le code .NET](../profiling/dotnet-alloc-tool.md)
- [Analyser l’utilisation de la mémoire](../profiling/analyze-memory-usage.md)
- [Analyser les performances du code asynchrone .NET](../profiling/analyze-async.md)
- [Analyser les performances de la base de données](../profiling/analyze-database.md)
- [Analyser l’utilisation du GPU](../profiling/gpu-usage.md)

## <a name="collect-profiling-data-from-the-command-line"></a>Collecter les données de profilage à partir de la ligne de commande

Pour mesurer les données de performances à partir de la ligne de commande, vous pouvez utiliser VSDiagnostics.exe, qui est inclus avec Visual Studio ou le Outils de contrôle à distance. Cela est utile pour capturer les traces de performances sur les systèmes où Visual Studio n’est pas installé, ou pour générer un script pour la collecte des traces de performances. Pour obtenir des instructions détaillées, consultez [mesurer les performances de l’application à partir de la ligne de commande](../profiling/profile-apps-from-command-line.md).