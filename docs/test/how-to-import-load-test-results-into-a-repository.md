---
title: Guide pratique pour importer les résultats des tests de charge dans un dépôt au sein de Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 1d9f94641fe3249e6aa36b01b408abd66781b81f
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Comment : importer les résultats d'un test de charge dans un référentiel

Lorsque vous exécutez un test de charge, les informations recueillies au cours de l'exécution sont stockées dans le référentiel des résultats des tests de charge. Ce référentiel contient des données de compteurs de performance et des informations relatives aux erreurs. Pour plus d’informations, consultez [Gestion des résultats des tests de charge dans le dépôt des résultats de tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md).

 Vous pouvez gérer les résultats des tests de charge à partir de l’éditeur de test de charge via la boîte de dialogue **Ouvrir et gérer des résultats des tests de charge**. Vous pouvez ouvrir, importer, exporter et supprimer les résultats des tests de charge.

## <a name="to-import-results-into-a-repository"></a>Pour importer les résultats dans un référentiel

1.  Depuis un projet de test de performances de site Web et de charge, ouvrez un test de charge.

2.  Dans la barre d’outils incorporée, choisissez **Ouvrir et gérer des résultats**.

     La boîte de dialogue **Ouvrir et gérer des résultats des tests de charge** s’affiche.

3.  Dans **Entrer un nom de contrôleur pour rechercher les résultats des tests de charge**, sélectionnez un contrôleur. Sélectionnez **\<local>** pour accéder aux résultats stockés localement.

     Si des résultats des tests de charge sont disponibles, ceux-ci apparaissent dans la liste **Résultats du test de charge**. Les colonnes sont **Heure**, **Durée**, **Utilisateur**, **Résultat**, **Test** et **Description**. **Test** contient le nom du test et **Description** contient la description facultative qui est ajoutée avant l’exécution du test.

4.  Choisissez **Importer**.

     La boîte de dialogue **Importer les résultats des tests de charge** s’affiche.

5.  Dans la zone **Nom de fichier**, tapez le nom d’un fichier de résultats des tests archivés, puis choisissez **Ouvrir**.

     \- ou -

     Recherchez le fichier, puis choisissez **Ouvrir**.

    > [!NOTE]
    > Un fichier de résultats des tests archivés spécifié à cette étape a dû être créé en exécutant l'opération d'exportation.

     Les résultats sont importés et apparaissent dans la liste **Résultats du test de charge**.

## <a name="see-also"></a>Voir aussi

- [Gestion des résultats des tests de charge dans le référentiel des résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Guide pratique pour exporter les résultats des tests de charge à partir d’un référentiel](../test/how-to-export-load-test-results-from-a-repository.md)