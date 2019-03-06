---
title: 'Procédure : créer des graphes personnalisés dans les résultats des tests de charge'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, creating
- load test results graphs
ms.assetid: 17fcafce-76f9-4411-9389-6e5376eab236
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a03d16f74623d935e8f4f09b0f397672ad226487
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932403"
---
# <a name="how-to-create-custom-graphs-in-load-test-results"></a>Procédure : créer des graphes personnalisés dans les résultats des tests de charge

Vous pouvez concevoir des graphiques qui affichent des informations spécifiques à propos des résultats de test de charge. Vous concevez un graphique personnalisé en spécifiant les compteurs de test de charge que le graphique affichera.

Vous pouvez appliquer la procédure suivante pendant l'exécution d'un test de charge ou après.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-load-test-results-graph"></a>Pour créer un graphique personnalisé sur les résultats d'un test de charge

1.  Dans la barre d’outils **Test de charge**, choisissez **Ajouter un nouveau graphique**.

     \- ou -

     Dans **l’Analyseur de test de charge**, cliquez avec le bouton droit dans le volet **Compteurs** ou sur un graphique, puis sélectionnez **Ajouter un graphique**.

     La boîte de dialogue **Entrer le nom du graphique** s’affiche.

2.  Sous **Nom du graphique**, tapez le nom du graphique, puis choisissez **OK**.

     Le nouveau graphique s’affiche dans **l’Analyseur de test de charge**. Il apparaît dans le panneau graphique sélectionné et remplace le graphique qui s'y trouvait précédemment.

3.  Personnalisez le nouveau graphique en ajoutant des compteurs. Pour plus d'informations, voir [Procédure : ajouter et supprimer des compteurs sur des graphes](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Guide pratique pour ajouter et supprimer des compteurs sur des graphes](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)