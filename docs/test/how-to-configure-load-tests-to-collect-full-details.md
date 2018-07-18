---
title: Collecter les détails complets des utilisateurs virtuels pour un test de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart, configuring
- virtual user activity chart, configuring
ms.assetid: cb22e43b-af4d-4e09-9389-3c3fa00786f7
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: cac171d6f0e1bcd91a89be799497b84dc15fc5a5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31967094"
---
# <a name="how-to-configure-load-tests-to-collect-full-details-to-enable-virtual-user-activity-in-test-results"></a>Comment : configurer les tests de charge pour collecter les détails complets afin d'activer le graphiques d'activités des utilisateurs virtuels dans les résultats des tests

Pour utiliser le graphique d'activités des utilisateurs virtuels pour votre test de charge, vous devez configurer ce dernier afin qu'il collecte les détails complets. Pour ce faire, sélectionnez le paramètre **Tous les détails individuels** de la propriété **Stockage des détails de minuterie** associée à votre test de charge. Dans ce mode, votre test de charge collecte des informations détaillées sur chaque test, page et transaction.

 Si vous mettez à niveau un projet à partir d’une version antérieure du test de charge Visual Studio, utilisez les étapes de la procédure suivante pour activer la collection des détails complets.

 Le paramètre **Tous les détails individuels** de la propriété **Stockage des détails de minuterie** peut avoir pour valeur chacune des options suivantes :

-   **Tous les détails individuels :** collecte et stocke les données de temporisation individuelles pour chaque test, transaction et page émis pendant le test.

    > [!NOTE]
    > L’option **Tous les détails individuels** doit être sélectionnée pour activer les informations relatives aux données des utilisateurs virtuels dans vos résultats des tests de charge.

-   **Aucune :** ne collecte aucun détail de minuterie. Toutefois, les valeurs moyennes sont toujours disponibles.

-   **Statistiques uniquement :** stocke les données de temporisation individuelles, mais uniquement en tant que centiles. Cela permet d'économiser les ressources en matière d'espace.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Pour configurer la propriété de stockage des détails de minuterie dans un test de charge

1.  Ouvrez un test de charge dans l'éditeur de test de charge.

2.  Développez le nœud **Paramètres d’exécution** dans le test de charge.

3.  Choisissez les paramètres d’exécution à configurer, par exemple **Paramètres d’exécution1[Actifs]**.

4.  Ouvrez la fenêtre Propriétés. Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

5.  Sous la catégorie **Résultats**, choisissez la propriété **Stockage des détails de minuterie**, puis sélectionnez **Tous les détails individuels**.

     Après avoir configuré le paramètre **Tous les détails individuels** de la propriété **Stockage des détails de minuterie**, vous pouvez exécuter votre test de charge et consulter le graphique d’activités des utilisateurs virtuels. Pour plus d’informations, consultez [Guide pratique pour analyser l’activité des utilisateurs virtuels durant un test de charge](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Voir aussi

- [Analyse de l’activité des utilisateurs virtuels dans la vue Détails](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Procédure pas à pas : utilisation du graphique d’activités des utilisateurs virtuels pour isoler les problèmes](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)