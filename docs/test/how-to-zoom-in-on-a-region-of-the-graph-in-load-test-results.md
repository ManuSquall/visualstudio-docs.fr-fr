---
title: Effectuer un zoom sur les graphiques des résultats des tests de charge
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 836e4f30e2c84bf0093366f4cc38a2cb7f58b545
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287023"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Guide pratique pour faire un zoom sur une région du graphique des résultats d’un test de charge

Une fois un test de charge terminé, vous pouvez utiliser les barres de zoom pour effectuer un zoom avant et accéder à une zone spécifique du graphique. En zoomant en avant, vous pouvez examiner en détail les données générées durant une série de tests de charge.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Le zoom avant est disponible uniquement lorsque vous analysez les résultats d'un test de charge terminé et non pas lorsque vous observez les résultats d'un test en cours.

Le contrôle de zoom est uniquement visible dans **l’Analyseur de test de charge** lorsque vous consultez un résultat de test de charge en mode zoom. Le mode zoom est appliqué dans la vue Graphiques lorsqu'un test de charge s'est terminé ou qu'un test de charge exécuté précédemment est chargé. Vous pouvez afficher ou masquer les contrôles de zoom sur les graphiques à l’aide du bouton **Afficher les contrôles de zoom** dans la barre d’outils.

Le **zoom sur l’axe des abscisses (x)** peut être ajusté pour analyser certaines périodes au cours du test de charge. Le **zoom sur l’axe des ordonnées (y)** peut être ajusté pour analyser certaines plages de valeurs pour les compteurs inclus dans le graphique.

La **chronologie horizontale** et les **contrôles de zoom des plages de valeurs verticaux** peuvent être ajustés à l’aide de la souris. Le **contrôle de chronologie horizontal** peut également être ajusté à l’aide des touches de direction gauche et droite. En utilisant les touches de direction pour ajuster le contrôle de zoom, vous pouvez ajuster la plage des fenêtres de 1 intervalle d'échantillonnage à la fois. L’utilisation simultanée de la touche **Maj** et des touches de direction permet de procéder par plages de 10 intervalles d’échantillonnage à la fois.

Pour ajuster le contrôle de zoom à l’aide de la touche de direction, définissez d’abord le focus sur le contrôle de zoom à l’aide de la touche de **tabulation**. Lorsque le focus est placé sur le curseur gauche, les touches de direction déplacent la limite initiale de la fenêtre de zoom de 1 intervalle à gauche ou à droite. Lorsque le focus est sur le curseur de centre, vous pouvez utiliser les touches de direction pour faire défiler la fenêtre de zoom à gauche ou à droite de 1 intervalle d'échantillonnage sans modifier la taille de la fenêtre de zoom. Enfin, le curseur du côté droit se déplace, permettant l'extension ou la réduction de la plage de la fin de la fenêtre de zoom de 1 intervalle d'échantillonnage.

Pour revenir aux contrôles de zoom horizontal et vertical afin d’afficher la chronologie complète et les plages de valeurs, vous pouvez utiliser l’option **Zoom arrière horizontal**, l’option **Zoom arrière vertical** ou l’option **Zoom avant/arrière** dans le menu contextuel du graphique.

> [!TIP]
> Vous pouvez utiliser la commande **Synchroniser les contrôles de zoom horizontal** dans la barre d’outils pour activer/désactiver la synchronisation de zoom horizontal automatique. Lorsque la synchronisation est activée, un effet de zoom appliqué à un graphique est également appliqué à tous les autres graphiques de la vue Graphiques.

![Contrôle de zoom de l'affichage de graphiques](../test/media/ltest_zoomcontrol.png)

Dans l’illustration précédente, un zoom avant a été appliqué au graphique **Système testé** pour étudier les problèmes de seuil. Les violations de seuils ont été activées à l’aide de l’option **Afficher les violations de seuils sur le graphique** de la liste déroulante **Options de graphique** dans la barre d’outils.

Pour plus d’informations, consultez [analyser les résultats des tests de charge dans la vue graphiques](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="display-graphs"></a>Afficher des graphiques

Avant de pouvoir modifier l'affichage des graphiques en effectuant un zoom avant ou arrière ou en le faisant défiler, suivez la procédure suivante pour afficher ces graphiques.

Pour afficher des graphes :

1. Exécutez un test de charge jusqu'à ce qu'il soit terminé.

2. À la fin de la série de tests de charge, choisissez **Oui** dans la boîte de dialogue qui vous invite à afficher les résultats à partir du magasin des résultats des tests de charge.

     \- ou -

     Voir les détails d'un test de charge exécuté par le passé. Pour plus d’informations, consultez [Comment : accéder aux résultats des tests de charge pour l’analyse](../test/how-to-access-load-test-results-for-analysis.md).

3. Choisissez **Graphiques** si vos graphiques ne sont pas affichés.

4. Si les barres de zoom ne sont pas affichées, choisissez **Afficher les contrôles de zoom**.

     Deux barres de zoom sont disponibles pour chaque graphique. La barre de zoom qui contrôle l'échelle verticale apparaît à gauche du graphique. La barre de zoom qui contrôle l'échelle horizontale apparaît sous le graphique.

     Chaque barre de zoom possède deux poignées. Une poignée est une zone rectangulaire située à chaque extrémité de la barre de zoom.

## <a name="zoom-and-scroll"></a>Zoom et défilement

Lorsque plusieurs graphiques sont affichés, vous pouvez les garder synchronisés afin qu'ils affichent la même partie de la série de tests de charge.

### <a name="to-synchronize-zooming-and-scrolling"></a>Pour synchroniser le zoom et le défilement

1. Dans l' **Analyseur de test de charge**, choisissez **synchroniser les contrôles de zoom horizontal**.

     Lorsque le bouton **Synchroniser les contrôles de zoom horizontal** est sélectionné, si vous un faites un zoom et faites défiler l’échelle de temps d’un graphique en particulier, ce zoom et ce défilement sont également répercutés sur les autres graphiques.

2. Choisissez à nouveau **Synchroniser les contrôles de zoom horizontal**.

     Lorsque le bouton **Synchroniser les contrôles de zoom horizontal** n’est pas sélectionné, si vous un faites un zoom et faites défiler l’échelle de temps d’un graphique en particulier, ce zoom et ce défilement ne sont appliqués qu’à ce graphique.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Pour faire un zoom et faire défiler une portion du graphique

1. Sur la barre de zoom sous un graphique, faites glisser la poignée de gauche à droite.

     Ceci permet d'effectuer un zoom sur la dernière partie de la série de tests. De la même façon, si vous faites glisser la poignée de droite vers la gauche, vous effectuez un zoom sur la première partie de la série de tests.

2. Pour faire un zoom avant sur une zone en particulier, faites glisser les deux poignées vers le centre du graphique.

     Plus les deux poignées sont proches l’une de l’autre, plus l’agrandissement est élevé et permet de révéler des segments plus courts et plus précis du test de charge.

     Cliquez sur la section centrale de la barre de zoom et faites-la glisser pour défiler jusqu'à un point particulier dans le test de charge.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Pour effectuer un zoom avant d'une zone du graphique en cliquant dessus et en la faisant glisser

1. Choisissez un graphique à une extrémité de la zone de zoom.

2. Faites glisser le pointeur de la souris à l'autre extrémité de la zone de zoom.

3. Relâchez le bouton de la souris.

    Cela agrandit la zone que vous avez définie en cliquant dessus et en la faisant glisser.

   La procédure suivante décrit la manière d'effectuer rapidement un zoom arrière sans avoir à déplacer les extrémités de la barre de zoom.

### <a name="to-zoom-out"></a>Pour effectuer un zoom arrière

1. Cliquez avec le bouton droit sur un graphique, graphique sur lequel un zoom avant a été effectué au préalable.

2. Dans le menu contextuel, sélectionnez **Zoom arrière horizontal**.

     Cela effectue un zoom arrière pour afficher l'intégralité de la série de tests de charge.

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Procédure : ajouter et supprimer des compteurs sur des graphiques](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
