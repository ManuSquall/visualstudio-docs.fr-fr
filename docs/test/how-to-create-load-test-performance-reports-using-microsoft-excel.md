---
title: Créer des rapports de performances de test de charge à l’aide de Microsoft Excel
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6bd73c643cdc01be07d56857f65d3fb34c6346e0
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747578"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Procédure : créer des rapports de performances de test de charge à l’aide de Microsoft Excel

Vous pouvez créer des rapports de test de charge Microsoft Excel basés sur au moins deux résultats de tests.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Deux types de rapports de test de charge sont disponibles :

- **Comparaison de séries** Ce rapport crée un ensemble de rapports qui permettent de comparer les données de deux résultats de test de charge à l’aide de tables et de graphiques à barres.

- **Tendance** Ce rapport génère une analyse de tendances sur la base d’au moins deux résultats de test de charge. Les résultats sont affichés à l'aide de graphiques en courbes, mais les données sont disponibles dans des tableaux croisés dynamique.

> [!TIP]
> Vous pouvez également créer manuellement des rapports Microsoft Word en copiant et collant des données des vues Résumé, Graphiques et Tables. Consultez [Guide pratique pour créer manuellement un rapport de performances de test de charge à l’aide de Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

Chaque type de rapport permet de partager des données de performance avec les parties prenantes et d'indiquer si l'intégrité et les performances globales du système s'améliorent ou empirent.

Les définitions des rapports sont stockées dans la base de données de tests de charge. Une fois un rapport enregistré, sa définition est enregistrée dans la base de données et peut être réutilisée par la suite.

Le classeur Excel peut être partagé avec les parties prenantes sans que ceux-ci aient à se connecter à la base de données pour consulter le rapport.

> [!NOTE]
> Vous pouvez partager le classeur Excel. Cependant, seuls les utilisateurs ayant installé Visual Studio sur leur ordinateur peuvent modifier les feuilles de calcul. Les autres utilisateurs ne verront pas l’option **Rapport de test de charge** dans le ruban **Office**, mais ils pourront afficher le classeur.

L'illustration suivante est un exemple de rapport qui affiche une corrélation entre une baisse de vitesse de la transaction (Mettre à jour le panier) et la dégénération du compteur (% processeur). Cela indique un problème potentiel dans le code de l'application, au lieu de la base de données ou du réseau, et présente un bon exemple à diagnostiquer à l'aide du profileur ASP.NET.

![Problème potentiel dans le code de l'application](../test/media/lt_excel.png)

Vous pouvez générer des rapports Excel dans **l’Analyseur de test de charge**, à l’aide du bouton **Créer un rapport Excel** de la barre d’outils, ou à partir d’Excel par le biais de l’option **Rapport de test de charge** sous l’onglet **Test de charge** du ruban **Office**.

> [!NOTE]
> Si vous ajoutez des commentaires à un test de charge, ils apparaissent dans le rapport Excel.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Pour créer des rapports de comparaison de tests de charge à l'aide d'Excel

1. Avant de créer un rapport, vous devez exécuter un test de charge.

2. Vous pouvez créer les rapports de tests de charge Excel de deux façons :

   - Une fois un test de charge terminé, dans la page **Résultats du test de charge**, choisissez le bouton **Créer un rapport Excel** dans la barre d’outils.

      > [!NOTE]
      > Si le bouton **Créer un rapport Excel** est désactivé dans la barre d’outils de l’**Afficheur des résultats des tests de performances web**, vous devrez peut-être exécuter Microsoft Excel une première fois pour l’activer. Quand Visual Studio Enterprise est installé, le complément de test de charge de Visual Studio Enterprise est copié vers votre ordinateur pour Microsoft Excel ; toutefois, Microsoft Excel doit être exécuté pour terminer le processus d'installation du complément.

      Microsoft Excel s’ouvre avec **l’Assistant Générer un rapport de test de charge**.

   **OU**

   1. Ouvrez Microsoft Excel, sélectionnez l’onglet **Test de charge** dans le ruban **Office**, puis choisissez **Rapport de test de charge**.

       **L’Assistant Générer un rapport de test de charge** s’affiche.

   2. Dans la page **Sélectionner la base de données contenant les tests de charge**, sous **Nom du serveur**, tapez le nom du serveur contenant les résultats du test de charge.

   3. Dans la liste déroulante **Nom de la base de données**, sélectionnez la base de données qui contient les résultats du test de charge.

3. Dans la page **Comment voulez-vous générer votre rapport ?** , vérifiez que **Créer un rapport** est sélectionné et choisissez **Suivant**.

4. Dans la page **Quel type de rapport voulez-vous générer ?** , vérifiez que **Exécuter la comparaison** est sélectionné et choisissez **Suivant**.

5. Dans la page **Entrer le détail du rapport de test de charge**, attribuez un nom à votre rapport dans **Nom du rapport**.

6. Sélectionnez le test de charge dont vous souhaitez créer le rapport, puis sélectionnez **Suivant**.

7. Dans la page **Sélectionner les séries pour votre rapport**, sous **Sélectionner une ou plusieurs séries à ajouter à ce rapport**, sélectionnez deux résultats de test de charge que vous souhaitez comparer dans le rapport et cliquez sur **Suivant**.

   > [!NOTE]
   > Vous ne pouvez créer un rapport de comparaison que sur la base de deux résultats de test de charge. Si vous sélectionnez un seul résultat de test de charge ou plus de deux résultats de test de charge, un message d'avertissement s'affiche.

8. Dans la page **Sélectionner les compteurs pour votre rapport**, sous **Sélectionner un ou plusieurs compteurs à ajouter à ce rapport**, vous disposez d’une liste de compteurs pouvant être développée pour personnaliser votre rapport. Sélectionnez les compteurs à partir desquels vous souhaitez comparer les deux séries de tests sélectionnées dans le rapport et cliquez sur **Terminer**.

9. Le rapport du classeur Excel est créé avec les onglets de feuille de calcul suivants :

   - **Table des matières** - Affiche le nom du rapport du test de charge et propose une table des matières comportant des liens vers les différents onglets du rapport.

   - **Séries** - Donne des détails sur les deux séries comparées dans le rapport.

   - **Comparaison de tests** - Donne des détails sous forme d’histogramme sur les améliorations et les régressions des performances entre les deux séries faisant l’objet d’une comparaison.

   - **Comparaison de pages** - Propose des données de comparaison de performances sous forme d’histogramme et de pourcentage entre les deux séries sur les différentes pages figurant dans les séries de tests.

   - **Comparaison d’ordinateurs** - Propose des données de comparaison entre les deux séries sur la base des ordinateurs utilisés.

   - **Comparaison d’erreurs** - Compare les types d’erreurs rencontrés entre les deux séries et indique le nombre d’occurrences.

     > [!TIP]
     > Pour optimiser les rapports, plusieurs propriétés sont disponibles dans les tests de charge et tests des performances web. La demande de page comporte deux propriétés qui sont présentées dans les rapports : Objectif et nom du rapport. Le temps de réponse de la page est comparé à l'objectif et le nom du rapport est utilisé à la place de l'URL dans les rapports. Dans les Paramètres de série de tests de charge, sous Gérer les ensembles de compteurs, la propriété Étiquettes d’ordinateur est présentée dans le nom des ordinateurs figurant dans les rapports. Cela s'avère très utile pour décrire le rôle d'un ordinateur particulier dans le rapport.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Pour créer des rapports de tendance de tests de charge à l'aide d'Excel

1. Avant de créer un rapport, vous devez exécuter un test de charge.

2. Vous pouvez créer les rapports de tests de charge Excel de deux façons :

   - Une fois un test de charge terminé, dans la page **Résultats du test de charge**, choisissez le bouton **Créer un rapport Excel** dans la barre d’outils.

      > [!NOTE]
      > Si le bouton **Créer un rapport Excel** est désactivé dans la barre d’outils de l’**Afficheur des résultats des tests de performances web**, vous devrez peut-être exécuter Microsoft Excel une première fois pour l’activer. Quand Visual Studio Enterprise est installé, le complément de test de charge de Visual Studio Enterprise est copié vers votre ordinateur pour Microsoft Excel ; toutefois, Microsoft Excel doit être exécuté pour terminer le processus d'installation du complément.

      Microsoft Excel s’ouvre avec **l’Assistant Générer un rapport de test de charge**.

   **OU**

   1. Ouvrez Microsoft Excel, sélectionnez l’onglet **Test de charge** dans le ruban **Office**, puis choisissez **Rapport de test de charge**.

       **L’Assistant Générer un rapport de test de charge** s’affiche.

   2. Dans la page **Sélectionner la base de données contenant les tests de charge**, sous **Nom du serveur**, tapez le nom du serveur contenant les résultats du test de charge.

   3. Dans la liste déroulante **Nom de la base de données**, sélectionnez la base de données qui contient les résultats du test de charge.

3. Dans la page **Comment voulez-vous générer votre rapport ?** , vérifiez que **Créer un rapport** est sélectionné et choisissez **Suivant**.

4. Dans la page **Quel type de rapport voulez-vous générer ?** , vérifiez que **Tendance** est sélectionné et choisissez **Suivant**.

5. Dans la page **Entrer le détail du rapport de test de charge**, attribuez un nom à votre rapport dans **Nom du rapport**.

6. Sélectionnez le test de charge dont vous souhaitez créer le rapport, puis sélectionnez **Suivant**.

7. Dans la page **Sélectionner les séries pour votre rapport**, sous **Sélectionner une ou plusieurs séries à ajouter à ce rapport**, sélectionnez deux résultats de test de charge que vous souhaitez comparer dans le rapport et choisissez **Suivant**.

8. Dans la page **Sélectionner les compteurs pour votre rapport**, sous **Sélectionner un ou plusieurs compteurs à ajouter à ce rapport**, vous disposez d’une liste de compteurs pouvant être développée pour personnaliser votre rapport. Sélectionnez les compteurs que vous souhaitez comparer en vue d’effectuer une analyse de tendances et choisissez **Terminer**.

9. Le rapport est créé avec une table des matières qui propose des liens vers les différents onglets du classeur Excel générés dans le rapport. Les liens reposent sur les compteurs sélectionnés pour le rapport de tendance. Par exemple, si vous avez laissé les compteurs par défaut sélectionnés au cours de l'étape 7, le rapport générera alors des données présentées dans des onglets séparés dans Excel, pour chaque compteur répertorié au cours de l'étape 7. Les données générées pour chaque compteur sont présentées sous forme de graphiques tendanciels.

   > [!TIP]
   > Pour optimiser les rapports, plusieurs propriétés sont disponibles dans les tests de charge et tests des performances web. La demande de page comporte deux propriétés qui sont présentées dans les rapports : Objectif et nom du rapport. Le temps de réponse de la page est comparé à l'objectif et le nom du rapport est utilisé à la place de l'URL dans les rapports. Dans les Paramètres de série de tests de charge, sous Gérer les ensembles de compteurs, la propriété Étiquettes d’ordinateur est présentée dans le nom des ordinateurs figurant dans les rapports. Cela s'avère très utile pour décrire le rôle d'un ordinateur particulier dans le rapport.

## <a name="net-security"></a>Sécurité .NET

Les rapports et les résultats des tests de charge peuvent contenir des informations très sensibles qui pourraient être utilisées pour lancer une attaque contre votre ordinateur ou votre réseau. Les rapports et les résultats des tests de charge contiennent le nom des ordinateurs et les chaînes de connexion. Vous devez être conscient de ce risque lorsque vous partagez des rapports de tests de charge avec d'autres personnes.

## <a name="see-also"></a>Voir aussi

- [Créer des rapports sur les résultats des tests de charge pour les comparaisons de tests ou l’analyse des tendances](../test/compare-load-test-results.md)