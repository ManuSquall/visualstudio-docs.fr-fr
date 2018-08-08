---
title: Options de traçage des compteurs graphiques pour les tests de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, graphing counters
ms.assetid: 1969c20b-e0eb-48f6-a49f-a9090cd86008
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 5df33a8cf05e4ad73b1643e2948392e49a32356e
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382319"
---
# <a name="how-to-specify-plot-options-for-graphing-counters"></a>Guide pratique pour spécifier les options de traçage des compteurs graphiques

La boîte de dialogue **Options de traçage** vous permet de changer la couleur et le style de ligne d’un compteur tracé sur un graphique. Vous pouvez également régler la plage sur une valeur spécifique ou définir un réglage automatique de la plage, en fonction des données échantillonnées.

![Boîte de dialogue Options de traçage](../test/media/ltest_plotoptions.png)

## <a name="to-specify-plotting-options-for-graphs"></a>Pour spécifier des options de traçage pour les graphiques

1.  Dans la barre d’outils de **l’Analyseur de test de charge**, choisissez **Graphiques**.

     Les résultats du test de charge s’affichent alors dans la vue du graphique.

2.  Dans la légende ou le graphique, cliquez avec le bouton droit sur la ligne ou la ligne de traçage en cours du compteur de performances dont vous souhaitez changer l’option de traçage, puis sélectionnez **Options de traçage**.

     La boîte de dialogue **Options de traçage** s’affiche.

3.  Utilisez la liste déroulante **Couleur** afin de sélectionner la couleur à utiliser pour le traçage du compteur de performances.

4.  Utilisez la liste déroulante **Style** afin de sélectionner le style à utiliser pour le traçage du compteur de performances.

5.  Effectuez l’une des opérations suivantes :

     Sélectionnez **Ajuster automatiquement la plage** (valeur par défaut)

     \- ou -

     Décochez la case **Ajuster automatiquement la plage** et utilisez la liste déroulante **Plage** pour spécifier la plage à utiliser pour le traçage du compteur de performances.

6.  Cliquez sur **OK**.

     Le compteur de performance pour lequel vous avez modifié les options s'affiche dans le graphique avec les modifications effectuées.

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Guide pratique pour créer des graphiques personnalisés](../test/how-to-create-custom-graphs-in-load-test-results.md)
