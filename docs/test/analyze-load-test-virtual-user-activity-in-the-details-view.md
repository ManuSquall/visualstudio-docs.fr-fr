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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0289ff0d4a20eacc4f6801d9300d39df594bc79e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591233"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analyse de l’activité des utilisateurs virtuels d’un test de charge dans la vue Détails de l’analyseur de test de charge

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Graphique d’activités des utilisateurs virtuels**

![Graphique d'activités des utilisateurs virtuels](../test/media/virtual_actchart.png)

La vue **Détails** affiche le **graphique d’activités des utilisateurs virtuels**, utilisé pour analyser visuellement les actions des utilisateurs virtuels individuels exécutées au cours du test de charge. Le **graphique d’activités des utilisateurs virtuels** permet de visualiser les modèles d’activités des utilisateurs et les modèles de charge, de mettre en corrélation des tests lents ou ayant échoué et de consulter des requêtes basées sur d’autres activités des utilisateurs virtuels. Le **graphique d’activités des utilisateurs virtuels** peut également vous aider à identifier les pics d’utilisation d’une UC ou les chutes d’activité des requêtes par seconde, ainsi que les tests ou pages en cours d’exécution pendant ces pics ou ces chutes.

> [!NOTE]
> Avant d’exécuter le test de chargement pour lequel vous souhaitez utiliser le **graphique virtuel des détails d’activité des utilisateurs,** vous devez vérifier que la propriété de stockage des détails de **synchronisation** est définie à l’option **AllIndividualDetails** en utilisant l’éditeur de test de performance de charge.

**Détails Legend Panel**

![Panneau Légende du détail](../test/media/ltest_detailslegend.png)

Le panneau Légende du détail est visible dans le **graphique d’activités des utilisateurs virtuels**. Il vous permet de filtrer les tests, les pages et les transactions en fonction de plusieurs critères différents. Par exemple, vous pouvez supprimer certains tests de la vue, supprimer tous les tests réussis ou supprimer les tests qui ont abouti à certains échecs. Vous pouvez également supprimer tous les tests qui n'ont pas de journaux.

Vous pouvez mettre en surbrillance les tests ayant échoué, ce qui entraîne l'affichage en rouge de tous les tests qui n'ont pas réussi. Vous pouvez également mettre en surbrillance les tests qui ont des journaux des tests. Les tests qui ont des journaux prennent une couleur verte.

**Panneau des résultats du filtre**

![Panneau de filtrage des résultats](../test/media/ltest_filterresults.png)

Le panneau Résultats du filtre est visible dans le **graphique d’activités des utilisateurs virtuels**. Le panneau Résultats du filtre peut filtrer en fonction des éléments suivants :

- **Indiquer uniquement les résultats avec journaux** Affiche uniquement les résultats des tests associés à des journaux des tests.

- **Afficher les résultats réussis** Affiche les résultats réussis.

- **Afficher les résultats avec des erreurs** Affiche les résultats comportant des erreurs qui peuvent être utiles au débogage.

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-|-|
|**Exécutez votre test de charge :** Une fois que vous avez créé un test de charge et configuré pour activer la collecte virtuelle de données d’activité utilisateur, vous devez exécuter le test jusqu’à ce qu’il soit complet afin de visualiser le **tableau d’activité des utilisateurs virtuels**.||
|**Afficher les résultats des tests de charge qui contiennent les données d’activité utilisateur virtuelle :** Une fois que votre test de chargement a été créé, configuré et terminé en cours d’exécution, vous pouvez afficher les données d’activité utilisateur virtuel en utilisant le **tableau d’activité des utilisateurs virtuels**.|-   [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Comment : Analyser ce que font les utilisateurs virtuels lors d’un test de charge](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Isoler les problèmes de performance dans les tests de charge :** Vous pouvez utiliser le **tableau d’activité des utilisateurs virtuels** pour aider à isoler les problèmes de performances dans votre test de charge.|-   [Procédure pas à pas : utilisation du tableau virtuel de l’activité utilisateur pour isoler les problèmes](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
