---
title: "Comment : supprimer les résultats d'un test de charge d'un référentiel"
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26dc9750a2bf2eaf5d0ee5dd3d08485c458bb74a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589056"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Guide pratique pour supprimer les résultats d’un test de charge d’un référentiel

Lorsque vous exécutez un test de charge, les informations recueillies au cours de l'exécution sont stockées dans le référentiel des résultats des tests de charge. Ce référentiel contient des données de compteurs de performance et des informations relatives aux erreurs. Pour plus d’informations, consultez [Gérer les résultats des tests de charge dans le référentiel des résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Vous pouvez gérer les résultats des tests de charge à partir de l’éditeur de test de charge via la boîte de dialogue **Ouvrir et gérer des résultats des tests de charge**. Vous pouvez ouvrir, importer, exporter et supprimer les résultats des tests de charge.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Pour supprimer les résultats à partir d'un référentiel

1. Depuis un projet de test de performances web et de charge, ouvrez un test de charge.

2. Dans la barre d’outils incorporée, choisissez **Ouvrir et gérer des résultats**.

     La boîte de dialogue **Ouvrir et gérer des résultats des tests de charge** s’affiche.

3. Dans **Entrer un nom de contrôleur pour rechercher les résultats des tests de charge**, sélectionnez un contrôleur. Sélectionnez **\<Local - Aucun contrôleur** pour accéder aux résultats stockés localement.

4. Dans **Afficher les résultats pour le test de charge suivant**, sélectionnez le test de charge dont vous souhaitez consulter les résultats. Sélectionnez **\<Afficher les résultats de tous les tests>** pour consulter les résultats de tous les tests.

     Si les résultats du test de charge sont disponibles, ils apparaissent dans la liste **Résultats du test de charge**. Les colonnes sont **Heure**, **Durée**, **Utilisateur**, **Résultat**, **Test** et **Description**. **Test** contient le nom du test et **Description** contient la description facultative qui est ajoutée avant l’exécution du test. La colonne **Description** affiche les descriptions courtes qui sont entrées dans les **Commentaires d’analyse** pour ce résultat de test.

5. Dans la liste **Résultats du test de charge**, choisissez un résultat. Vous pouvez utiliser la touche **Maj**, la touche **Ctrl**, ou les deux à la fois pour sélectionner plusieurs résultats.

6. Choisissez **Supprimer**.

     Les résultats sont supprimés du référentiel.

    > [!NOTE]
    > La boîte de dialogue **Ouvrir et gérer des résultats des tests de charge** reste ouverte après que les résultats ont été supprimés.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour exporter les résultats des tests de charge à partir d’un référentiel](../test/how-to-export-load-test-results-from-a-repository.md)
- [Gérer des résultats des tests de charge dans le référentiel des résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Guide pratique pour importer les résultats d’un test de charge dans un référentiel](../test/how-to-import-load-test-results-into-a-repository.md)
