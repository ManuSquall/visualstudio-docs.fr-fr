---
title: Analyse des violations de règles de seuil dans les tests de charge dans l’analyseur de test de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.threshholdresult
helpviewer_keywords:
- load tests, thresholds
- threshold violations
- threshold counts
- load tests, threshold violations
- load test results, analyzing threshold violations
- thresholds in load tests
ms.assetid: 969ed346-cf2e-4d48-82b3-edb3e075e1c0
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 41837a9ff3d67f2d712352115bcb6581580b32a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812996"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Analyse des violations de règles de seuil dans les tests de charge dans l’analyseur de test de charge

Les règles de seuil sont associées à des compteurs de performance spécifiques, et les violations indiquent qu'un compteur de performance a dépassé ou est descendu en dessous d'une valeur définie. Lorsque vous exécutez un test de charge, vous pouvez analyser les violations qui se produisent pour les règles de seuil définies précédemment.

Si des violations se produisent, un lien hypertexte **Violations de seuil** apparaît sur la barre d’état de **Analyseur de test de charge** et spécifie le nombre de violations qui se sont produites. Vous cliquez sur le lien hypertexte pour afficher le tableau des violations de seuils. Vous pouvez également consulter les violations de seuil dans la fenêtre **Compteurs** et sur le graphique.

## <a name="view-threshold-violations-in-the-table"></a>Affichage des violations de seuil du tableau

 Le tableau des violations de seuils affiche les 1 000 premières violations. Le tableau suivant contient les colonnes :

|Colonne|Description|Visible par défaut|
|-|-|-|
|réflexion|Heure à laquelle la violation s'est produite lors du test de charge.|Oui|
|Ordinateur|Nom de l'ordinateur testé sur lequel la violation s'est produite. **Remarque :** Ceci est important quand vous exécutez des tests de charge sur des plateformes de test.|Oui|
|Category|Catégorie du compteur de performance sur lequel la violation s'est produite.|Oui|
|Counter|Nom du compteur de performance sur lequel la violation s'est produite.|Oui|
|Instance|Instance de compteur de performance sur laquelle la violation s'est produite.|Oui|
|Message|Message qui décrit la violation de seuil. Par exemple, **La valeur 5 dépasse la valeur du seuil critique 0**.|Oui|

> [!NOTE]
> Vous pouvez trier la table en choisissant les en-têtes de colonne.

 Pour plus d’informations, consultez [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Affichage des violations de seuil dans le volet Compteurs

 Vous pouvez afficher les violations de seuil dans le volet **Compteurs**, dans l’arborescence qui répertorie les compteurs de performance de votre test de charge. Les icônes du volet **Compteurs** indiquent les violations de seuil. L'icône sera l'un des suivants :

 L'icône sera l'un des suivants :

 ![Aucune violation de seuil](../test/media/icon_ltest_1.gif) Aucune violation de seuil.

 ![Une violation de seuil critique dans le dernier intervalle](../test/media/icon_ltest_2.gif) Une violation de seuil critique s'est produite au cours du dernier intervalle.

 ![Une violation de seuil critique dans un intervalle précédant](../test/media/icon_ltest_3.gif) Une violation de seuil critique s'est produite au cours d'un intervalle précédent.

 ![Une violation de seuil d'avertissement dans le dernier intervalle](../test/media/icon_ltest_4.gif) Une violation de seuil d'avertissement s'est produite au cours du dernier intervalle.

 ![Une violation de seuil d'avertissement dans un intervalle précédant](../test/media/icon_ltest_5.gif) Une violation de seuil d'avertissement s'est produite au cours d'un intervalle précédent.

 Les violations de seuils peuvent également être indiquées sur le graphique (facultatif). L'icône de seuil apparaît sur le graphique à côté du point de données où la violation de seuil s'est produite.

 Dans l'arborescence de compteurs, l'icône de violation de seuil est propagée du nœud de compteur spécifique jusqu'au nœud racine. Ceci vous signale une violation sur un compteur qui n’est pas forcément visible dans l’arborescence, car elle n’a pas été développée.

 Pour plus d’informations, consultez [Utilisation du volet Compteurs dans la vue Graphiques et la vue Tables](../test/counters-panel-in-load-test-analyzer.md).

## <a name="view-threshold-violations-on-the-graph"></a>Affichage des violations de seuil sur le graphique

 Vous pouvez afficher les violations de seuils sur le graphique. Comme sur le volet **Compteurs**, des icônes indiquent les violations de seuil sur le graphique. Les icônes apparaissent sur le graphique à côté du point de données où la violation de seuil s'est produite. Si une violation de seuil se produit sur un compteur qui n’apparaît pas sur le graphique, vous pouvez l’ajouter au graphique en le faisant glisser depuis le volet **Compteurs** vers le graphique.

 Pour plus d’informations, consultez [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Voir aussi

- [Spécification des ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)