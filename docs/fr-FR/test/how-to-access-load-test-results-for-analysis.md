---
title: Analyser les résultats des tests de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, accessing
- Load Test Viewer
- load tests, accessing
- load tests, analyzing
- load tests, results
- Load Test Viewer, viewing
ms.assetid: b0a3e694-2894-479b-b270-7e61e9fafacd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d20754bc61a003b1b7f6d1eb84ce419c2c6e442b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-access-load-test-results-for-analysis"></a>Comment : accéder aux résultats des test de charge pour l'analyse

Lorsque vous exécutez un test de charge avec l'éditeur de test de charge, les résultats du test de charge s'affichent automatiquement et le test de charge en cours d'exécution apparaît dans l'analyseur de test de charge. Lorsque vous exécutez un test de charge à partir de la ligne de commande, vous devez accéder manuellement aux résultats du test de charge.

Le résultat du test de charge pour le test de charge terminé contient des exemples de compteur de performance et des informations sur les erreurs qui ont été collectées à intervalles réguliers sur les ordinateurs en cours de test. Un grand nombre d'exemples de compteurs de performance peuvent être collectés au cours d'une série de tests de charge. La quantité de données de performance collectées dépend de la durée de la série de tests, de l'intervalle d'échantillonnage, du nombre d'ordinateurs sous test et du nombre de compteurs collectés, des collecteurs de données configuré et des niveaux de journalisation. Pour un test de charge volumineux, le volume de données de performances collectées peut facilement atteindre plusieurs gigaoctets. Pour plus d’informations, consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

## <a name="to-access-a-load-test-result"></a>Pour accéder à un résultat de test de charge

1.  Depuis un projet de test de performances de site Web et de charge, ouvrez un test de charge.

2.  Dans la barre d’outils de l’éditeur de test de charge, choisissez le bouton **Ouvrir et gérer des résultats**.

     La boîte de dialogue **Ouvrir et gérer des résultats** s’affiche.

3.  Dans **Entrer un nom de contrôleur pour rechercher les résultats des tests de charge**, sélectionnez un contrôleur. Sélectionnez **\<local> - Aucun contrôleur** pour accéder aux résultats stockés localement.

4.  Dans **Afficher les résultats pour le test de charge suivant**, sélectionnez le test de charge dont vous souhaitez consulter les résultats. Sélectionnez **\<Afficher les résultats de tous les tests>** pour consulter les résultats de tous les tests.

     Si des résultats des tests de charge sont disponibles, ceux-ci apparaissent dans la liste **Résultats du test de charge**. Les colonnes sont **Heure**, **Durée**, **Utilisateur**, **Résultat**, **Test** et **Description**. **Test** contient le nom du test et **Description** contient la description facultative qui est ajoutée avant l’exécution du test.

    > [!NOTE]
    > Les résultats apparaissent avec les résultats les plus récents en haut de la liste.

5.  Dans la liste **Résultats du test de charge**, sélectionnez les résultats à analyser, puis choisissez **Ouvrir**.

6.  L'analyseur de test de charge s'affiche. Le résultat du test de charge sélectionné s'affiche en mode Résumé. Pour plus d’informations, consultez [Vue d’ensemble du résumé des résultats des tests de charge](../test/load-test-results-summary-overview.md).

     Vous pouvez gérer d'autres aspects des résultats du test de charge dans la boîte de dialogue Ouvrir et gérer des résultats, notamment l'importation, l'exportation et la suppression des résultats de test de charge. Pour plus d’informations, consultez [Gestion des résultats des tests de charge dans le dépôt des résultats de tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)