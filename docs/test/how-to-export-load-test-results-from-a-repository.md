---
title: Exporter des résultats des tests de charge
description: Découvrez comment exporter des informations à partir du référentiel de Résultats des tests de charge à l’aide de la boîte de dialogue Ouvrir et gérer le Résultats des tests de charge.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a0e7d00949686cd7d52400c2d71123b86d28625b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961506"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Guide pratique pour exporter les résultats des tests de charge à partir d’un référentiel

Lorsque vous exécutez un test de charge, les informations recueillies au cours de l'exécution sont stockées dans le référentiel des résultats des tests de charge. Ce référentiel contient des données de compteurs de performance et des informations relatives aux erreurs. Pour plus d’informations, consultez [gérer les résultats des tests de charge dans le référentiel de résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Vous pouvez gérer les résultats des tests de charge à partir de l’éditeur de test de charge via la boîte de dialogue **Ouvrir et gérer des résultats des tests de charge**. Vous pouvez ouvrir, importer, exporter et supprimer les résultats des tests de charge.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>Pour exporter les résultats à partir d'un référentiel

1. Depuis un projet de test de performances web et de charge, ouvrez un test de charge.

2. Dans la barre d’outils incorporée, choisissez **Ouvrir et gérer des résultats**.

     La boîte de dialogue **Ouvrir et gérer des résultats des tests de charge** s’affiche.

3. Dans **Entrer un nom de contrôleur pour rechercher les résultats des tests de charge**, sélectionnez un contrôleur. Sélectionnez cette option **\<Local - No controller>** pour accéder aux résultats stockés localement.

4. Dans **Afficher les résultats pour le test de charge suivant**, sélectionnez le test de charge dont vous souhaitez consulter les résultats. Sélectionnez cette option **\<Show results for all tests>** pour afficher tous les résultats de tous les tests.

     Si les résultats du test de charge sont disponibles, ils apparaissent dans la liste **Résultats du test de charge**. Les colonnes sont **Heure**, **Durée**, **Utilisateur**, **Résultat**, **Test** et **Description**. **Test** contient le nom du test et **Description** contient la description facultative qui est ajoutée avant l’exécution du test. La colonne **Description** affiche les descriptions courtes qui sont entrées dans les **Commentaires d’analyse** pour ce résultat de test.

5. Dans la liste **Résultats du test de charge**, choisissez un résultat. Vous pouvez utiliser la touche **Maj**, la touche **Ctrl**, ou les deux, pour sélectionner plusieurs résultats et les exporter vers un fichier unique.

6. Choisissez **Export** (Exporter).

     La boîte de dialogue **Exporter des résultats des tests de charge** apparaît.

7. Dans la zone **Nom de fichier**, tapez un nom, puis choisissez **Enregistrer**.

     Les résultats sont exportés vers un fichier d'archives.

    > [!NOTE]
    > La boîte de dialogue **Ouvrir et gérer des résultats des tests de charge** reste ouverte après que les résultats sont apparus.

## <a name="see-also"></a>Voir aussi

- [Gérer les résultats des tests de charge dans le référentiel de Résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Comment : supprimer les résultats d’un test de charge d’un référentiel](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Comment : importer les résultats d’un test de charge dans un référentiel](../test/how-to-import-load-test-results-into-a-repository.md)
