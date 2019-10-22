---
title: Ensembles de compteurs et règles de seuil pour les tests de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- load tests, thresholds
- counter sets
- load tests, performance
- load tests, counter sets
- load tests, threshold rules
ms.assetid: 9e14d955-f3a4-4717-bbfe-7f08cdda5678
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 493295bdbcd1b4906aedf6dca54e264e8ae5e8c6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659951"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Spécifier des ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge

Les tests de charge fournissent des ensembles de compteurs nommés, qui sont utiles lorsque vous analysez des données de compteur de performance. Les ensembles de compteurs sont organisés par technologie et incluent Application, ASP.NET, .NET Application, IIS et SQL. Quand vous créez un test de charge avec **l’Assistant Nouveau test de charge**, vous ajoutez un ensemble initial de compteurs. Ceux-ci vous offrent un groupe d'ensembles de compteurs prédéfinis et importants pour votre test de charge. Vous gérez vos compteurs dans **l’éditeur de test de charge**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Si vos tests de charge sont répartis entre des ordinateurs distants, les compteurs de contrôleur et d'agent sont automatiquement mappés au contrôleur et aux ensembles de compteurs de l'agent. Pour plus d’informations sur l’utilisation d’ordinateurs distants dans votre test de charge, consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

Les ensembles de compteurs sont recueillis sur les ordinateurs que vous spécifiez. L’association entre un ensemble de compteurs et un ordinateur qui est utilisé pendant un test de charge porte le nom de *mappage d’ensemble de compteurs*. Par exemple, le serveur web que vous testez peut avoir des mappages d’ensembles de compteurs ASP.NET, IIS et .NET.

Par défaut, les compteurs de performance sont rassemblés sur le contrôleur et les agents. Pour plus d’informations, consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

Il est important que vous ajoutiez les serveurs sous test à la liste des ordinateurs sur lesquels rassembler des compteurs. De cette manière, toutes les données système importantes sont rassemblées et surveillées pendant le test de charge.

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-|-----------------------|
|**Gérer les ensembles de compteurs pour votre test de charge :** Après avoir créé votre test de charge, vous pouvez modifier l’ensemble de compteurs dans l’éditeur de test de charge. La gestion d'ensembles de compteurs implique le choix du jeu d'ordinateurs à partir duquel vous souhaitez collecter des données de performance et l'assignation d'un jeu d'ensembles de compteurs à collecter à partir de chaque ordinateur individuel. Vous gérez vos compteurs dans l'éditeur de test de charge.|-   [Guide pratique pour gérer des ensembles de compteurs](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Ajouter des ensembles de compteurs à votre test de charge :** quand vous créez un test de charge avec l’**Assistant Nouveau test de charge**, vous ajoutez un ensemble initial de compteurs. Ceux-ci vous offrent un groupe d'ensembles de compteurs prédéfinis pour votre test de charge. Après avoir créé un test de charge, vous pouvez ajouter de nouveaux compteurs aux ensembles de compteurs existants à l'aide de l'éditeur de test de charge.|-   [Guide pratique pour ajouter des compteurs à des ensembles de compteurs](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Guide pratique pour ajouter des ensembles de compteurs personnalisés](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Spécifier une règle de seuil à l’aide de compteurs pour votre test de charge :** Une règle de seuil est une règle définie sur un compteur de performances individuel pour monitorer l’utilisation des ressources système pendant un test de charge. Les définitions d'ensembles de compteurs contiennent des règles de seuil prédéfinies pour de nombreux compteurs de performance clés. Les règles de seuil contenues dans des tests de charge comparent une valeur de compteur de performance à une valeur de constante ou une autre valeur de compteur de performance.|-   [Guide pratique pour ajouter une règle de seuil](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Assigner des noms conviviaux aux ordinateurs auxquels les ensembles de compteurs sont mappés :** Vous pouvez ajouter des balises d’ordinateur qui vous permettent d’appliquer un nom reconnu facilement par un ordinateur. Les balises s’affichent dans le nœud **Mappages des ensembles de compteurs** de l’arborescence dans l’éditeur de test de charge. Plus important, les balises s'affichent dans les rapports Excel qui permettent aux parties prenantes d'identifier le rôle de l'ordinateur dans le test de charge, par exemple, « ServerWeb1 dans lab2 » ou « SQL Server2 dans le bureau de Phoenix ».<br /><br /> Pour plus d’informations, voir [Créer des rapports sur les résultats des tests de charge à des fins de comparaison ou d’analyse des tendances](../test/compare-load-test-results.md).||

## <a name="use-counter-sets"></a>Utiliser des ensembles de compteurs

Les outils de test de charge rassemblent des données de performance et fournissent des graphiques à l'aide des valeurs de compteurs dans le temps. Les données de compteurs sont rassemblées selon des intervalles spécifiés par l'utilisateur pendant une série de tests de charge. Pour plus d’informations, voir [Guide pratique : Spécifier l’échantillonnage](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Vous pouvez afficher les compteurs au moment de l’exécution ou après une série de tests de charge à l’aide de *l’analyseur de test de charge*.

Les données de compteurs sont rassemblées sur le serveur et sur tout ordinateur où un test est exécuté. Si vous avez installé un ensemble d'ordinateurs agents sur lesquels exécuter vos tests, les compteurs sont également rassemblés sur ces ordinateurs.

Il existe trois catégories de compteurs : pourcentages, comptes et moyennes. Le pourcentage d'utilisation du processeur, le nombre de verrous SQL Server et le nombre de demandes IIS par seconde sont des exemples de compteurs.

![Ensembles de compteurs du test de charge](../test/media/loadtestcountersets.png)

Les données de performances pour chaque requête HTTP sont envoyées par l'ordinateur qui exécute un test, comme un ordinateur agent. Pour les demandes, vous pouvez surveiller des données telles que le Temps moyen jusqu'au premier octet, le Temps de réponse et le Nombre moyen de demandes par seconde.

Pour faciliter la collecte des données de performances sur un serveur web, Visual Studio fournit également des ensembles de compteurs prédéfinis et nommés, basés sur la technologie utilisée dans les tests de charge. Ces ensembles sont utiles lorsque vous analysez un serveur qui exécute les services Internet (IIS), ASP.NET ou SQL Server. Les compteurs non fournis dans l'ensemble de compteur par défaut peuvent être ajoutés à l'aide de l'Éditeur de test de charge. Il est important que vous ajoutiez les ordinateurs ou les serveurs à tester à votre test de charge, afin d'être sûr de pouvoir surveiller l'utilisation des ressources sur ces ordinateurs. Pour plus d’informations, consultez [Guide pratique pour gérer les ensembles de compteurs](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

L'analyse des résultats des séries de tests de charge nécessite souvent une connaissance spécifique au domaine d'une zone particulière, afin de déterminer quelles données rassembler, où définir des règles de seuil et comment savoir si une mesure reflète un problème spécifique dans l'application. Pour plus d’informations, consultez [À propos des règles de seuil](#about-threshold-rules).

### <a name="performance-counter-sampling-interval-considerations"></a>Considérations relatives à l’intervalle d’échantillonnage des compteurs de performances

Sélectionnez une valeur appropriée de la propriété **Taux d’échantillonnage** dans les paramètres d’exécution d’un test de charge en fonction de la longueur de votre test de charge. Un taux d'échantillonnage moins élevé, tel que la valeur par défaut de cinq secondes, nécessite une capacité d'espace supplémentaire dans la base de données des résultats du test de charge. Pour les tests de charge de plus longue durée, l'augmentation du taux d'échantillonnage pour permet de réduire le volume de données collectées. Pour plus d’informations, voir [Guide pratique : Spécifier l’échantillonnage](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Voici certaines indications pour les taux d'échantillonnage.

|Durée du test de charge|Taux d'échantillonnage recommandé|
|-|-----------------------------|
|\< 1 heure|5 secondes|
|1 à 8 heures|15 secondes|
|8 à 24 heures|30 secondes|
|> 24 heures|60 secondes|

## <a name="store-performance-data"></a>Stocker les données de performances

Durant une série de tests de charge, les données des compteurs de performances sont collectées et stockées dans le *référentiel des résultats de test de charge*. Pour plus d’informations, voir [Gérer les résultats des tests de charge dans le référentiel des résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>À propos des règles de seuil

Une *règle de seuil* est une règle définie sur un compteur de performances individuel pour monitorer l’utilisation des ressources système pendant un test de charge. Les définitions d'ensembles de compteurs contiennent des règles de seuil prédéfinies pour de nombreux compteurs de performance clés. Pour plus d’informations, consultez [Utiliser des ensembles de compteurs pour analyser les données des compteurs de performances dans les tests de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="threshold-rules-and-levels"></a>Règles de seuil et niveaux

Lorsque vous créez des règles de seuils dans vos tests de charge, vous choisissez entre deux types de règles :

Comparer avec constante&mdash;Comparez une valeur de compteur de performances avec une valeur de constante.

Comparer avec compteurs&mdash;Comparez une valeur de compteur de performances avec une autre valeur de compteur de performances.

Lorsque vous créez des règles de seuil, vous définissez également les niveaux pour la règle. Les niveaux sont le seuil d'avertissement et le seuil critique. Lorsque vous consultez une série de tests de charge, les violations des seuils de niveau d'avertissement sont indiquées par un symbole jaune et les violations des seuils de niveau critique sont indiquées par un symbole rouge.

## <a name="the-alert-if-over-property"></a>Propriété Alerte en cas de dépassement

Affectez la valeur **True** à la propriété **Alerte en cas de dépassement** pour indiquer que le dépassement d’un seuil constitue un problème. Par exemple, si la règle de seuil a la valeur **% Temps processeur** et que vous souhaitez être alerté si la valeur est supérieure à 90, utilisez le type de règle **Comparer avec constante**, affectez la valeur 90 à **Valeur de seuil critique**, puis affectez la valeur **True** à **Alerte en cas de dépassement**.

Affectez la valeur **False** à la propriété **Alerte en cas de dépassement** pour indiquer que le fait d’être sous un seuil constitue un problème. Par exemple, si la règle de seuil a la valeur **Requêtes/s** et que vous souhaitez être alerté si la valeur est inférieure à 50, utilisez le type de règle **Comparer avec constante**, affectez la valeur 50 à **Valeur de seuil critique**, puis affectez la valeur **False** à **Alerte en cas de dépassement**.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour ajouter une règle de seuil](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Analyser les violations des règles de seuil](../test/analyze-threshold-rule-violations-in-load-tests.md)