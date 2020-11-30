---
title: Temps de réponse d’une page dans un test de charge
description: Le temps nécessaire à la chargement d’une page Web est le temps de réponse. Découvrez comment définir un objectif de temps de réponse pour chaque requête de page Web dans votre test de performances de site Web.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a20e8dc21e2ff5d76ea582b6ea3a9a0e36f7ed74
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328650"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Guide pratique pour afficher le temps de réponse d’une page web dans un test de charge à l’aide de l’analyseur de test de charge

Le temps nécessaire au chargement de chaque page Web est appelé temps de *réponse*. Lorsque vous créez un test de performances web, vous pouvez définir un objectif de temps de réponse pour chaque requête de page web de votre test de performances web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Si vous exécutez votre test de performances web sous contrainte dans un test de charge, vous pouvez analyser les informations suivantes pour chaque page :

- Temps de réponse moyen pour la page.

- Pourcentage des itérations de test qui atteignent l'objectif de temps de réponse pour la page.

- Vous pouvez analyser les temps de réponse de la page Web en utilisant la vue tables ou la vue graphiques dans l' **Analyseur de test de charge**:

- Analyse des temps de réponse de la page web dans la vue Tables

- Analyse des temps de réponse de la page web dans la vue Graphiques

## <a name="view-response-time-data-in-a-table"></a>Afficher les données de temps de réponse dans un tableau

1. Dans l' **Analyseur de test de charge**, choisissez **tables** dans la barre d’outils pour vous assurer que la grille de la table est affichée.

2. Dans la zone de liste déroulante **Table**, sélectionnez **Pages**.

3. Les données de chaque page s'affichent dans la grille. Généralement, les colonnes suivantes s'affichent :

   |En-tête de colonne|Description|
   |-|-|
   |**Page**|Nom de la page web.|
   |**Scénario**|Nom du scénario. Important si votre test de performances web comporte plusieurs scénarios.|
   |**Test**|Nom du test de performances web. Important si vous possédez plusieurs tests de performances web dans votre test de charge.|
   |**Réseau**|Type de réseau.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
   |**Total**|Nombre total de requêtes effectuées pour la page web. Il s'agit du nombre total d'itérations dans le test de charge.|
   |**Moy.**|Temps de réponse moyen de la page.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
   |**Min**|Temps de réponse minimum de la page.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
   |**Médiane**|Temps de réponse médian de la page.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
   |**90%**|90e centile pour le temps de réponse. Cela indique que 90 % des pages ont répondu plus rapidement que ce nombre, et 10 % des pages ont répondu plus lentement.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
   |**95%**|95e centile pour le temps de réponse. Cela indique que 95 % des pages ont répondu plus rapidement que ce nombre, et 5 % des pages ont répondu plus lentement.|
   |**99 %**|99e centile pour le temps de réponse. Cela indique que 99 % des pages ont répondu plus rapidement que ce nombre, et 1 % des pages ont répondu plus lentement.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
   |**Max**|Temps de réponse maximum de la page.<br /><br /> Par défaut, ces données ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
   |**STD dev**|Par défaut, les données d'écart type ne sont pas collectées. Pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud de paramètre d’exécution à changer. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **AllIndividualDetails**.|
   |**Temps de réponse de la page**|Temps de réponse moyen pour toutes les requêtes effectuées pour la page web.|
   |**Objectif**|Objectif de temps de réponse de la page. Il s'agit d'une valeur constante pour la page. **Remarque :**  L’objectif de temps de page s’affiche uniquement lorsque l’objectif a été défini pour la requête dans le test de performances de site Web.|
   |**% correspondant à l’objectif**|Pourcentage de requêtes effectuées pour la page web qui a atteint l’objectif de temps de réponse.|

   Pour plus d’informations, consultez [analyser les résultats et les erreurs des tests de charge dans la vue tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Afficher les données de temps de réponse dans un graphique

Vous pouvez également consulter les données de temps de réponse dans un graphique pour savoir comment elles changent avec le temps pendant votre test de charge. Ces données sont particulièrement utiles si votre modèle de charge augmente pendant l'exécution du test (par exemple, si vous utilisez le modèle de charge par étape). Pour plus d’informations, consultez [Modifier les modèles de charge en modèle d’activités des utilisateurs virtuels](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Pour consulter les données de temps de réponse dans un graphe :

1. Dans l' **Analyseur de test de charge**, choisissez **graphiques** dans la barre d’outils pour vous assurer que le graphique est affiché.

2. Dans la fenêtre **Compteurs**, développez le nœud du scénario qui vous intéresse (par exemple, `Scenario1`).

3. Développez le nœud du test de performances web qui vous intéresse.

4. Développez le nœud **Pages**.

5. Développez le nœud de la page qui vous intéresse.

6. Cliquez avec le bouton droit sur **% pages correspondant à l’objectif**, puis choisissez **Afficher le compteur sur le graphique**.

    Les données sont ajoutées au graphique.

7. Facultatif Répétez l’étape précédente pour **moy. heure** de la page, **objectif du temps de réponse** de la page et **nombre total de pages**.

   > [!NOTE]
   > **Objectif de temps de réponse** a une valeur constante.

   Pour plus d’informations, consultez [analyser les résultats des tests de charge dans la vue graphiques](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Comment : accéder aux résultats des tests de charge pour l’analyse](../test/how-to-access-load-test-results-for-analysis.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
