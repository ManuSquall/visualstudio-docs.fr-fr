---
title: 'Procédure : supprimer des résultats des tests de charge dans un dépôt'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, deleting results
- load test results, removing
- Load Test Results Repository
- load tests, removing results
- load test results, deleting
ms.assetid: c2afe36b-d061-4f0e-9580-c18569ec08f9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: e2a7df778ff506c76513af6e6fe926a193f6a18e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065272"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Procédure : supprimer des résultats des tests de charge dans un dépôt

Lorsque vous exécutez un test de charge, les informations recueillies au cours de l'exécution sont stockées dans le référentiel des résultats des tests de charge. Ce référentiel contient des données de compteurs de performance et des informations relatives aux erreurs. Pour plus d’informations, consultez [Gérer les résultats des tests de charge dans le référentiel des résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Vous pouvez gérer les résultats des tests de charge à partir de l’éditeur de test de charge via la boîte de dialogue **Ouvrir et gérer des résultats des tests de charge**. Vous pouvez ouvrir, importer, exporter et supprimer les résultats des tests de charge.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Pour supprimer les résultats à partir d'un référentiel

1.  Depuis un projet de test de performances web et de charge, ouvrez un test de charge.

2.  Dans la barre d’outils incorporée, choisissez **Ouvrir et gérer des résultats**.

     La boîte de dialogue **Ouvrir et gérer des résultats des tests de charge** s’affiche.

3.  Dans **Entrer un nom de contrôleur pour rechercher les résultats des tests de charge**, sélectionnez un contrôleur. Sélectionnez **\<Local - Aucun contrôleur** pour accéder aux résultats stockés localement.

4.  Dans **Afficher les résultats pour le test de charge suivant**, sélectionnez le test de charge dont vous voulez voir les résultats. Sélectionnez **\<Afficher les résultats de tous les tests** pour voir les résultats de tous les tests.

     Si les résultats du test de charge sont disponibles, ils apparaissent dans la liste **Résultats du test de charge**. Les colonnes sont **Heure**, **Durée**, **Utilisateur**, **Résultat**, **Test** et **Description**. **Test** contient le nom du test et **Description** contient la description facultative qui est ajoutée avant l’exécution du test. La colonne **Description** affiche les descriptions courtes qui sont entrées dans les **Commentaires d’analyse** pour ce résultat de test.

5.  Dans la liste **Résultats du test de charge**, choisissez un résultat. Vous pouvez utiliser la touche **Maj**, la touche **Ctrl**, ou les deux à la fois pour sélectionner plusieurs résultats.

6.  Choisissez **Supprimer**.

     Les résultats sont supprimés du référentiel.

    > [!NOTE]
    > La boîte de dialogue **Ouvrir et gérer des résultats des tests de charge** reste ouverte après que les résultats ont été supprimés.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour exporter des résultats des tests de charge à partir d’un dépôt](../test/how-to-export-load-test-results-from-a-repository.md)
- [Gérer des résultats des tests de charge dans le référentiel des résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Guide pratique pour importer des résultats des tests de charge dans un dépôt](../test/how-to-import-load-test-results-into-a-repository.md)