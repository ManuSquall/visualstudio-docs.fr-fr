---
title: Analyser l’activité des utilisateurs virtuels pour les tests de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: 714e38e6bf0ca97e683eda6e5cd6303b9f1160fa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875269"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Procédure : analyser l’activité des utilisateurs virtuels durant un test de charge à l’aide du graphique d’activités des utilisateurs virtuels

Affichez les activités des utilisateurs virtuels associées à votre test de charge à l'aide du **graphique d'activités des utilisateurs virtuels**. Chaque ligne du graphique représente un utilisateur virtuel individuel. Le **graphique d'activités des utilisateurs virtuels** vous montre exactement ce que chaque utilisateur virtuel faisait pendant le test. Cela vous permet de visualiser les modèles d’activités des utilisateurs, de charger des modèles, de mettre en corrélation les tests lents ou non aboutis, et de consulter les requêtes basées sur d’autres activités d’utilisateurs virtuels. Le **graphique d'activités des utilisateurs virtuels** est disponible uniquement après que le test de charge a terminé de s'exécuter.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Les procédures suivantes montrent comment consulter le **graphique d'activités des utilisateurs virtuels**, comment examiner les activités d'utilisateurs spécifiques, et comment utiliser le filtrage.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Pour consulter le graphique d'activités des utilisateurs virtuels dans vos résultats de test de charge

1.  Pour consulter les données des utilisateurs virtuels, vous devez d’abord configurer le paramètre **Tous les détails individuels** pour la propriété **Stockage des détails de minuterie** associée à votre test de charge. Exécutez ensuite le test de charge.

2.  Après l'exécution de votre test de charge, la page de résumé des résultats des tests s'affiche. Choisissez le bouton **Détail de l’utilisateur** dans la barre d’outils.

     - ou -

     Ouvrez la vue Graphiques en choisissant le bouton **Graphiques** dans la barre d’outils. Cliquez avec le bouton droit sur un graphique, puis sélectionnez **Accéder au détail de l’utilisateur**.

     Si vous utilisez cette option, le **graphique d'activités des utilisateurs virtuels** affiche un zoom automatique de la partie du test sur laquelle vous avez cliqué avec le bouton droit. Par exemple, si votre pointeur se trouve approximativement à la marque des 30 secondes, l’affichage Détails s’effectuera à peu près à la marque des 30 secondes dans l’outil **Zoomer sur la période de temps** au bas du **Graphique d’activités des utilisateurs virtuels**.

     Vous pouvez ensuite examiner les activités d'un utilisateur spécifique dans le **graphique d'activités des utilisateurs virtuels**.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Pour examiner les activités d'un utilisateur spécifique dans le graphique d'activités des utilisateurs virtuels

1. Utilisez l'outil Zoomer sur la période de temps au bas du **graphique d'activités des utilisateurs virtuels** pour sélectionner une zone du graphique à examiner pour un utilisateur spécifique.

2. Pointez sur un détail du graphique. Notez que les informations suivantes sont affichées dans l'info-bulle :

   - **Identifiant utilisateur**

   - **Scénario**

   - **Test**

   - **URL** (ne s’affiche pas dans un test ou une transaction)

   - **Résultat**

   - **Navigateur** (ne s’affiche pas dans un test ou une transaction)

   - **Network**

   - **Heure de début**

   - **Durée**

   - **Agent**

   - **Journal des tests** (lien vers le journal des tests)

     > [!NOTE]
     > Afin de faciliter le débogage de votre application, si vous choisissez le lien **Journal des tests**, le résultat du test web ou du test unitaire associé au journal s'ouvre.

     Vous pouvez ensuite utiliser les opérations de filtrage et de mise en surbrillance disponibles dans le **graphique d'activités des utilisateurs virtuels**.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Pour utiliser les options de filtrage dans le graphique d'activités des utilisateurs virtuels

1. Dans **Légende du détail**, utilisez la liste déroulante pour sélectionner **Test**, **Page** ou **Transaction**.

    **Panneau Légende du détail**

    ![Panneau Légende du détail](../test/media/ltest_detailslegend.png)

2. Activez ou désactivez les cases à cocher pour les erreurs, les journaux, les tests, la recherche et les pages aspx associés au test de charge.

    Le **graphique d'activités des utilisateurs virtuels** est mis à jour en conséquence.

    Le **graphique d’activités des utilisateurs virtuels** permet de filtrer les tests, les pages et les transactions en fonction de plusieurs critères différents. Vous pouvez supprimer certains tests de la vue, supprimer tous les tests réussis ou supprimer les tests qui ont abouti à certains échecs. Vous pouvez également supprimer tous les tests qui n'ont pas de journaux.

    Par exemple, vous pouvez sélectionner l’option **(Surligner les erreurs)**, qui affiche toutes les erreurs du graphique en rouge. Vous pouvez également sélectionner l’option **(Surligner les résultats avec fichiers journaux)**, qui affiche tous les résultats des tests dont les journaux apparaissent en vert dans le graphique.

    **Panneau Filtrer les résultats**

    ![Panneau de filtrage des résultats](../test/media/ltest_filterresults.png)

3. Dans les **résultats de filtrage**, activez ou désactivez les cases à cocher des options de filtrage suivantes :

   - **Indiquer uniquement les résultats avec journaux** Affiche uniquement les résultats des tests associés à des journaux des tests.

   - **Afficher les résultats réussis** Affiche les résultats réussis.

   - **Afficher les résultats avec des erreurs** Affiche les résultats comportant des erreurs pouvant être utiles au débogage.

     > [!NOTE]
     > Vous pouvez examiner de manière plus approfondie la liste des types d’erreur répertoriés sous le nœud **Afficher les résultats avec des erreurs** en choisissant le bouton **Tables** dans la barre d’outils de l’**Afficheur de résultats de test de performances web**. Pour plus d’informations, consultez [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     Le **graphique d'activités des utilisateurs virtuels** est mis à jour en conséquence.

## <a name="see-also"></a>Voir aussi

- [Analyse de l’activité des utilisateurs virtuels dans la vue Détails](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Procédure pas à pas : Utilisation du graphique d’activités des utilisateurs virtuels pour isoler les problèmes](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)