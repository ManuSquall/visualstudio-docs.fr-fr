---
title: Exporter les résultats des tests de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 080bdfd79ee1fce4015fc2db9a695cb55c417165
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178768"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Comment : exporter les résultats des tests de charge à partir d'un référentiel

Lorsque vous exécutez un test de charge, les informations recueillies au cours de l'exécution sont stockées dans le référentiel des résultats des tests de charge. Ce référentiel contient des données de compteurs de performance et des informations relatives aux erreurs. Pour plus d’informations, consultez [Gestion des résultats des tests de charge dans le dépôt des résultats de tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Vous pouvez gérer les résultats des tests de charge à partir de l’éditeur de test de charge via la boîte de dialogue **Ouvrir et gérer des résultats des tests de charge**. Vous pouvez ouvrir, importer, exporter et supprimer les résultats des tests de charge.

## <a name="to-export-results-from-a-repository"></a>Pour exporter les résultats à partir d'un référentiel

1.  Depuis un projet de test de performances web et de charge, ouvrez un test de charge.

2.  Dans la barre d’outils incorporée, choisissez **Ouvrir et gérer des résultats**.

     La boîte de dialogue **Ouvrir et gérer des résultats des tests de charge** s’affiche.

3.  Dans **Entrer un nom de contrôleur pour rechercher les résultats des tests de charge**, sélectionnez un contrôleur. Sélectionnez **\<Local - Aucun contrôleur** pour accéder aux résultats stockés localement.

4.  Dans **Afficher les résultats pour le test de charge suivant**, sélectionnez le test de charge dont vous voulez voir les résultats. Sélectionnez **\<Afficher les résultats de tous les tests** pour voir les résultats de tous les tests.

     Si les résultats du test de charge sont disponibles, ils apparaissent dans la liste **Résultats du test de charge**. Les colonnes sont **Heure**, **Durée**, **Utilisateur**, **Résultat**, **Test** et **Description**. **Test** contient le nom du test et **Description** contient la description facultative qui est ajoutée avant l’exécution du test. La colonne **Description** affiche les descriptions courtes qui sont entrées dans les **Commentaires d’analyse** pour ce résultat de test.

5.  Dans la liste **Résultats du test de charge**, choisissez un résultat. Vous pouvez utiliser la touche Maj, la touche Ctrl, ou les deux, pour sélectionner plusieurs résultats et les exporter vers un fichier unique.

6.  Choisissez **Exporter**.

     La boîte de dialogue **Exporter des résultats des tests de charge** apparaît.

7.  Dans la zone **Nom de fichier**, tapez un nom, puis choisissez **Enregistrer**.

     Les résultats sont exportés vers un fichier d'archives.

    > [!NOTE]
    > La boîte de dialogue **Ouvrir et gérer des résultats des tests de charge** reste ouverte après que les résultats sont apparus.

## <a name="see-also"></a>Voir aussi

- [Gestion des résultats des tests de charge dans le référentiel des résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Guide pratique pour supprimer les résultats d’un test de charge d’un référentiel](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Guide pratique pour importer les résultats d’un test de charge dans un référentiel](../test/how-to-import-load-test-results-into-a-repository.md)