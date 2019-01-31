---
title: Analyse des résultats des tests de charge
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: c9894c62975da0353fd9e920fa5596e7e0ebeb26
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935850"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Analyse des résultats des tests de charge à l’aide de l’analyseur de test de charge

Localisez les goulots d’étranglement, identifiez les erreurs et mesurez les améliorations dans votre application quand vous utilisez **l’analyseur de test de charge**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Analysez les résultats de test de charge des manières suivantes :

-   Surveillez un test de charge pendant son exécution.

-   Analysez un test de charge après son exécution.

-   Consultez les résultats d'un test de charge précédent.

Vous pouvez également créer des rapports qui comparent deux ou plusieurs rapports d'analyse de tendance à partager avec les parties prenantes. Consultez [Création de rapports sur les résultats des tests de charge pour les comparaisons de tests ou l’analyse de tendances](../test/compare-load-test-results.md).

Vous pouvez effectuer ces tâches si vous exécutez votre test de charge à partir de Visual Studio Enterprise ou de la ligne de commande, et si vous exécutez votre test de charge sur un seul ordinateur ou sur un ordinateur distant.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Différences entre l’analyse d’une exécution de test de charge et d’un test de charge terminé

 Quand vous exécutez un test de charge, **l’analyseur de test de charge** s’affiche sous un onglet distinct, en indiquant le nom de votre test de charge et l’heure de démarrage du test (par exemple **LoadTest1 [12:40 PM]**). Lorsqu'un test de charge est exécuté, un plus petit groupe des données de compteur de performance est conservé dans la mémoire. Vous pouvez surveiller ce groupe de données lorsque votre test de charge est exécuté. Une fois le test de charge terminé, vous pouvez analyser le groupe de données complet à partir de la base de données. Il existe des différences entre la nature des données affichées lorsqu'un test de charge est exécuté et le type de données que vous pouvez afficher à l'issue de l'exécution d'un test de charge. Par exemple, 90 % et 95 % des données de temps de réponse ne sont pas calculés tant que le test de charge n'est pas terminé. Il existe également des différences dans les fonctionnalités des outils disponibles pour analyser les données.

 Quand vous exécutez le test de charge, deux vues sont disponibles : la vue **Graphiques** et la vue **Tables**. La vue **Graphiques** vous permet de tracer sur un graphique les compteurs de performance collectés. La vue **Tables** fournit des informations sur chacun des tests, pages, transactions et requêtes collectés. Vous obtenez également une table qui répertorie les erreurs.

 Par défaut, quand la série de tests de charge est terminée, la vue **Résumé** s’affiche. Vous pouvez basculer entre les vues **Résumé**, **Graphiques**, **Tables** et **Details** à l’aide de la barre d’outils. Vous pouvez ancrer ou rendre flottante la fenêtre de **l’analyseur de test de charge** à l’aide des techniques usuelles de manipulation de fenêtre Visual Studio. Quand vous analysez les séries de tests de charge terminées, vous pouvez avoir plusieurs instances de **l’analyseur de test de charge** ouvertes en même temps pour comparer différentes séries de tests de charge.

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-|-|
|**Accès aux résultats de votre test de charge :** Lorsque vous exécutez un test de charge avec l’éditeur de test de charge, les résultats s’affichent automatiquement et le test de charge en cours d’exécution apparaît dans **l’Analyseur de test de charge**.|-   [Guide pratique pour accéder aux résultats des tests de charge à des fins d’analyse](../test/how-to-access-load-test-results-for-analysis.md)|
|**Ajouter des notes d’analyse à votre test de charge :** vous pouvez ajouter des commentaires au test de charge quand vous effectuez votre analyse. Les commentaires sont stockés définitivement avec le résultat du test de charge. La description que vous entrez s’affiche également dans la colonne **Description** associée au test de charge dans la boîte de dialogue **Ouvrir et gérer des résultats des tests de charge** de l’éditeur de test de charge.<br /><br /> Pour plus d'informations, voir [Procédure : accéder aux résultats des tests de charge à des fins d’analyse](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> En outre, les commentaires s'affichent lorsque vous créez un rapport Excel pour les résultats de test de charge.<br /><br /> Pour plus d’informations, consultez [Création de rapports sur les résultats des tests de charge pour les comparaisons de tests ou l’analyse de tendances](../test/compare-load-test-results.md).||
|**Analyse des résultats de votre test de charge :** après avoir accédé aux données d’exécution des tests de charge, vous pouvez analyser les données résultantes. Vous pouvez consulter le Résumé du test de charge pour comprendre rapidement les résultats. Ce résumé affiche les résultats clés dans un format compact et facile à lire.<br /><br /> Vous pouvez l'imprimer. Cela rend son utilisation pratique lorsque vous communiquez des résultats aux parties prenantes.<br /><br /> Vous pouvez analyser les détails des résultats du test de charge en utilisant les graphiques et les tables dans les résultats, notamment **Erreurs**, **Pages**, **Requêtes**, **SQL Trace**, **Tests**, **Seuils**  et **Transactions**.|-   [Vue d’ensemble du résumé des résultats des tests de charge](../test/load-test-results-summary-overview.md)<br />-   [Guide pratique pour afficher le temps de réponse d’une page web](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Analyse des violations des règles de seuil](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Analyse de l’activité des utilisateurs virtuels dans les résultats des tests de charge pour isoler les problèmes de performances :** vous pouvez utiliser le graphique d’activités des utilisateurs virtuels pour visualiser ce que font les utilisateurs virtuels durant un test de charge. Cela peut vous aider à isoler les pics d’activité d’une UC ou les chutes d’activité des requêtes par seconde, et déterminer les tests ou les pages en cours d’exécution pendant ces pics ou ces chutes.|-   [Analyse de l’activité des utilisateurs virtuels dans la vue Détails](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|