---
title: Propriété stockage des détails de minuterie (paramètre d’exécution du test de charge)
description: Découvrez comment modifier la propriété stockage des détails de minuterie pour un paramètre d’exécution. Les valeurs valides sont tous les détails individuels, aucun et statistiques uniquement.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f208dd19674a257381db6feeaf47df5d3951ff9d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969293"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Guide pratique pour spécifier la propriété de stockage des détails de minuterie d’un paramètre d’exécution de tests de charge

Après avoir créé votre test de charge à l’aide de **l’Assistant Nouveau test de charge**, vous pouvez utiliser **l’éditeur de test de charge** pour changer les paramètres afin de répondre à vos besoins et vos objectifs de test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Vous pouvez modifier la valeur de la propriété **Stockage des détails de minuterie** des paramètres d’exécution dans la fenêtre **Propriétés**. Vous pouvez définir la propriété **Stockage des détails de minuterie** avec l’une des options suivantes :

- **Tous les détails individuels :** Collecte et stocke les données de temporisation individuelles pour chaque test, transaction et page émis pendant le test.

  > [!NOTE]
  > L’option **Tous les détails individuels** doit être sélectionnée pour activer les informations relatives aux données des utilisateurs virtuels dans vos résultats des tests de charge. Pour plus d’informations, voir [Analyser l’activité des utilisateurs virtuels dans la vue Détails](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

- **Aucune :** ne collecte aucun détail de minuterie. Toutefois, les valeurs moyennes sont toujours disponibles.

- **Statistiques uniquement :** Stocke les données de temporisation individuelles, mais uniquement en tant que centiles. Cela permet d'économiser les ressources en matière d'espace.

  **Considérations relatives à la propriété Stockage des détails de minuterie**

  Si la propriété **Stockage des détails de minuterie** est activée, le temps nécessaire à l’exécution de chaque test, transaction et page individuels pendant le test de charge est stocké dans le référentiel des résultats des tests de charge. Cela permet l’affichage des données de quatre-vingt et 95e centile dans l' **Analyseur de test de charge** dans les tables **tests**, **transactions** et **pages** .

  Si la propriété **Stockage des détails de minuterie** est activée et que vous définissez sa valeur avec **StatisticsOnly** ou **AllIndividualDetails**, tous les tests individuels, les pages et les transactions sont chronométrés, et les données de centile sont calculées à partir des données de minutage individuelles. Avec l’option **StatisticsOnly**, après que les données de centile ont été calculées, les données de minutage individuelles sont supprimées du référentiel. Cela réduit la capacité d'espace requise dans le référentiel lorsque vous utilisez des détails de minuterie. Toutefois, vous pouvez traiter les données détaillées de minutage d’une autre façon à l’aide des outils SQL, auquel cas l’option **AllIndividualDetails** doit être utilisée afin que la données détaillées de minutage soient disponibles pour ce traitement. En outre, si vous affectez la valeur **AllIndividualDetails** à la propriété, vous pouvez analyser l’activité des utilisateurs virtuels à l’aide du **graphique d’activités des utilisateurs virtuels** dans l' **Analyseur de test de charge** à l’issue de l’exécution du test de charge. Pour plus d’informations, voir [Analyser l’activité des utilisateurs virtuels dans la vue Détails](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

  La capacité d'espace requise dans le référentiel des résultats du test de charge pour stocker les détails de minuterie peut être très élevée, en particulier pour les longs tests de charge. En deuxième lieu, le temps nécessaire pour stocker ces données dans le référentiel des résultats du test de charge à la fin du test de charge est plus long parce que ces données sont stockées sur les agents de test de charge jusqu'à ce que l'exécution du test de charge soit terminée, après quoi les données sont stockées dans le référentiel. La propriété **Stockage des détails de minuterie** est activée par défaut. Si cela pose un problème pour votre environnement de test, vous pouvez affecter à la propriété **Stockage des détails de minuterie** la valeur **Aucun**.

  Les données détaillées de minutage sont stockées dans le fichier *LoadTestItemResults.dat* pendant l’exécution, et sont transmises au contrôleur à l’issue de l’exécution du test de charge. Pour un test de charge exécuté sur une longue durée, la taille du fichier est volumineuse. Si la capacité d'espace disque est insuffisante sur l'ordinateur de l'agent, cela posera un problème.

  Si vous mettez à niveau un projet à partir d'une version antérieure du test de charge Visual Studio, utilisez la procédure suivante pour activer la collecte des détails complets.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Pour configurer la propriété de stockage des détails de minuterie dans un test de charge

1. Ouvrez un test de charge dans l'éditeur de test de charge.

2. Développez le nœud **Paramètres d’exécution** dans le test de charge.

3. Choisissez les paramètres d’exécution à configurer, par exemple **Paramètres d’exécution1[Actifs]**.

4. Ouvrez la fenêtre **Propriétés** . Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

5. Sous la catégorie **Résultats**, choisissez la propriété **Stockage des détails de minuterie**, puis sélectionnez **Tous les détails individuels**.

     Une fois que vous avez configuré le paramètre **tous les détails individuels** pour la propriété **stockage des détails de minuterie** , vous pouvez exécuter votre test de charge et afficher le graphique d’activités des **utilisateurs virtuels**. Pour plus d’informations, consultez [Guide pratique pour analyser l’activité des utilisateurs virtuels durant un test de charge](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Voir aussi

- [Analyse de l’activité des utilisateurs virtuels dans la vue Détails](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Procédure pas à pas : utilisation du graphique d’activités des utilisateurs virtuels pour isoler les problèmes](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
