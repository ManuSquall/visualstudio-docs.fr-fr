---
title: Ajouter et supprimer des compteurs sur des graphiques dans les résultats des tests de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8b43cc3acbbff70124685229e33362cfd9b30561
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908799"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Comment : ajouter et supprimer des compteurs sur des graphiques dans les résultats des tests de charge

Vous pouvez utiliser le volet **Compteurs** pour ajouter des compteurs de performances à un graphique.

 ![Compteur ajouté à un graphique](../test/media/ltest_selectcounter.png)

 **Considérations relatives à l’intervalle d’échantillonnage des compteurs de performances**

 Choisissez une valeur pour la propriété **Taux d’échantillonnage** dans les paramètres d’exécution d’un test de charge en fonction de la longueur de votre test de charge. Un taux d'échantillonnage moins élevé, tel que la valeur par défaut de cinq secondes, nécessite une capacité d'espace supplémentaire dans la base de données des résultats du test de charge. Pour les tests de charge de plus longue durée, l'augmentation du taux d'échantillonnage permet de réduire le volume de données collectées. Pour plus d’informations, voir [Guide pratique : Spécifier l’échantillonnage](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

 Voici quelques instructions sur les taux d'échantillonnage :

|Durée du test de charge|Taux d'échantillonnage recommandé|
|-|-----------------------------|
|\< 1 heure|5 secondes|
|1 à 8 heures|15 secondes|
|8 à 24 heures|30 secondes|
|> 24 heures|60 secondes|

 **Considérations relatives à l’inclusion de détails de minutage pour collecter des données de centile**

 Les paramètres d’exécution de l’éditeur de test de charge contiennent une propriété nommée **Stockage des détails de minuterie**. Si la propriété **Stockage des détails de minuterie** est activée, le temps nécessaire à l’exécution de chaque test, transaction et page individuels pendant le test de charge est stocké dans le référentiel des résultats des tests de charge. Ainsi, les données du 90e et du 95e centiles s’affichent dans **l’Analyseur de test de charge** des tables Tests, Transactions et Pages.

 Vous avez deux possibilités pour activer la propriété **Stockage des détails de minuterie** dans les propriétés des paramètres d’exécution : **StatisticsOnly** et **AllIndividualDetails**. Quelle que soit l’option choisie, tous les tests, pages et transactions individuels sont chronométrés et les données de centile sont calculées à partir des données de temporisation individuelles. La différence est qu’avec l’option **StatisticsOnly**, les données de minutage individuelles sont supprimées du référentiel dès que les données de centile ont été calculées. Cela réduit la capacité d'espace requise dans le référentiel lorsque vous utilisez des détails de minuterie. Toutefois, les utilisateurs expérimentés peuvent traiter les données des détails de minuterie d'une autre façon, en utilisant des outils SQL. Si c’est le cas, l’option **AllIndividualDetails** doit être utilisée afin que les données des détails de minutage soient disponibles pour ce traitement. Par ailleurs, si vous affectez la valeur **AllIndividualDetails** à la propriété, vous pourrez analyser l’activité des utilisateurs virtuels dans le graphique **Activité des utilisateurs virtuels** de **l’Analyseur de test de charge** à l’issue de l’exécution du test de charge. Pour plus d’informations, voir [Analyser l’activité des utilisateurs virtuels dans la vue Détails](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

La capacité d'espace requise dans le référentiel des résultats du test de charge pour stocker les détails de minuterie pouvait être très élevée, en particulier pour les longs tests de charge. En outre, le temps nécessaire pour stocker ces données dans le référentiel des résultats du test de charge à la fin du test de charge est plus long, étant donné que ces données sont stockées sur les agents de test de charge jusqu'à la fin de l'exécution du test de charge. Lorsque le test de charge est terminé, les données sont stockées dans le référentiel. Par défaut, la propriété **Stockage des détails de minuterie** est activée. Si cela pose un problème pour votre environnement de test, vous pouvez affecter la valeur **Aucun** à la propriété **Stockage des détails de minuterie**.

Pour plus d’informations, voir [Guide pratique : Spécifier la propriété de stockage des détails de minutage](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Pour afficher un compteur de performance particulier sur un graphique de test de charge

1.  Une fois que l’exécution d’un test de charge est terminée, ou après avoir chargé un résultat de test, dans la barre d’outils de l’Analyseur de test de charge, choisissez **Graphiques**.

     Le volet **Compteurs** s’affiche dans la vue Graphiques.

    > [!NOTE]
    > Si le volet **Compteurs** n’est pas visible, choisissez **Afficher le volet Compteurs** dans la barre d’outils.

2.  Dans le volet **Compteurs**, développez les nœuds de la hiérarchie jusqu’au compteur de performances que vous souhaitez afficher sous forme graphique.

     Par exemple, afficher la mémoire disponible sur l’ordinateur où les tests s’exécutent, développez **Ordinateurs**, développez le nœud correspondant à l’ordinateur, puis développez **Mémoire**. Le compteur **Mégaoctets disponibles** s’affiche.

3.  Choisissez le graphique sur lequel vous souhaitez afficher le compteur de performance.

4.  Cliquez avec le bouton droit sur un compteur de performance du volet **Compteurs** et sélectionnez **Afficher le compteur sur le graphique**.

    > [!TIP]
    > Pour interrompre temporairement l'affichage des données du compteur de performance sur le graphique, désactivez la case à cocher du compteur de performance dans la légende. Les statistiques min, max et moy. et statistiques sont toujours analysées, mais la ligne de tendance n'est pas affichée sur le graphique. Cela peut être utile si le graphique contient plusieurs tracés des compteurs de performance qui se chevauchent pendant que vous analysez les problèmes. Pour plus d’informations, voir [Utiliser la légende de la vue Graphiques pour analyser des tests de charge](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5.  Pour supprimer les données du compteur de performance dans le graphique, cliquez avec le bouton droit sur le compteur de performance dans la colonne **Compteur** de la légende et sélectionnez **Supprimer**.

     \- ou -

     Cliquez avec le bouton droit sur la ligne de données dans le graphique et sélectionnez **Supprimer**.

     \- ou -

     Choisissez le compteur de performance dans la colonne **Compteur** de la légende ou la ligne de données dans le graphique, puis appuyez sur la touche **Suppr**.

    > [!NOTE]
    > Vous pouvez également choisir de placer un compteur de performance sur la légende, mais pas sur le graphique, en utilisant la commande **Afficher le compteur sur la légende**.

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Guide pratique pour créer des graphiques personnalisés](../test/how-to-create-custom-graphs-in-load-test-results.md)