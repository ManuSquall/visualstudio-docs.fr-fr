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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: c65b9ad5c6a9d554f2c71cc5d17c63ce9368df2c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055398"
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