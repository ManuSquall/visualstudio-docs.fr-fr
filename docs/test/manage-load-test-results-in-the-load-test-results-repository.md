---
title: Gérer les résultats des tests de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6b24fcc485462b8d67ae88104c1ee3ed156e747
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652934"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Gérer des résultats de tests de charge dans le référentiel des résultats des tests de charge

Quand vous exécutez vos tests de charge, toutes les informations collectées pendant une série de tests de charge peuvent être stockées dans le *référentiel des résultats des tests de charge*, qui est une base de données SQL. Le référentiel des résultats des tests de charge contient des données de compteurs de performance et des informations relatives aux erreurs enregistrées. La base de données du référentiel des résultats est créée par le programme d'installation pour les contrôleurs ou créée automatiquement lors de la première série locale d'un test de charge. Pour une série locale, la base de données sera créée automatiquement si le schéma de test de charge n'est pas présent.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Si vous modifiez la chaîne de connexion du référentiel des résultats du contrôleur de façon à utiliser un autre serveur, le nouveau serveur doit exécuter le script *loadtestresultsrepository.sql* pour créer le schéma.

Visual Studio Enterprise fournit des ensembles de compteurs nommés qui recueillent des compteurs de performance courants en fonction d'une technologie. Ces ensembles sont utiles lorsque vous analysez un serveur IIS, un serveur ASP.NET ou un serveur SQL. Toutes les données recueillies avec les ensembles de compteurs sont stockées dans le référentiel des résultats des tests de charge.

> [!IMPORTANT]
> Il existe une différence entre un ensemble de compteurs et les données de compteurs de performance. Un ensemble de compteurs est composé de métadonnées. Il définit un groupe de compteurs de performance qui doivent être recueillis à partir d'un ordinateur qui exécute un rôle particulier, tel qu'un serveur IIS ou SQL Server. L'ensemble de compteurs fait partie de la définition de test de charge. Les données de compteurs de performance sont recueillies en fonction des ensembles de compteurs, du mappage de l'ensemble de compteurs à un ordinateur spécifique et du taux d'échantillonnage.

## <a name="sql-server-versions"></a>Versions de SQL Server

Pour utiliser des tests de charge, vous pouvez utiliser SQL Server Express LocalDB qui est installé avec Visual Studio. Il s’agit du serveur de base de données par défaut pour les tests de charge (notamment l’intégration à Microsoft Excel). SQL Server Express LocalDB est un mode d'exécution de SQL Server Express qui s'adresse aux développeurs de programme. L'installation de SQL Server Express LocalDB copie un ensemble minimal de fichiers nécessaires pour démarrer le moteur de base de données SQL Server.

Si votre équipe prévoit des besoins importants en base de données ou que vos projets sont trop volumineux pour SQL Server Express LocalDB, vous devez envisager une mise à niveau vers SQL Express ou SQL Server édition complète pour bénéficier d’un potentiel de mise à l’échelle supplémentaire. Si vous mettez à niveau SQL Server, les fichiers MDF et LDF pour SQL Server Express LocalDB sont stockés dans le dossier du profil utilisateur. Ces fichiers peuvent être utilisés pour importer la base de données de test de charge vers SQL Server Express ou SQL Server.

## <a name="load-test-results-store-considerations"></a>Considérations relatives au magasin des résultats des tests de charge

Quand Visual Studio Enterprise est installé, le magasin des résultats de test de charge est configuré pour utiliser une instance de SQL Express installée sur l’ordinateur. SQL Express est limité à l'utilisation d'une capacité d'espace disque maximum de 4 Go. Si vous exécutez de nombreux tests de charge sur une longue période, vous devez envisager de configurer le magasin des résultats de test de charge pour utiliser une instance du produit SQL Server complet si disponible.

## <a name="load-test-analyzer-tasks"></a>Tâches de l’Analyseur de test de charge

|Tâches|Rubriques associées|
|-|-----------------------|
|**Configurer un référentiel des résultats des tests de charge :** Vous pouvez configurer un référentiel des résultats des tests de charge sur une base de données SQL. **Remarque :** Un référentiel de test de charge peut également être créé quand vous installez un contrôleur de test. Pour plus d’informations, consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).||
|**Sélection et affichage d’un référentiel de résultats :** Vous pouvez sélectionner un référentiel de résultats spécifique. Vous n'êtes pas limité à un magasin de résultats local. Souvent, les tests de charge sont exécutés sur un jeu distant d'ordinateurs agents. Vous pouvez enregistrer les résultats des tests de vos agents ou de votre ordinateur local sur un serveur SQL sur lequel vous avez créé un magasin de résultats de tests de charge. Dans les deux cas, vous devez identifier l’emplacement où stocker les résultats de votre test de charge à l’aide de la fenêtre **Administrer les contrôleurs de test**.|-   [Guide pratique pour sélectionner un référentiel de résultats de tests de charge](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Guide pratique pour accéder aux résultats des tests de charge à des fins d’analyse](../test/how-to-access-load-test-results-for-analysis.md)|
|**Suppression un résultat des tests de charge d’un référentiel :** Vous pouvez supprimer un résultat de test de charge à partir de **l’éditeur de test de charge**, à l’aide de la boîte de dialogue **Ouvrir et gérer des résultats des tests de charge**.|-   [Guide pratique pour supprimer les résultats d’un test de charge d’un référentiel](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Importer et exporter des résultats dans un référentiel :** Vous pouvez importer et exporter des résultats de test de charge à partir de **l’éditeur de test de charge**.|-   [Guide pratique pour importer les résultats d’un test de charge dans un référentiel](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Guide pratique pour exporter les résultats des tests de charge à partir d’un référentiel](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>Tâches connexes

[Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

Vous pouvez afficher les résultats à la fois d’un test de charge en cours d’exécution et d’un test de charge terminé à l’aide de **l’Analyseur de test de charge**.

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Guide pratique pour accéder aux résultats des tests de charge à des fins d’analyse](../test/how-to-access-load-test-results-for-analysis.md)