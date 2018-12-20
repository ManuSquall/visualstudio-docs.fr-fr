---
title: 'Procédure : importer les résultats d’un test de charge dans un référentiel'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 4f4b62f13a78ae716fd7bfe4e1a158450590a864
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065984"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Procédure : importer les résultats d’un test de charge dans un référentiel

Lorsque vous exécutez un test de charge, les informations recueillies au cours de l'exécution sont stockées dans le référentiel des résultats des tests de charge. Ce référentiel contient des données de compteurs de performance et des informations relatives aux erreurs. Pour plus d’informations, consultez [Gérer les résultats des tests de charge dans le référentiel des résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Vous pouvez gérer les résultats des tests de charge à partir de l’éditeur de test de charge via la boîte de dialogue **Ouvrir et gérer des résultats des tests de charge**. Vous pouvez ouvrir, importer, exporter et supprimer les résultats des tests de charge.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>Pour importer les résultats dans un référentiel

1.  Depuis un projet de test de performances web et de charge, ouvrez un test de charge.

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

- [Gérer des résultats des tests de charge dans le référentiel des résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Guide pratique pour exporter les résultats des tests de charge à partir d’un référentiel](../test/how-to-export-load-test-results-from-a-repository.md)