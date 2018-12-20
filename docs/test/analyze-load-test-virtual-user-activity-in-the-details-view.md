---
title: Analyse de l'activité des utilisateurs virtuels d'un test de charge
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ff4d71af450fa6d3f907bb1e1b5b963044e959ff
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059906"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analyse de l’activité des utilisateurs virtuels d’un test de charge dans la vue Détails de l’analyseur de test de charge

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Graphique d’activités des utilisateurs virtuels**

![Graphique d'activités des utilisateurs virtuels](../test/media/virtual_actchart.png)

La vue **Détails** affiche le **graphique d’activités des utilisateurs virtuels**, utilisé pour analyser visuellement les actions des utilisateurs virtuels individuels exécutées au cours du test de charge. Le **graphique d’activités des utilisateurs virtuels** permet de visualiser les modèles d’activités des utilisateurs et les modèles de charge, de mettre en corrélation des tests lents ou ayant échoué et de consulter des requêtes basées sur d’autres activités des utilisateurs virtuels. Le **graphique d’activités des utilisateurs virtuels** peut également vous aider à identifier les pics d’utilisation d’une UC ou les chutes d’activité des requêtes par seconde, ainsi que les tests ou pages en cours d’exécution pendant ces pics ou ces chutes.

> [!NOTE]
> Avant d’exécuter le test de charge pour lequel vous souhaitez utiliser le **graphique d’activités des utilisateurs virtuels**, vous devez vérifier que la propriété **Stockage des détails de minuterie** a la valeur **AllIndividualDetails** à l’aide de l’éditeur de test de charge.

 **Panneau Légende du détail**

 ![Panneau Légende du détail](../test/media/ltest_detailslegend.png)

 Le panneau Légende du détail est visible dans le **graphique d’activités des utilisateurs virtuels**. Il vous permet de filtrer les tests, les pages et les transactions en fonction de plusieurs critères différents. Par exemple, vous pouvez supprimer certains tests de la vue, supprimer tous les tests réussis ou supprimer les tests qui ont abouti à certains échecs. Vous pouvez également supprimer tous les tests qui n'ont pas de journaux.

 Vous pouvez mettre en surbrillance les tests ayant échoué, ce qui entraîne l'affichage en rouge de tous les tests qui n'ont pas réussi. Vous pouvez également mettre en surbrillance les tests qui ont des journaux des tests. Les tests qui ont des journaux prennent une couleur verte.

 **Panneau Filtrer les résultats**

 ![Panneau de filtrage des résultats](../test/media/ltest_filterresults.png)

 Le panneau Résultats du filtre est visible dans le **graphique d’activités des utilisateurs virtuels**. Le panneau Résultats du filtre peut filtrer en fonction des éléments suivants :

-   **Indiquer uniquement les résultats avec journaux** Affiche uniquement les résultats des tests associés à des journaux des tests.

-   **Afficher les résultats réussis** Affiche les résultats réussis.

-   **Afficher les résultats avec des erreurs** Affiche les résultats comportant des erreurs qui peuvent être utiles au débogage.

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-|-|
|**Exécuter votre test de charge :** une fois que vous avez créé un test de charge et que vous l’avez configuré pour la collecte des données d’activité des utilisateurs virtuels, vous devez exécuter le test jusqu’à son terme pour pouvoir consulter le **graphique d’activités des utilisateurs virtuels**.||
|**Afficher les résultats des tests de charge qui contiennent des données d’activité des utilisateurs virtuels :** à la fin de la création, de la configuration et de l’exécution de votre test de charge, vous pouvez consulter les données d’activité des utilisateurs virtuels à l’aide du **graphique d’activités des utilisateurs virtuels**.|-   [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Guide pratique pour analyser l’activité des utilisateurs virtuels durant un test de charge](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Isoler les problèmes de performances dans les tests de charge :** vous pouvez utiliser le **graphique d’activités des utilisateurs virtuels** pour contribuer à isoler les problèmes de performances dans votre test de charge.|-   [Procédure pas à pas : Utilisation du graphique d’activités des utilisateurs virtuels pour isoler les problèmes](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)