---
title: Analyse des résultats et des erreurs des tests de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.pageresult
- vs.test.load.dialog.column
- vs.test.load.monitor.requestresult
- vs.test.load.monitor.testresult
- vs.test.load.monitor.table.view
- vs.test.load.monitor.agentresult
- vs.test.load.monitor.transactionresult
helpviewer_keywords:
- tables, Load Test Viewer options
- load test results, tables
- load tests, Load Test Viewer
- data [Visual Studio ALM], load test tables
- Load Test Viewer, tables
- load tests, results tables
ms.assetid: 0a84bda3-6051-45eb-9c7f-d57419e1f97d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 1b111aad6da99f54edfe8dc4fd4b63ff7a495f34
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179659"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Analyser les résultats et les erreurs des tests de charge dans la vue Tables de l’analyseur de test de charge

Lorsque vous consultez les résultats d'une série de tests de charge, vous pouvez afficher différents volets vous permettant d'analyser les données de différentes manières. Vous pouvez afficher les données sous forme de graphique pour voir comment elles évoluent dans le temps ou les consulter dans des tables détaillées.

Pour basculer en mode table, choisissez **Tables** dans la barre d’outils de **test de charge**. Pour passer d’une table à une autre, utilisez la liste déroulante **Table** accessible dans la barre d’outils située au-dessus de la grille des tables. En mode table, vous pouvez consulter jusqu'à quatre tables à la fois. Pour plus d’informations, consultez [Disposer en mosaïque les tables de tests de charge](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) dans cette rubrique.

La plupart des valeurs numériques affichées dans une table pour les compteurs de performance sont cumulatives sur l'ensemble de la série de tests de charge. Les colonnes nommées **Dernièrement** sont une exception et représentent la valeur de l’intervalle d’échantillonnage le plus récent.

> [!NOTE]
> Les colonnes nommées **Dernièrement** ne sont disponibles qu’au cours de l’exécution d’un test de charge. Une fois qu'un test de charge est terminé, ces colonnes ne sont plus disponibles.

 Vous pouvez trier la plupart des tables en choisissant le titre de la colonne sur laquelle vous souhaitez effectuer le tri. Par défaut, certaines tables n'affichent pas toutes les colonnes disponibles. Vous pouvez ajouter des colonnes aux tables, si des colonnes sont disponibles. Pour ajouter des colonnes, cliquez avec le bouton droit sur la table, puis choisissez **Ajouter/Supprimer des colonnes**.

> [!NOTE]
> Vous pouvez copier les données d'une table dans d'autres applications telles qu'Excel, à des fins d'analyse supplémentaire.

## <a name="the-load-test-tables"></a>Tables de tests de charge

 Le tableau suivant répertorie les tables disponibles pour analyser des séries de tests de charge.

|Nom de la table|Description|
|----------------|-----------------|
|Erreurs|Affiche une liste des erreurs qui se sont produites pendant la série de tests de charge. Pour plus d’informations, consultez [Table Erreurs](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) dans cette rubrique, et [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|
|Pages|Affiche une liste de pages consultées pendant une série de tests de charge. Certaines données de cette table ne sont disponibles qu'à l'issue d'un test de charge. Pour plus d’informations, consultez [Guide pratique pour afficher la réponse d’une page web](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|Requêtes|Affiche des détails relatifs aux demandes émises pendant un test de charge. Cela inclut toutes les demandes HTTP et les demandes dépendantes, telles que les images. Pour plus d’informations, consultez [Table Requêtes](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) dans cette rubrique.|
|Trace SQL|Affiche les résultats du traçage SQL. Cette table n'est disponible qu'à l'issue d'un test de charge et uniquement si le traçage SQL a été utilisé pendant le test. Pour plus d’informations, consultez [Table Données de trace SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) dans cette rubrique.|
|Tests|Affiche des détails relatifs aux tests exécutés pendant un test de charge. Pour plus d’informations, consultez [Table Tests](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) dans cette rubrique.|
|Seuils|Affiche une liste des violations de règles de seuil qui se sont produites pendant la série de tests de charge. Pour plus d’informations, consultez [Analyse des violations des règles de seuil](../test/analyze-threshold-rule-violations-in-load-tests.md).|
|Transactions|Affiche une liste des transactions qui se sont produites pendant une série de tests de charge. Pour plus d’informations, consultez [Table Transactions](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) dans cette rubrique.|
|Agents|S’affiche uniquement si votre test de charge utilise un contrôleur de test et des agents de test. Affiche une liste des agents utilisés pendant la série de tests de charge. Le tableau Agents indique le nombre de requêtes testées par l'agent et, parmi ces requêtes, le nombre d'échecs. En outre, le tableau Agents indique le nombre de tests que l'agent a effectués dans la combinaison de tests pour le test de charge et le nombre d'échecs.|
|Détails du test|Affiche des détails des tests inclus dans la combinaison de tests pour le test de charge. Les détails incluent le nom du test, le scénario du test, l'heure de démarrage du test, la durée d'exécution du test et le résultat de test qui indique si le test a réussi ou a échoué. En cas d’échec du test, un lien est fourni dans la colonne **Détails**. Vous pouvez cliquer sur le lien pour accéder à l'éditeur de test de performances Web avec la requête ayant échoué en surbrillance.|

## <a name="collect-percentile-data"></a>Collecter les données de centile

 Certaines tables de tests de charge peuvent contenir des colonnes supplémentaires, incluant des données de centile et des temps de réponse répartis dans des groupes selon l'émulation du réseau. Par défaut, ces données ne sont pas collectées. Les données de centile ne seront disponibles que si vous avez enregistré les résultats dans une base de données, et non localement. Pour plus d’informations, consultez [Gestion des résultats des tests de charge dans le dépôt des résultats de tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md). En outre, pour collecter ces données, dans **l’éditeur de test de charge**, sous le nœud **Paramètres d’exécution**, sélectionnez le nœud Paramètre d’exécution à modifier. Dans la fenêtre **Propriétés**, pour la propriété **Stockage des détails de minuterie**, sélectionnez **StatisticsOnly** ou **AllIndividualDetails**. Pour plus d’informations, consultez [Guide pratique pour afficher la réponse d’une page web](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>Table Requêtes

 La table **Requêtes** affiche des détails relatifs aux requêtes émises pendant un test de charge. Cela inclut toutes les demandes HTTP et les demandes dépendantes, telles que les images. La table répertorie les demandes par test et scénario, parce qu'une demande peut être incluse dans de nombreux tests et scénarios.

 Le tableau suivant répertorie les colonnes de la table **Requêtes** :

|Colonne|Description|Visible par défaut|
|------------|-----------------|------------------------|
|**Requête**|URL de la requête. Par exemple, *home.html* ou *orange-arrow.gif*.|Oui|
|**Scénario**|Nom du scénario.|Oui|
|**Test**|Nom du test.|Oui|
|**Total**|Nombre total de demandes de tests de performances web émises pendant la série de tests de charge. Il comprend les demandes ayant abouti ou échoué, mais pas les demandes mises en cache, car elles ne sont pas adressées au serveur web.|Oui|
|**Réussite**|Nombre de fois où la demande a été émise et a réussi.|Non|
|**Échec**|Nombre de fois où la demande a été émise et a échoué. Les entrées de cette colonne apparaissent sous forme de liens hypertexte. Vous pouvez cliquer sur un lien hypertexte pour afficher la liste des erreurs dans la boîte de dialogue **Erreurs du test de charge**. Pour plus d’informations, consultez [Analyser les résultats de test de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Oui|
|**Mis en cache**|Nombre total de fois où la demande a déjà été mise en cache.|Non|
|**Requêtes/s**|Taux par seconde de la demande pendant la série de tests de charge.|Non|
|**Réussite/s**|Taux par seconde de cette demande pendant la série de tests de charge, pour les instances de cette demande qui ont réussi.|Non|
|**Échecs/s**|Taux par seconde de cette demande pendant la série de tests de charge, pour les instances de cette demande qui ont échoué.|Non|
|**Temps du premier octet**|Délai moyen avant de recevoir le premier octet de la réponse, mesuré à partir du moment où la demande a été envoyée au serveur web. Les unités sont les secondes.|Non|
|**Temps de réponse**|Délai moyen avant de recevoir la totalité de la réponse à une demande, mesuré à partir du moment où la demande a été envoyée au serveur web. Les unités sont les secondes.|Oui|
|**Longueur du contenu**|Longueur moyenne du contenu de la réponse à la demande. Les unités sont les octets.|Oui|

## <a name="the-tests-table"></a>Table Tests

 La table **Tests** affiche des détails relatifs aux tests exécutés pendant un test de charge. La table répertorie les tests par test et scénario, parce qu'un test peut être inclus dans de nombreux scénarios.

 Le tableau suivant répertorie les colonnes de la table **Tests**.

|Colonne|Description|Visible par défaut|
|------------|-----------------|------------------------|
|**Test**|Nom du test.|Oui|
|**Scénario**|Nom du scénario.|Oui|
|**Total**|Nombre total de fois où le test a été exécuté dans le scénario. Cela inclut le nombre de fois où le test a réussi et échoué.|Oui|
|**Réussite**|Nombre de fois où le test a été exécuté dans le scénario et a réussi.|Oui|
|**Échec**|Nombre de fois où le test a été exécuté dans le scénario et a échoué. Les entrées de cette colonne apparaissent sous forme de liens hypertexte. Vous pouvez cliquer sur un lien hypertexte pour afficher la liste des erreurs dans la boîte de dialogue **Erreurs du test de charge**. Pour plus d’informations, consultez [Analyser les résultats de test de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Oui|
|**Tests/s**|Taux par seconde du test pendant la série de tests de charge.|Oui|
|**Réussite/s**|Taux par seconde de ce test pendant la série de tests de charge, pour les instances de ce test qui ont réussi.|Non|
|**Échecs/s**|Taux par seconde de ce test pendant la série de tests de charge, pour les instances de ce test qui ont échoué.|Non|
|**Durée du test**|Durée moyenne pour exécuter le test pendant la série de tests de charge. Les unités sont les secondes.|Oui|
|**90% de la durée du test**|90e centile pour la durée du test.|Non|
|**95% de la durée du test**|95e centile pour la durée du test.|Oui|
|**Requêtes/test**|Nombre moyen de demandes du test s’il s’agit d’un test de performances web.|Non|

## <a name="the-transactions-table"></a>Table Transactions

 La table **Transactions** affiche une liste des transactions qui se sont produites pendant une série de tests de charge. Les transactions font référence aux transactions définies dans un test de performances web ou aux minuteurs définis dans un test unitaire. Une transaction ne fait pas référence aux transactions de bases de données.

 Le tableau suivant répertorie les colonnes de la table **Transactions**.

> [!NOTE]
> Pour afficher toutes les colonnes, vous devez activer la propriété Stockage des détails de minuterie associée au paramètre d'exécution actif. Pour plus d’informations, consultez [Guide pratique pour spécifier la propriété de stockage des détails de minuterie](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Colonne|Description|Visible sans les détails de minuterie|
|------------|-----------------|------------------------------------|
|**Transaction**|Nom de la transaction.|Oui|
|**Scénario**|Nom du scénario.|Oui|
|**Test**|Nom du test.|Oui|
|**Total**|Nombre total de transactions émises pendant la série de tests de charge.|Oui|
|**Temps de transaction**|Durée d’exécution de la transaction pendant une série de tests de charge. Dans le cas des tests de performances web, le temps de réflexion est compris dans le calcul. Les unités sont les secondes.|Non|
|**Temps de réponse**|Temps de réponse de la transaction de test de performances web dans une série de tests de charge. Le temps de réponse diffère du temps de transaction dans le fait qu’il ne comprend pas le temps de réflexion écoulé durant la transaction. Les unités sont les secondes.|Non|
|**Temps de réponse moyen**|Temps de transaction moyen. Ce temps inclut des temps de réflexion. Par exemple, si vous avez trois requêtes et que chacune présente un temps de réflexion, ce temps comprendra ces temps de réflexion et le temps effectif d'exécution des requêtes.|Non|
|**Temps de réponse moyen**|Temps de réponse moyen d’une transaction de test de performances web dans une série de tests de charge. Le temps de réponse diffère du temps de transaction dans le fait qu’il ne comprend pas le temps de réflexion écoulé durant la transaction. Les unités sont les secondes.|Non|
|**Temps de réponse min**|Cela n'inclut pas les temps de réflexion.|Non|
|**Temps de réponse max**|Cela n'inclut pas les temps de réflexion.|Non|
|**Temps de réponse médian**|Cela n'inclut pas les temps de réflexion.|Non|
|**90% du temps de réponse**|90e centile pour le temps de transaction. Cela n'inclut pas les temps de réflexion. **Remarque :** Ce comportement est différent de Visual Studio Team System 2008 Test Load Agent, qui utilisait la valeur **90% du temps de transaction**.|Non|
|**95% du temps de réponse**|95e centile pour le temps de transaction. Cela n'inclut pas les temps de réflexion. **Remarque :** Ce comportement est différent de Visual Studio Team System 2008 Test Load Agent, qui utilisait la valeur **95% du temps de transaction**.|Non|
|**99% du temps de réponse**|99e centile du temps de transaction. Cela n'inclut pas les temps de réflexion.|Non|
|**Écart type du temps de réponse**|Cela n'inclut pas les temps de réflexion.|Non|

## <a name="the-errors-table"></a>Table Erreurs

 Lorsque vous exécutez un test de charge, vous pouvez analyser les erreurs qui se produisent. L'analyse des erreurs et l'ajustement de vos tests constituent une partie importante du processus de test de charge. En cas d’erreurs, un lien hypertexte **erreurs** apparaît dans la barre d’état du test de charge et spécifie le nombre d’erreurs qui se sont produites. Pour afficher la table d'erreurs, cliquez sur le lien hypertexte.

 La table d'erreurs rassemble les erreurs survenues lors d'un test de charge par type et sous-type d'erreur. La table contient également une ligne **total** qui spécifie le nombre total de toutes les erreurs qui se sont produites.

 La table d'erreurs contient les colonnes suivantes :

|Colonne|Description|Visible par défaut|
|------------|-----------------|------------------------|
|Type|Type de l'erreur. Par exemple, HttpError.|Oui|
|SubType|Sous-type de l'erreur. Par exemple, LoadTestException.|Oui|
|Count|Nombre d'erreurs de ce type survenues lors du test de charge. Les entrées de cette colonne apparaissent sous forme de liens hypertexte. Vous pouvez cliquer sur un lien hypertexte pour afficher la liste des erreurs.|Oui|
|Dernier message|Message qui décrit l'erreur. Par exemple, 404 - Non trouvé.|Oui|

 Pour plus d’informations, consultez [Utilisation de tables de tests de charge](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

### <a name="drill-down-to-the-error-list"></a>Parcourir la liste d’erreurs

La table d'erreurs regroupe les erreurs par type et sous-type d'erreur. Pour consulter une table des erreurs individuelles, vous affichez la boîte de dialogue **Erreurs du test de charge**. Pour afficher la boîte de dialogue, cliquez sur un lien hypertexte dans la colonne **Nombre** de la table d’erreurs. Vous pouvez également cliquer avec le bouton droit sur une ligne de la table d’erreurs qui est remplie, puis choisir **Erreurs**.

> [!NOTE]
> Seules les 1000 premières instances de combinaisons de types et sous-types d'erreurs sont recueillies. Quand vous affichez la boîte de dialogue **Erreurs du test de charge**, vous consulterez, au plus, les 1 000 premières instances d’erreurs.

La table **Erreurs du test de charge** contient les colonnes suivantes :

|Colonne|Description|
|------------|-----------------|
|**Heure**|Heure à laquelle l'erreur s'est produite lors du test de charge.|
|**Agent**|Nom de l'ordinateur agent sur lequel l'erreur s'est produite. C’est important lorsque vous exécutez des tests de charge à l’aide de contrôleurs de test et des agents de test. Pour plus d’informations, consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).|
|**Test**|Nom du test de performances web dans lequel l’erreur s’est produite.|
|**Scénario**|Nom du scénario dans lequel l'erreur s'est produite.|
|**Requête**|URL de la requête dans laquelle l'erreur s'est produite.|
|**Type**|Type de l'erreur. Par exemple, HttpError.|
|**Sous-type**|Sous-type de l'erreur. Par exemple, LoadTestException.|
|**Text**|Texte du message d'erreur. Par exemple, 404 - Non trouvé.|
|**Pile**|Les entrées de cette colonne sont vides, ou contiennent le mot **Pile** sous la forme d’un lien hypertexte. Vous pouvez cliquer sur le lien hypertexte pour afficher une trace de la pile de l'erreur.|
|**Détails**|Les entrées de cette colonne sont vides, ou contiennent le mot **TestLog** sous la forme d’un lien hypertexte. Ce lien peut vous aider à isoler des erreurs dans le test de charge. Par exemple, le lien **TestLog** d’une erreur de demande du test de performances web permet d’afficher les résultats du test dans l’Afficheur de résultats de test de performances web et de mettre l’erreur en surbrillance.|

> [!NOTE]
> Vous pouvez trier la table en choisissant les en-têtes de colonne.

## <a name="the-sql-trace-data-table"></a>Table de données Trace SQL

Vous pouvez collecter les données de trace SQL pendant une série de tests de charge pour les analyser ultérieurement. La collecte de données de trace vous permet d'identifier les procédures stockées et les requêtes qui s'exécutent le plus lentement dans la base de données SQL Server testée.

Si le traçage SQL est activé, un fichier contenant les données de trace SQL est créé pendant la série de tests de charge. Ces données sont enregistrées automatiquement dans le magasin des résultats des tests de charge à l'issue de la série de tests et le fichier de trace est supprimé. Vous pouvez analyser les données de trace dans le tableau **Trace SQL** à la fin du test de charge.

### <a name="to-view-sql-trace-data"></a>Pour voir des données de trace SQL

1. Dans l’analyseur de test de charge, choisissez **Tables** dans la barre d’outils pour vérifier que la grille des tables est affichée.

2. Dans la zone de liste déroulante **Table**, sélectionnez **Trace SQL**.

3. Les données de trace qui ont été collectées pendant la série de tests sont affichées dans la grille. La table répertorie les opérations SQL exécutées le plus lentement, triées par durée, en commençant par la plus lente. En général, la colonne **Durée** est la première colonne à examiner. Les données sont indiquées millisecondes.

   Les colonnes affichées sont les suivantes :

    - **Event, classe**

    - **Durée**

    - **Processeur**

    - **Lectures**

    - **Écritures**

    - **TextData**

    - **StartTime**

    - **EndTime**

   Pour effectuer le traçage d'événements SQL autres que les données identifiées dans ces colonnes, vous pouvez configurer votre propre traçage SQL personnalisé à l'aide de l'outil Générateur de profils SQL, distinct de Visual Studio.

## <a name="tile-load-test-tables"></a>Disposer en mosaïque les tables de tests de charge

Lorsque vous consultez les résultats d'une série de tests de charge, vous pouvez afficher les données sous la forme de tables détaillées. Pour basculer en mode table, choisissez **Tables** dans la barre d’outils de **test de charge**. Les tables disponibles sont **Erreurs**, **Pages**, **Requêtes**, **Trace SQL**, **Tests**, **Seuils** et **Transactions**. Pour plus d’informations, consultez [Utilisation de tables de tests de charge](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

Le mode table vous permet de consulter jusqu'à quatre tables à la fois sans qu'elles se chevauchent.

### <a name="to-tile-tables"></a>Pour disposer des tables en mosaïque

1. Dans la barre d’outils de **l’analyseur de test de charge**, choisissez **Tables**.

     L'affichage en table s'ouvre. La disposition par défaut est deux panneaux horizontaux.

2. Dans la barre d’outils de **l’Analyseur de test de charge**, cliquez sur le bouton de **disposition**, puis choisissez l’une des options suivantes :

    - **Un panneau**

    - **Deux panneaux horizontaux**

    - **Trois panneaux horizontaux**

    - **Quatre panneaux horizontaux**

3. Pour passer d’une table à une autre, utilisez, dans chaque panneau, la liste déroulante située au-dessus de la grille des tables.

    > [!NOTE]
    > Vous ne pouvez pas afficher la même table dans plusieurs panneaux. Si vous modifiez la table affichée dans un panneau en une table déjà affichée dans un autre panneau, les tables basculent de panneaux.

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Guide pratique pour accéder aux résultats des tests de charge à des fins d’analyse](../test/how-to-access-load-test-results-for-analysis.md)
- [Analyser les résultats des tests de charge dans la vue Graphiques](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analyser les violations des règles de seuil](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Gérer des résultats des tests de charge dans le référentiel des résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Vue d’ensemble du résumé des résultats des tests de charge](../test/load-test-results-summary-overview.md)