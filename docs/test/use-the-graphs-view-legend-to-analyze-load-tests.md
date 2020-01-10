---
title: Utilisation de la légende de la vue Graphiques pour analyser des tests de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1455c67c3cb6d8dc99aeab91a7bfa63cce009c51
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590798"
---
# <a name="use-the-graphs-view-legend-to-analyze-load-tests"></a>Utiliser la légende de la vue Graphiques pour analyser des tests de charge

La vue Graphiques de l'outil Analyseur de test de charge inclut le volet de la légende qui affiche des informations sur chaque compteur de performance associé au graphique actuellement sélectionné.

![Légende de la vue Graphiques](../test/media/load_viewlegend.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Les informations suivantes sont contenues dans la légende :

- **Afficher sur le graphique :** Utilisez les cases à cocher pour indiquer si la ligne d’un compteur particulier, comme **Charge utilisateur** ou **Erreurs/s**, est tracée sur le graphique. Activez une case à cocher pour que la ligne soit tracée sur le graphique. Désactivez une case à cocher pour supprimer du graphique la ligne du tracé. Lorsqu'une ligne de tracé est supprimée, les statistiques du compteur continuent à s'afficher dans la légende.

- **Plage :** cette colonne affiche la plage de l’axe Y du compteur de performances. Par défaut, cette valeur s'ajuste automatiquement au fur et à mesure que la plage des exemples de données évolue. Une plage ajustée automatiquement sera toujours la puissance 10 supérieure à la valeur Max ; cela inclut les puissances 10 négatives. Un graphique peut contenir divers compteurs, chacun avec une plage différente. Par conséquent, l'axe Y n'est pas étiqueté avec un plage spécifique, mais est étiqueté avec les valeurs comprises entre 0 et 100 qui représentent un pourcentage de la plage totale de chaque compteur. Par exemple, pour un compteur avec une plage de 1 000, un point de données de 60 sur l'axe Y correspondrait à une valeur de 600 pour le compteur.

    > [!NOTE]
    > Vous pouvez désactiver le réglage automatique des valeurs de la plage en verrouillant la plage sur une valeur spécifique. Lorsque la plage est verrouillée, toutes les valeurs qui dépassent la plage s'affichent comme valeur maximale spécifiée en haut du graphique. Utilisez la boîte de dialogue **Options de tracé** pour verrouiller la plage sur une valeur spécifique.

- **Compteur :** Les quatre colonnes nommées **Compteur**, **Instance**, **Catégorie** et **Ordinateur** identifient le compteur de performances de manière unique.

- **Couleur :** La colonne **Couleur** affiche la couleur et le style de la ligne tracée pour le compteur de performances. Utilisez la boîte de dialogue **Options de tracé** pour modifier la couleur ou le style de ligne d’un compteur de performances sur le graphique. La boîte de dialogue **Options de tracé** est disponible dans le menu contextuel de la légende.

- **Statistiques :** Les colonnes **Min**, **Max**, **Moy** et **Dernier** affichent les statistiques respectives relatives au compteur de performances. Ces valeurs correspondent aux données affichées dans la région visible du graphique. Par exemple, si vous appliquez un zoom avant sur une région d'une exécution, les statistiques de la légende reflètent uniquement les valeurs de la zone zoomée. La colonne « Dernier » correspond à la valeur du compteur de performance sur le dernier intervalle d'échantillonnage effectué.

    > [!NOTE]
    > La colonne Dernier s'affiche uniquement dans la légende de l'outil Analyseur de test de charge pendant l'exécution du test de charge.

     Pour plus d’informations, consultez [Guide pratique pour faire un zoom avant sur une région du graphique](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

La sélection d'un élément dans la légende effectue les opérations suivantes :

- Autorise la suppression de l'élément dans la légende et dans le graphique. Cliquez avec le bouton droit sur l’élément et sélectionnez **Supprimer**, ou appuyez sur la touche **Supprimer**.

- Met en surbrillance la ligne tracée sur le graphique.

- Affiche dans la grille de données les données de l'élément sélectionné.

- Permet d’accéder à la boîte de dialogue **Options de tracé** pour le compteur.

> [!TIP]
> Vous pouvez utiliser le bouton de la liste déroulante **Options des diagrammes** dans la barre d’outils de **l’Analyseur de test de charge** et sélectionner **Afficher la légende** pour afficher ou masquer le volet **Légende** associé à la vue du graphique.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour faire un zoom avant sur une région du graphique](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md)
