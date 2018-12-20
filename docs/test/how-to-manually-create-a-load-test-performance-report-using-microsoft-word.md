---
title: Créer un rapport de performances de test de charge à l’aide de Microsoft Word
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: c718501f4a3665f2383560f8c472102bfb5be757
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064454"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Procédure : créer manuellement un rapport de performances de test de charge à l’aide de Microsoft Word

Vous pouvez créer manuellement des rapports de test de charge en copiant et en collant les données du mode Résumé et de la vue Graphiques des résultats des tests de charge. Les données qui sont présentées dans les vues Graphiques et Résumé sont appliquées au format HTML lorsqu'elles sont copiées.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Vous pouvez également copier le texte brut de la vue Tables et les captures d’écran du mode Détails dans Microsoft Word. Toutefois, il n’est pas appliqué au format HTML et nécessite une mise en forme et des modifications supplémentaires.

> [!TIP]
> Vous pouvez également générer des rapports Microsoft Excel organisés automatiquement. Pour plus d'informations, voir [Procédure : créer des rapports de performances de test de charge à l’aide de Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Copier les données du mode Résumé

1.  Dans **Résultats du test de charge**, si le mode Résumé n’est pas affiché, cliquez sur **Résumé** dans la barre d’outils.

2.  En mode Résumé, cliquez avec le bouton droit et sélectionnez **Sélectionner tout**.

3.  En mode Résumé, cliquez avec le bouton droit et sélectionnez **Copier**. Cela restitue les données du mode Résumé au format HTML dans le Presse-papiers.

4.  Dans Microsoft Word, collez les données du mode Résumé à l’emplacement souhaité.

5.  Vous pouvez maintenant modifier, mettre en forme et supprimer certains aspects du contenu copié en fonction de vos besoins en matière de création de rapport.

## <a name="copy-graph-view-data"></a>Copier les données de la vue Graphiques

1.  Dans **Résultats du test de charge**, si la vue Graphiques n’est pas affichée, choisissez **Graphiques** dans la barre d’outils.

2.  (Facultatif) Faites un zoom avant sur le graphique spécifique à copier dans votre document Microsoft Word, comme l’indique l’illustration suivante. Pour plus d'informations, voir [Procédure : effectuer un zoom avant sur une région du graphique](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Contrôle de zoom de l'affichage de graphiques](../test/media/ltest_zoomcontrol.png)

3.  Sur le graphique à copier dans votre document Microsoft Word, cliquez avec le bouton droit, puis sélectionnez **Copier**.

4.  Dans Microsoft Word, collez le graphique et les données de table associées à l’emplacement souhaité.

    > [!WARNING]
    > Vous ne pouvez pas copier le graphique d'un bureau à distance et le coller sur un autre ordinateur, parce que seules les informations de table associées au graphique seront copiées et pas l'image du graphique. L'image du graphique est stockée dans le répertoire temporaire de l'ordinateur à partir duquel il a été copié, et le deuxième ordinateur ne peut pas supprimer la référence de ce répertoire.

## <a name="see-also"></a>Voir aussi

- [Créer des rapports sur les résultats des tests de charge pour les comparaisons de tests ou l’analyse des tendances](../test/compare-load-test-results.md)
- [Guide pratique pour créer des rapports de performances de test de charge à l’aide de Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)