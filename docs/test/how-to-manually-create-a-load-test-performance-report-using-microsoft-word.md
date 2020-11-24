---
title: Créer un rapport de performances de test de charge à l’aide de MS Word
description: Découvrez comment créer manuellement des rapports de test de charge Microsoft Word en copiant et en collant des données à partir de la vue de la charge Résultats des tests Résumé et des graphiques.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2bddd2585d3bc88821fb2c265f21bfda84ed7bef
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440998"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Guide pratique pour créer manuellement un rapport de performances de test de charge à l’aide de Microsoft Word

Vous pouvez créer manuellement des rapports de test de charge en copiant et en collant les données du mode Résumé et de la vue Graphiques des résultats des tests de charge. Les données qui sont présentées dans les vues Graphiques et Résumé sont appliquées au format HTML lorsqu'elles sont copiées.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Vous pouvez également copier le texte brut de la vue Tables et les captures d’écran du mode Détails dans Microsoft Word. Toutefois, il n’est pas appliqué au format HTML et nécessite une mise en forme et des modifications supplémentaires.

> [!TIP]
> Vous pouvez également générer des rapports Microsoft Excel organisés automatiquement. Pour plus d’informations, consultez [Guide pratique pour créer des rapports de performances de test de charge à l’aide de Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Copier les données du mode Résumé

1. Dans la **résultats des tests de charge**, si la vue de résumé n’est pas affichée, cliquez sur **Résumé** dans la barre d’outils.

2. En mode Résumé, cliquez avec le bouton droit et sélectionnez **Sélectionner tout**.

3. En mode Résumé, cliquez avec le bouton droit et sélectionnez **Copier**. Cela restitue les données du mode Résumé au format HTML dans le Presse-papiers.

4. Dans Microsoft Word, collez les données du mode Résumé à l’emplacement souhaité.

5. Vous pouvez maintenant modifier, mettre en forme et supprimer certains aspects du contenu copié en fonction de vos besoins en matière de création de rapport.

## <a name="copy-graph-view-data"></a>Copier les données de la vue Graphiques

1. Dans la **résultats des tests de charge**, si la vue graphiques n’est pas affichée, choisissez **graphiques** dans la barre d’outils.

2. (Facultatif) Faites un zoom avant sur le graphique spécifique à copier dans votre document Microsoft Word, comme l’indique l’illustration suivante. Pour plus d’informations, consultez [Comment : effectuer un zoom avant sur une région du graphique](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Contrôle de zoom de l'affichage de graphiques](../test/media/ltest_zoomcontrol.png)

3. Sur le graphique à copier dans votre document Microsoft Word, cliquez avec le bouton droit, puis sélectionnez **Copier**.

4. Dans Microsoft Word, collez le graphique et les données de table associées à l’emplacement souhaité.

    > [!WARNING]
    > Vous ne pouvez pas copier le graphique d'un bureau à distance et le coller sur un autre ordinateur, parce que seules les informations de table associées au graphique seront copiées et pas l'image du graphique. L'image du graphique est stockée dans le répertoire temporaire de l'ordinateur à partir duquel il a été copié, et le deuxième ordinateur ne peut pas supprimer la référence de ce répertoire.

## <a name="see-also"></a>Voir aussi

- [Créer des rapports sur les résultats des tests de charge pour les comparaisons de tests ou l’analyse des tendances](../test/compare-load-test-results.md)
- [Guide pratique pour créer des rapports de performances de test de charge à l’aide de Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
