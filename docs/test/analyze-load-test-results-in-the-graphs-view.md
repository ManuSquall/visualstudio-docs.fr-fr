---
title: Analyser les résultats des tests de charge-vue graphiques (analyseur de test de charge)
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graph.view
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, graphs in Load Test Viewer
- Load Test Viewer, graphs
- load tests, results graphs
- load tests, using graphs
- load test results, graphs
ms.assetid: 4a919cd8-541c-40ee-be3b-352fabc56140
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b48162da7a753516ce0c1ae0dba4cfe1f94387e4
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810651"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Analyser les résultats des tests de charge dans la vue Graphiques de l’analyseur de test de charge

Les résultats d'un test de charge sont affichés comme des données dans plusieurs volets différents.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Pour afficher les résultats des tests sous forme de graphiques, choisissez **graphiques** dans la barre d’outils de **test de charge** . Chaque graphique individuel est affiché dans un panneau, avec son nom indiqué en haut dans une liste déroulante. Pour afficher un graphique différent dans le panneau, sélectionnez un autre un nom de graphique dans la liste.

Jusqu'à quatre panneaux de graphique peuvent être affichés à la fois. Vous pouvez passer d’une disposition de panneau à l’autre à l’aide les boutons de la barre d’outils de **disposition du panneau**.

Plusieurs graphiques prédéfinis sont disponibles. Vous pouvez utiliser les graphiques prédéfinis tels quels ou vous pouvez les personnaliser. En outre, vous pouvez créer vos propres graphiques. Pour plus d’informations, consultez [Comment : ajouter et supprimer des compteurs sur des graphiques](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) et [Comment : créer des graphiques personnalisés](../test/how-to-create-custom-graphs-in-load-test-results.md).

## <a name="built-in-graphs"></a>Graphiques prédéfinis

Le tableau suivant répertorie les graphiques prédéfinis à votre disposition pour analyser des résultats de tests de charge.

|Nom du graphique|Description|
|-|-|
|Indicateurs clés|Compteurs qui décrivent les aspects de base des performances des tests, tels que la charge utilisateur, le débit et le temps de réponse.|
|Temps de réponse du test|Données concernant la durée d'exécution des tests.|
|Temps de réponse de la page|Temps de réponse moyen des pages web consultées pendant le test de charge.|
|Système testé|Informations sur les ordinateurs utilisés pour exécuter l'application en cours de test. Cela inclut des données sur l'utilisation de la mémoire, le processeur, le disque physique, les processus.<br /><br /> Par défaut, seules les données sur les compteurs Mégaoctets disponibles et Temps processeur sont collectées.|
|Contrôleur et agents|Informations sur les ordinateurs utilisés pour exécuter les tests de charge. Cela inclut des données sur l'utilisation de la mémoire, le processeur, le disque physique, les processus.<br /><br /> Par défaut, seules les données sur les compteurs Mégaoctets disponibles et Temps processeur sont collectées.|
|Temps de réponse de la transaction|Temps de réponse moyen pour les transactions effectuées durant le test de charge.|

Vous pouvez afficher différents compteurs sur le graphique au moment de l'exécution et après l'exécution d'un test.

> [!NOTE]
> Seuls les compteurs de performance de temps de réponse peuvent être ajoutés à un graphique de temps de réponse généré automatiquement.

Les informations sur les compteurs sont affichées à la fois sur le graphique et dans la légende au-dessous du graphique. Vous pouvez également effectuer un zoom avant sur une section du graphique. Pour plus d’informations, consultez [Comment : effectuer un zoom avant sur une région du graphique](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

## <a name="counters-displayed-in-graphs"></a>Compteurs affichés sur les graphiques

Les graphiques affichent des *compteurs*. Les compteurs font référence aux données rassemblées pendant un test de charge, des exemples de compteurs sont les tests par seconde ou la durée moyenne du test. Pour plus d’informations sur les compteurs, consultez [spécification des ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

La légende des compteurs affichés dans les graphiques indique plusieurs colonnes de données utiles relatives à la série de tests de charge. Pour désactiver l'affichage des données sur le graphique, désactivez la case à cocher sur la ligne dans la légende.

La légende contient les colonnes suivantes :

|Counter|Nom du compteur|
|-|-|
|Instance|Nom de l'instance de compteur.|
|Category|Nom de la catégorie de compteur.|
|Computer|Le nom de l'ordinateur sur lequel les données du compteur sont collectées.|
|Color|Couleur de la ligne sur le graphique.|
|Plage|Indique le nombre représenté par 100 sur le graphique de ce compteur. Par exemple, pour une plage dont la limite supérieure est 10 000, l'étiquette 100 au sommet du graphique, représente 10 000.|
|Min|Indique la valeur minimale du compteur en millisecondes.|
|Max|Indique la valeur maximale du compteur en millisecondes.|
|Moy|Indique la valeur moyenne du compteur en millisecondes.|
|Dernier|Affiche la valeur du compteur pendant le dernier intervalle d'échantillonnage en millisecondes.|

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-|-|
|**Personnaliser les graphiques à l’aide de la légende :** la légende de la vue Graphiques affiche les informations de chaque compteur de performances associé à un graphique. Vous pouvez utiliser la légende pour supprimer les compteurs de performance, mettre en surbrillance les compteurs de performance dans le graphique et personnaliser les options de traçage.|-   [Utilisation de la légende de la vue graphiques pour analyser les tests de charge](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Afficher des compteurs sur des graphiques :** vous pouvez ajouter différents genres de données au graphique de résultats des tests de charge en y plaçant des compteurs.|-   [Procédure : ajouter et supprimer des compteurs sur des graphiques](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Faire un zoom sur des graphiques :** à la fin d’un test de charge, vous pouvez utiliser les barres de zoom pour effectuer un zoom avant et accéder à une zone spécifique du graphique. En zoomant en avant, vous pouvez examiner en détail les données générées durant une série de tests de charge.|-   [Comment : effectuer un zoom avant sur une région du graphique](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Afficher en mosaïque des graphiques :** vous pouvez réorganiser les graphiques de résultats des tests de charge selon plusieurs modèles. Vous pouvez disposer en mosaïque jusqu'à quatre graphiques.||
|**Créer des graphiques personnalisés :** vous pouvez concevoir des graphiques qui affichent des informations spécifiques sur les résultats des tests de charge. Vous concevez un graphique personnalisé en spécifiant les compteurs de test de charge que le graphique affichera.|-   [Comment : créer des graphiques personnalisés](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Exportez les données des compteurs de performance dans le graphique :** Vous pouvez exporter les données de graphique vers Microsoft Excel en utilisant le bouton **exporter un graphique des données vers Excel** dans la barre d’outils de l' **Analyseur de test de charge** lorsque vous êtes dans la vue **graphiques** .||

## <a name="related-tasks"></a>Tâches associées

[Analyser les résultats et les erreurs des tests de charge dans la vue tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

[Comment : accéder aux résultats des tests de charge pour l’analyse](../test/how-to-access-load-test-results-for-analysis.md)

[Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>Voir aussi

- [Procédure : ajouter et supprimer des compteurs sur des graphiques](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [Comment : créer des graphiques personnalisés](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Comment : effectuer un zoom avant sur une région du graphique](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
