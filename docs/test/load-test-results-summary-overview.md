---
title: Vue d'ensemble du résumé des résultats des tests de charge
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.summary.view
helpviewer_keywords:
- load test results, summary
- load tests, summary in analyzer
- load tests, results summary
- Load Test Viewer, summary
- load tests, summary in Load Test Viewer
ms.assetid: 326b6c3c-5378-452b-8ca3-ba5a06ab3d41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7cc4cc2af5fb78c181be94863176914c17481e95
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55928723"
---
# <a name="load-test-results-summary-overview"></a>Présentation du récapitulatif des résultats des tests de charge

Après avoir exécuté un test de charge, vous pouvez consulter le résumé du test de charge pour comprendre rapidement les résultats. Ce résumé fournit les résultats clés dans un format compact et facile à lire. Vous pouvez également l'imprimer. Cela rend son utilisation pratique lorsque vous communiquez des résultats aux parties prenantes. Le résumé du test de charge est également la vue par défaut lorsque vous ouvrez un résultat de test de charge d'un précédemment test de charge exécuté. Pour plus d'informations, voir [Procédure : accéder aux résultats des tests de charge à des fins d’analyse](../test/how-to-access-load-test-results-for-analysis.md).

![Mode Résumé](../test/media/ltest_summaryview.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="the-load-test-summary"></a>Récapitulatif du test de charge

Le résumé du test de charge est divisé en sections. Les sections initiales apparaissent en haut du résumé et sont toujours visibles. Lorsque vous consultez le résumé du test de charge, les éléments suivants figurent en premier :

- Informations sur les séries de tests

- Résultats globaux

- Statistique clé : Top 5 des pages les plus lentes

- Statistique clé : Top 5 des tests les plus lents

- Statistique clé : Top 5 des opérations SQL les plus lentes

    > [!NOTE]
    > La section relative aux opérations SQL s'affiche uniquement si le traçage SQL est activé dans le test de charge.

Les sections de fermeture apparaissent à la fin du résumé et peuvent être réduites pour économiser de l‘espace. Les éléments suivants apparaissent à la fin du résumé du test de charge :

- Résultats des tests

- Résultats de la page

- Résultats de la transaction

- Systèmes sous ressources de test

- Ressources du contrôleur et de l'agent

- Erreurs

## <a name="test-run-information"></a>Informations sur les séries de tests

La section des informations relatives à la série de tests contient des informations générales sur la série, dont le nom du test, les heures de début et de fin, et le contrôleur ayant exécuté le test. Elle contient également une description facultative de la série, que vous ajoutez lors de l'exécution du test de charge.

## <a name="overall-results"></a>Résultats globaux

La section relative aux résultats globaux contient une synthèse des résultats du test, dont le nombre de requêtes par seconde, le nombre total de requêtes ayant échoué, le temps de réponse moyen et le temps de réponse moyen de la page.

## <a name="key-statistic-top-5-slowest-pages"></a>Statistique clé : Top 5 des pages les plus lentes

La section relative aux pages les plus lentes contient les 5 premières pages les plus lentes du test de charge. L'URL et le temps de chargement moyens de la page sont affichés pour chaque page. Les pages sont répertoriées dans l'ordre décroissant. Vous pouvez choisir l’URL d’une page pour ouvrir la table **Pages** et obtenir plus de détails sur cette page. Pour plus d'informations, voir [Procédure : afficher le temps de réponse d’une page web](../test/how-to-view-web-page-response-time-in-a-load-test.md).

La valeur du centile pour **95% du temps de réponse de la page (s)** indique que 95 % des pages ont été traitées dans un délai inférieur à cette durée en secondes.

## <a name="key-statistic-top-5-slowest-tests"></a>Statistique clé : Top 5 des tests les plus lents

La section relative aux tests les plus lents contient les 5 premiers tests les plus lents du test de charge. Le nom et la durée moyenne du test sont affichés pour chaque test. Les tests sont répertoriés dans l'ordre décroissant. Vous pouvez choisir le nom d’un test pour ouvrir la table **Tests** et obtenir plus de détails sur ce test. Pour plus d’informations, consultez [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

La valeur du centile pour **95% du temps de test (s)** indique que 95 % des tests ont été effectués dans un délai inférieur à cette durée en secondes.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Statistique clé : Top 5 des opérations SQL les plus lentes

Si le traçage SQL est activé dans le test de charge, la section relative aux requêtes les plus lentes contient les 5 premières requêtes les plus lentes du test de charge. Le nom et la durée de l'opération sont affichés pour chaque test. La durée est affichée en microsecondes (SQL Server 2005) ou en millisecondes (SQL Server 2000 et versions antérieurs). Les tests sont répertoriés dans l'ordre décroissant en fonction de la durée. Vous pouvez choisir le nom d’une opération pour ouvrir la table **Trace SQL** et obtenir plus de détails sur cette opération. Pour plus d’informations, consultez [Table Données de trace SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table).

## <a name="test-results"></a>Résultats des tests

La section relative aux résultats des tests contient une liste de tous les tests et scénarios du test de charge. Le nom du test, le scénario, le nombre de fois où il a été exécuté, le nombre de fois où il a échoué et la durée moyenne du test sont affichés. Vous pouvez choisir le nom d’un test pour ouvrir la table **Tests** et obtenir plus de détails sur ce test. Pour plus d’informations, consultez [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Vous pouvez réduire et développer cette section en cliquant sur la flèche située à gauche du titre de la section.

## <a name="page-results"></a>Résultats de la page

La section relative aux résultats de la page contient la liste de toutes les pages web du test de charge. L'URL, le scénario, le nom du test, le temps de réponse moyen de la page et le compte sont affichés. Vous pouvez choisir l’URL d’une page pour ouvrir la table **Pages** et obtenir plus de détails sur cette page. Pour plus d'informations, voir [Procédure : afficher le temps de réponse d’une page web](../test/how-to-view-web-page-response-time-in-a-load-test.md).

> [!NOTE]
> Vous pouvez réduire et développer cette section en cliquant sur la flèche située à gauche du titre de la section.

## <a name="transaction-results"></a>Résultats de la transaction

La section relative aux résultats de la transaction contient une liste de toutes les transactions du test de charge. Le nom de la transaction, le scénario, le test, le temps de réponse, la durée calendaire et le compte sont affichés. Vous pouvez choisir le nom d’une transaction pour ouvrir la table **Transactions** et obtenir plus de détails sur cette transaction. Pour plus d’informations, consultez [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Vous pouvez réduire et développer cette section en cliquant sur la flèche située à gauche du titre de la section.

Les valeurs de centile signalent les informations de transaction suivantes :

-   90 % du total des transactions ont été effectuées dans un délai inférieur à \<durée> secondes.

-   95 % du total des transactions ont été effectuées dans un délai inférieur à \<durée> secondes.

## <a name="system-under-test-resources"></a>Ressources du système sous test

La section relative aux ressources du système sous test contient une liste d'ordinateurs qui constituent l'ensemble des ordinateurs cibles pour lesquels la charge est générée. Cela inclut tout ordinateur à partir desquels vous rassemblez des ensembles de compteurs autres que les agents ou les contrôleurs. Le nom des ordinateurs, le temps processeur en % et la mémoire disponible sont affichées. Vous pouvez choisir un nom d’ordinateur pour ouvrir le graphique **Système testé** et voir l’utilisation des ressources au fil du temps. Pour plus d’informations, consultez [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Vous pouvez réduire et développer cette section en cliquant sur la flèche située à gauche du titre de la section.

## <a name="controller-and-agent-resources"></a>Ressources du contrôleur et de l’agent

La section relative aux ressources du contrôleur et de l'agent contient une liste des ordinateurs utilisés pour exécuter le test. Le nom des ordinateurs, le temps processeur en % et la mémoire disponible sont affichées. Vous pouvez choisir un nom d’ordinateur pour ouvrir le graphique **Contrôleur et agents** et voir l’utilisation des ressources au fil du temps. Pour plus d’informations, consultez [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Vous pouvez réduire et développer cette section en cliquant sur la flèche située à gauche du titre de la section.

## <a name="errors"></a>Erreurs

La section relative aux erreurs contient une liste de toutes les erreurs qui se sont produites durant le test de charge. Le type et sous-type de l'erreur, le compte et le dernier message sont affichés. Vous pouvez choisir une erreur pour ouvrir la table **Erreurs** et obtenir plus de détails sur cette erreur. Pour plus d’informations, consultez [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Vous pouvez réduire et développer cette section en cliquant sur la flèche située à gauche du titre de la section.

## <a name="print-a-summary"></a>Imprimer un récapitulatif

Vous pouvez imprimer le récapitulatif du test de charge en choisissant **Imprimer** dans le menu contextuel du récapitulatif. Vous pouvez d’abord obtenir un aperçu de l’impression en choisissant **Aperçu avant impression** dans le menu contextuel du récapitulatif. Vous pouvez également effectuer l'impression directement à partir de l'écran d'aperçu.

## <a name="see-also"></a>Voir aussi

- [Analyser les violations des règles de seuil](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)