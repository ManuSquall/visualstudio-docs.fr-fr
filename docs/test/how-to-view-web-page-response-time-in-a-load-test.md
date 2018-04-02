---
title: Temps de réponse d’une page dans un test de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 055bb9b9ae369cd6b62741f7d23295c34b7d1d32
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Comment : afficher le temps de réponse d’une page web dans un test de charge à l’aide de l’analyseur de test de charge

Le temps nécessaire pour charger chaque page web est appelé « *temps de réponse* ». Lorsque vous créez un test de performances de site web, vous pouvez définir un objectif de temps de réponse pour chaque requête de page web de votre test de performances de site web.

Si vous exécutez votre test de performances de site Web sous contrainte dans un test de charge, vous pouvez analyser les informations suivantes pour chaque page :

-   Temps de réponse moyen pour la page.

-   Pourcentage des itérations de test qui atteignent l'objectif de temps de réponse pour la page.

-   Vous pouvez analyser des temps de réponse de page web en utilisant la vue Tables ou la vue Graphiques dans l’analyseur de test de charge :

-   Analyse des temps de réponse de la page web dans la vue Tables

-   Analyse des temps de réponse de la page web dans la vue Graphiques

## <a name="view-response-time-data-in-a-table"></a>Afficher les données de temps de réponse dans un tableau

### <a name="to-view-response-time-data-in-a-table"></a>Pour consulter les données de temps de réponse dans un tableau

1.  Dans l’analyseur de test de charge, choisissez **Tables** dans la barre d’outils pour vérifier que la grille des tables est affichée.

2.  Dans la zone de liste déroulante **Table**, sélectionnez **Pages**.

3.  Les données de chaque page s'affichent dans la grille. Généralement, les colonnes suivantes s'affichent :

    |||
    |-|-|
    |**Page**|Nom de la page web.|
    |**Scénario**|Nom du scénario. Important si votre test de performances de site Web comporte plusieurs scénarios.|
    |**Test**|Nom du test de performances de site Web. Important si vous possédez plusieurs tests de performances de site Web dans votre test de charge.|
    |**Network**|Type de réseau.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
    |**Total**|Nombre total de requêtes effectuées pour la page web. Il s'agit du nombre total d'itérations dans le test de charge.|
    |**Moy.**|Temps de réponse moyen de la page.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
    |**Min**|Temps de réponse minimum de la page.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
    |**Médian**|Temps de réponse médian de la page.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
    |**90%**|90e centile pour le temps de réponse. Cela indique que 90 % des pages ont répondu plus rapidement que ce nombre, et 10 % des pages ont répondu plus lentement.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
    |**95%**|95e centile pour le temps de réponse. Cela indique que 95 % des pages ont répondu plus rapidement que ce nombre, et 5 % des pages ont répondu plus lentement.|
    |**99%**|99e centile pour le temps de réponse. Cela indique que 99 % des pages ont répondu plus rapidement que ce nombre, et 1 % des pages ont répondu plus lentement.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
    |**Max**|Temps de réponse maximum de la page.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
    |**Écart type**|Par défaut, les données d'écart type ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
    |**Temps de réponse de la page**|Temps de réponse moyen pour toutes les requêtes effectuées pour la page web.|
    |**Objectif**|Objectif de temps de réponse de la page. Il s'agit d'une valeur constante pour la page. **Remarque :** L’objectif de temps de réponse de la page n’apparaît que quand l’objectif a été défini pour la requête dans le test de performances web.|
    |**% correspondant à l’objectif**|Pourcentage de requêtes effectuées pour la page web qui a atteint l’objectif de temps de réponse.|

 Pour plus d’informations, consultez [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Afficher les données de temps de réponse dans un graphique

Vous pouvez également consulter les données de temps de réponse dans un graphique pour savoir comment elles changent avec le temps pendant votre test de charge. Ces données sont particulièrement utiles si votre modèle de charge augmente pendant l’exécution du test (par exemple, si vous utilisez le modèle de charge par étape). Pour plus d’informations, consultez [Modification des modèles de charge en modèle d’activités des utilisateurs virtuels](../test/edit-load-patterns-to-model-virtual-user-activities.md).

### <a name="to-view-response-time-data-in-a-graph"></a>Pour consulter les données de temps de réponse dans un graphique

1.  Dans l’analyseur de test de charge, choisissez **Graphiques** dans la barre d’outils pour vérifier que le graphique est affiché.

2.  Dans la fenêtre **Compteurs**, développez le nœud du scénario qui vous intéresse (par exemple, `Scenario1`).

3.  Développez le nœud du test de performances de site Web qui vous intéresse.

4.  Développez le nœud **Pages**.

5.  Développez le nœud de la page qui vous intéresse.

6.  Cliquez avec le bouton droit sur **% pages correspondant à l’objectif**, puis choisissez **Afficher le compteur sur le graphique**.

     Les données sont ajoutées au graphique.

7.  (Facultatif) Répétez l'étape précédente pour Avg. Page Time, Page Response Time Goal et Total Pages.

    > [!NOTE]
    > Page Response Time Goal est une valeur constante.

 Pour plus d’informations, consultez [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Guide pratique pour accéder aux résultats des tests de charge pour l’analyse](../test/how-to-access-load-test-results-for-analysis.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)