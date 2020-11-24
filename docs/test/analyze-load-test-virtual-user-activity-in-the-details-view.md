---
title: Analyse de l'activité des utilisateurs virtuels d'un test de charge
description: En savoir plus sur le mode Détails, qui affiche le graphique d’activités des utilisateurs virtuels. Analyser les utilisateurs virtuels individuels qui ont été exécutés pendant le test de charge.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5c05a907bf75ffcdff5bb579ec2624e0dc8a7df9
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441896"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analyse de l’activité des utilisateurs virtuels d’un test de charge dans la vue Détails de l’analyseur de test de charge

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Graphique d’activités des utilisateurs virtuels**

![Graphique d'activités des utilisateurs virtuels](../test/media/virtual_actchart.png)

La vue **Détails** affiche le **graphique d’activités des utilisateurs virtuels**, utilisé pour analyser visuellement les actions des utilisateurs virtuels individuels exécutées au cours du test de charge. Le **graphique d’activités des utilisateurs virtuels** permet de visualiser les modèles d’activités des utilisateurs et les modèles de charge, de mettre en corrélation des tests lents ou ayant échoué et de consulter des requêtes basées sur d’autres activités des utilisateurs virtuels. Le **graphique d’activités des utilisateurs virtuels** peut également vous aider à identifier les pics d’utilisation d’une UC ou les chutes d’activité des requêtes par seconde, ainsi que les tests ou pages en cours d’exécution pendant ces pics ou ces chutes.

> [!NOTE]
> Avant d’exécuter le test de charge pour lequel vous souhaitez utiliser le **graphique des détails de l’activité des utilisateurs virtuels**, vous devez vérifier que la propriété **stockage des détails de minuterie** a la valeur **AllIndividualDetails** à l’aide de l’éditeur de test de performances de charge.

**Panneau de légende des détails**

![Panneau Légende du détail](../test/media/ltest_detailslegend.png)

Le panneau Légende du détail est visible dans le **graphique d’activités des utilisateurs virtuels**. Il vous permet de filtrer les tests, les pages et les transactions en fonction de plusieurs critères différents. Par exemple, vous pouvez supprimer certains tests de la vue, supprimer tous les tests réussis ou supprimer les tests qui ont abouti à certains échecs. Vous pouvez également supprimer tous les tests qui n'ont pas de journaux.

Vous pouvez mettre en surbrillance les tests ayant échoué, ce qui entraîne l'affichage en rouge de tous les tests qui n'ont pas réussi. Vous pouvez également mettre en surbrillance les tests qui ont des journaux des tests. Les tests qui ont des journaux prennent une couleur verte.

**Panneau résultats du filtre**

![Panneau de filtrage des résultats](../test/media/ltest_filterresults.png)

Le panneau Résultats du filtre est visible dans le **graphique d’activités des utilisateurs virtuels**. Le panneau Résultats du filtre peut filtrer en fonction des éléments suivants :

- **Indiquer uniquement les résultats avec journaux** Affiche uniquement les résultats des tests associés à des journaux des tests.

- **Afficher les résultats réussis** Affiche les résultats réussis.

- **Afficher les résultats avec des erreurs** Affiche les résultats comportant des erreurs qui peuvent être utiles au débogage.

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-|-|
|**Exécutez votre test de charge :** Une fois que vous avez créé un test de charge et que vous l’avez configuré pour activer la collecte des données d’activités des utilisateurs virtuels, vous devez exécuter le test jusqu’à ce qu’il soit terminé afin d’afficher le **graphique d’activités des utilisateurs virtuels**.||
|**Affichez les résultats des tests de charge qui contiennent les données d’activités des utilisateurs virtuels :** Une fois que votre test de charge a été créé, configuré et que l’exécution est terminée, vous pouvez afficher les données d’activité des utilisateurs virtuels à l’aide du **graphique d’activités des utilisateurs virtuels**.|-   [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Comment : analyser ce que font les utilisateurs virtuels pendant un test de charge](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Isoler les problèmes de performances dans les tests de charge :** Vous pouvez utiliser le **graphique d’activités des utilisateurs virtuels** pour aider à isoler les problèmes de performances dans votre test de charge.|-   [Procédure pas à pas : utilisation du graphique d’activités des utilisateurs virtuels pour isoler les problèmes](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
