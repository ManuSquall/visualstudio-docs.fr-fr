---
title: Analyser les erreurs de test de charge à l’aide du volet des compteurs dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, counters panel
ms.assetid: 981b4f1e-505a-4078-a06d-58ae17d996b4
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 2705120f5cf0e13e94369140c256bd3c7ae1466b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-analyze-errors-using-the-counters-panel"></a>Comment : analyser les erreurs dans le volet Compteurs

Le volet des compteurs est visible dans la vue Graphiques et la vue Tables de l'analyseur de test de charge pendant l'exécution d'un test de charge, ou lorsque vous analysez un résultat de test de charge. Pour plus d’informations, consultez [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md), [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) et [Guide pratique pour accéder aux résultats des tests de charge à des fins d’analyse](../test/how-to-access-load-test-results-for-analysis.md).

 Le nœud **Erreurs** dans le volet des compteurs contient toutes les erreurs détectées pendant le test de charge. Le nœud Erreurs contient plusieurs nœuds d'erreur de sous-catégorie qui sont spécifiques à différents types d'erreurs. Par exemple, **Exceptions** et **Erreurs HTTP**.

 ![Nœud Erreurs du volet des compteurs](../test/media/ltest_errornode.png "LTest_ErrorNode")

## <a name="to-analyze-errors-in-the-counters-panel"></a>Pour analyser des erreurs dans le volet des compteurs

1.  Après avoir effectué un test de charge, ou après avoir chargé un résultat de test, dans la barre d’outils de l’analyseur de test de charge, choisissez **Graphiques** ou **Tables**.

     Le volet des **compteurs** s’affiche dans la vue Graphiques ou la vue Tables.

2.  Si le volet des compteurs n’est pas visible, choisissez **Afficher le volet des compteurs** dans la barre d’outils.

3.  Développez le nœud **Erreurs**, puis sélectionnez une catégorie d’erreur ou une sous-catégorie d’erreur à analyser.

4.  Cliquez avec le bouton droit sur l'erreur et sélectionnez l'une des options suivantes :

    -   **Afficher le compteur sur le graphique** : dans la vue Graphiques, l’erreur est ajoutée et mise en surbrillance sur le graphique sélectionné. Pour plus d’informations, consultez [Guide pratique pour ajouter et supprimer des compteurs sur des graphiques](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

    -   **Afficher le compteur sur la légende** : l’erreur est ajoutée et sélectionnée dans la légende. Pour plus d’informations, consultez [Utilisation de la légende de la vue Graphiques pour analyser des tests de charge](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

    -   **Ajouter un graphique** :

    1.  La boîte de dialogue **Entrer le nom du graphique** s’affiche.

    2.  Dans la zone de texte **Nom du graphique**, entrez un nom pour le nouveau graphique, puis choisissez **OK**.

    3.  (Facultatif) Cliquez de nouveau avec le bouton droit sur l’erreur, puis sélectionnez **Afficher le compteur sur le graphique**.

         Pour plus d’informations, consultez [Guide pratique pour créer des graphiques personnalisés](../test/how-to-create-custom-graphs-in-load-test-results.md).

5.  Si vous analysez une erreur dans un résultat de test de charge terminé, envisagez d’utiliser les fonctionnalités de zoom dans la vue Graphiques (facultatif). Pour plus d’informations, consultez [Guide pratique pour faire un zoom avant sur une région du graphique](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

    > [!TIP]
    > Si toutes les erreurs ont été détectées pendant la série de tests de charge, un lien nommé Erreurs, y compris le nombre trouvé, sera disponible dans la barre d'état Analyseur de test de charge. Vous pouvez choisir le lien pour afficher toutes les erreurs dans la table **Erreurs** de la vue Tables.

## <a name="see-also"></a>Voir aussi

- [Utilisation du volet Compteurs dans la vue Graphiques et la vue Tables](../test/counters-panel-in-load-test-analyzer.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)