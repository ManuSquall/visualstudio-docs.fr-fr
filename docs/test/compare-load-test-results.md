---
title: Comparaison des résultats des tests de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, results
ms.assetid: 31874114-459a-45d5-9f8b-2ea503627db8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: a2986c22dabc25e2db1e48e8308aa066ce6ca109
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921828"
---
# <a name="report-load-tests-results-for-test-comparisons-or-trend-analysis"></a>Créer des rapports sur les résultats des tests de charge pour les comparaisons de tests ou l’analyse des tendances

Vous pouvez créer des rapports de test de charge Microsoft Excel basés sur au moins deux résultats de tests.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Deux types de rapports de test de charge sont disponibles :

- Exécuter la comparaison&mdash;Ce rapport correspond en réalité à deux rapports qui présentent des données de comparaison côte à côte sous forme de tableaux et de graphiques à barres.

- Tendance&mdash;Ce rapport génère une analyse de tendances sur la base d’au moins deux rapports. Les résultats sont présentés sous forme de graphiques en courbes.

Chaque type de rapport permet de partager des données de performance avec les parties prenantes et d'indiquer si l'intégrité et les performances globales du système s'améliorent ou empirent.

Les définitions des rapports sont stockées dans la base de données de tests de charge. Une fois un rapport enregistré, sa définition est enregistrée dans la base de données et peut être réutilisée par la suite.

Le fichier de feuille de calcul peut être partagé avec les parties prenantes sans que ceux-ci aient à se connecter à la base de données pour consulter le rapport.

> [!NOTE]
> Si vous ajoutez des commentaires à un test de charge, ils apparaissent dans le rapport Excel.

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-|-|
|**Créer un rapport sur les tests de performances et de contrainte :** vous pouvez créer des rapports sur vos tests de performances web et de charge avec Microsoft Excel.|- [Guide pratique pour créer des rapports de performances de test de charge à l’aide de Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)|
|**Créer manuellement un rapport de performances et de contrainte avec Microsoft Word :** vous pouvez créer manuellement des rapports sur vos tests de performances web et de charge en copiant et en collant les données de synthèse, de table et de graphe dans un document Microsoft Word.|- [Guide pratique pour créer manuellement un rapport de performances de test de charge à l’aide de Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md)|

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)