---
title: Volet Compteurs pour l’analyse des tests de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, counters panel
ms.assetid: e1a388d7-5d33-4631-931a-5653ac4aefdc
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 9e693872784519f5cdcacbd0691b6f69334af22e
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="use-the-counters-panel-in-graphs-view-and-tables-view"></a>Utiliser le volet Compteurs dans la vue Graphiques et la vue Tables

Le volet des compteurs est visible dans la vue Graphiques et la vue Tables de l'analyseur de test de charge pendant l'exécution d'un test de charge, ou lorsque vous analysez un résultat de test de charge. Pour plus d’informations, consultez [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md), [Analyser les résultats des tests de charge et les erreurs dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) et [Guide pratique pour accéder aux résultats des tests de charge pour analyse](../test/how-to-access-load-test-results-for-analysis.md).

Le volet Compteurs affiche une vue structurée de tous les compteurs de performance qui ont été collectés pendant le test de charge. Vous pouvez afficher ou masquer le volet Compteurs en cliquant sur **Afficher le volet des compteurs** dans la barre d’outils Analyseur de test de charge.

Les compteurs sont organisés dans une arborescence, où les nœuds terminaux sont des instances de compteur de performance qui peuvent représentés graphiquement.

Le volet des compteurs fournit les fonctionnalités suivantes :

-   Communique des informations sur la violation du seuil.

-   Sélection des compteurs à représenter sur le graphique.

-   Une arborescence structurée de tous les compteurs de performance collectés pendant une série de tests de charge avec les branches principales suivantes :

    -   **Général :** Contient le récapitulatif des données des compteurs de performance pour chaque agent de test et pour tout le test de charge.

    -   **Nom du scénario :** les branches portant le nom du scénario de test de charge dans l’arborescence des compteurs de performance contiennent toutes les instances des compteurs de test de charge associées à un scénario de test de charge particulier. La plupart des compteurs de test de charge sont imbriqués dans une branche de scénario.

         Une branche de scénario contient des nœuds de test de performances de site web. Les nœuds de test de performances de site web contiennent les nœuds Pages, Requêtes et Transaction. Tout nœud terminal dans cette structure est un compteur de performance qui peut être ajouté à un graphique.

    -   **Ordinateurs :** contient toutes les instances des compteurs qui ne correspondent pas à un test de charge, regroupées par ordinateur. La branche Ordinateurs contient un nœud pour chaque ordinateur associé au contrôleur du test de charge spécifié dans la section Rôles des paramètres de test actuellement sélectionnés. Pour plus d’informations, consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

         Chaque nœud d'ordinateur contient un ensemble de catégories de compteurs de performance collectés sur cet ordinateur. Les catégories contiennent les compteurs et les compteurs contiennent les noms des instances de compteurs de performance.

    -   **Erreurs :** contient toutes les erreurs détectées pendant le test de charge. Le nœud Erreurs contient plusieurs nœuds d’erreurs correspondant à des sous-catégories. Les sous-catégories sont spécifiques à différents types d’erreurs, par exemple les exceptions et les erreurs HTTP.

### <a name="scenario-name-node-in-counters-panel"></a>Nœud du nom de scénario dans le volet des compteurs

|||
|-|-|
|![Nœud de nom de scénario du panneau Compteur](../test/media/ltest__namenode.png)|1. Tous les compteurs de performance associés à Scenario1 du test de charge s'affichent sous ce nœud.<br />2. Tous les tests d'un scénario se trouvent sous le nœud du scénario. L'étiquette indique le nom du test.<br />3. Les nœuds terminaux sous un nœud de test sont des compteurs de cas de test du test de charge, pour lesquels le nom de l’instance du compteur est le nom du test.<br />4. Toutes les instances du compteur des pages du test de charge associées à une branche de test de performances de site web. Au niveau de ce nœud, toutes les instances des compteurs de pages du test de charge, associées à Obtention d'ouverture de session (nom du rapport) de la page du test de performances de site web IBuyBrowse dans Scenario1 du test de charge sont contenues ici.<br />5. Les nœuds terminaux sous un nœud de page sont des compteurs de pages de test de charge.<br />6. Toutes les instances des compteurs de requêtes du test de charge associées à un test de performances de site web sont contenues dans une branche de test de performances de site web. Au niveau de ce nœud, toutes les instances des compteurs de requêtes, associées à Obtention d'ouverture de session (nom du rapport) de la requête du test de performances de site web IBuyBrowse dans Scenario1 du test de charge sont contenues ici.<br />7. Les nœuds terminaux sous un nœud de demande sont des compteurs de demandes du test de charge.<br />8. Toutes les instances des compteurs de transactions du test de charge associées à un test de performances de site web sont contenues dans une branche de test de performances de site web. Au niveau de ce nœud, toutes les instances de compteur des transactions associées à la transaction nommée Transaction1 du test de performances de site web IBuyBrowse dans Scenraio1 du test de charge sont contenues ici.<br />9. Les nœuds terminaux sous un nœud de transactions sont des compteurs de transactions du test de charge.<br />10. Noeud de test unitaire.|

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-----------|-----------------------|
|**Ajouter d’autres compteurs de performance à un graphique dans la vue Graphiques :** dans le volet Compteurs, vous pouvez ajouter différents types de données à un graphique de test de charge en rajoutant des compteurs de performance sur le graphique.|-   [Comment : ajouter et supprimer des compteurs sur des graphiques](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Analyser les violations des seuils vous avez spécifiés dans le test de charge :** le volet Compteurs affiche des icônes représentant des violations de seuil, que vous pouvez ajouter ensuite aux tables et aux graphiques pour une analyse plus approfondie.|-   [Comment : analyser les violations de seuils dans le volet Compteurs](../test/analyze-threshold-rule-violations-in-load-tests.md)|
|**Analyser les erreurs détectées pendant l’exécution du test de charge :** le volet des compteurs inclut un nœud Erreurs qui contient des catégories et des sous-catégories d’erreurs, comme les erreurs HTTP, que vous pouvez utiliser pour ajouter des erreurs aux graphiques pour une analyse plus détaillée.|-   [Guide pratique pour analyser les erreurs dans le volet Compteurs](../test/how-to-analyze-errors-using-the-counters-panel.md)|

## <a name="performance-counter-sampling-interval-considerations"></a>Considérations relatives à l'intervalle d'échantillonnage du compteur de performance

Choisissez une valeur pour la propriété **Taux d’échantillonnage** dans les paramètres d’exécution d’un test de charge en fonction de la longueur de votre test de charge. Un taux d'échantillonnage moins élevé, tel que la valeur par défaut de cinq secondes, nécessite une capacité d'espace supplémentaire dans la base de données des résultats du test de charge. Pour les tests de charge de plus longue durée, l'augmentation du taux d'échantillonnage permet de réduire le volume de données collectées. Pour plus d’informations, consultez [Guide pratique pour spécifier le taux d’échantillonnage](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Voici quelques instructions sur les taux d'échantillonnage :

|Durée du test de charge|Taux d'échantillonnage recommandé|
|------------------------|-----------------------------|
|\< 1 heure|5 secondes|
|1 à 8 heures|15 secondes|
|8 à 24 heures|30 secondes|
|> 24 heures|60 secondes|

## <a name="considerations-for-including-timing-details-to-collect-percentile-data"></a>Considérations relatives à l'inclusion de détails de minuterie pour collecter des données de centile

Les paramètres d’exécution de l’éditeur de test de charge contiennent une propriété nommée **Stockage des détails de minuterie**. Si la propriété **Stockage des détails de minuterie** est activée, le temps nécessaire à l’exécution de chaque test, transaction et page individuels pendant le test de charge est stocké dans le référentiel des résultats des tests de charge. Cela permet aux 90ème et 95ème données de centile de s’afficher dans l’analyseur de test de charge des tables Tests, Transactions et Pages.

Vous avez deux possibilités pour activer la propriété **Stockage des détails de minuterie** dans les propriétés des paramètres d’exécution : **StatisticsOnly** et **AllIndividualDetails**. Quelle que soit l’option choisie, tous les tests, pages et transactions individuels sont chronométrés et les données de centile sont calculées à partir des données de temporisation individuelles. La différence est qu’avec l’option **StatisticsOnly**, les données de minutage individuelles sont supprimées du référentiel dès que les données de centile ont été calculées. Cela réduit la capacité d'espace requise dans le référentiel lorsque vous utilisez des détails de minuterie. Toutefois, les utilisateurs expérimentés peuvent traiter les données des détails de minuterie d'une autre façon, en utilisant des outils SQL. Si c’est le cas, l’option **AllIndividualDetails** doit être utilisée afin que les données des détails de minutage soient disponibles pour ce traitement. En outre, si vous affectez la valeur **AllIndividualDetails** à la propriété, vous pouvez analyser l’activité des utilisateurs virtuels à l’aide du graphique d’activités des utilisateurs virtuels dans l’analyseur de test de charge à l’issue de l’exécution du test de charge. Pour plus d’informations, consultez [Analyse de l’activité des utilisateurs virtuels dans la vue Détails](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

La quantité d’espace requise dans le référentiel des résultats de test de charge pour stocker les détails de minutage peut être importante, en particulier pour les tests de charge qui s’exécutent longtemps. En outre, le temps nécessaire pour stocker ces données dans le référentiel des résultats du test de charge à la fin du test de charge est plus long, étant donné que ces données sont stockées sur les agents de test de charge jusqu’à la fin de l’exécution du test de charge. Lorsque le test de charge est terminé, les données sont stockées dans le référentiel. Par défaut, la propriété **Stockage des détails de minuterie** est activée. Si cela pose un problème pour votre environnement de test, vous pouvez affecter la valeur **Aucun** à la propriété **Stockage des détails de minuterie**.

Pour plus d’informations, consultez [Comment : spécifier la propriété Stockage des détails de minuterie](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)