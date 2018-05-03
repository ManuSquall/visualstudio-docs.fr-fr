---
title: Charge de travail Applications de science et analyse des données
description: La charge de travail Visual Studio regroupe Python, R et F#, et les distributions de leur runtime respectif, y compris Anaconda.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: ecbd5d1fce685243d889b39017efed24ca4492a0
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="install-data-science-support-in-visual-studio"></a>Installer la prise en charge de la science des données dans Visual Studio

La charge de travail Applications de science et analyse des données, que vous sélectionnez et installez via le programme d’installation de Visual Studio, regroupe trois langages et les distributions de leur runtime respectif :

- [R et Microsoft R Client](../rtvs/index.md)
- [Python et Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F# avec le .NET Framework](/dotnet/fsharp/)

![Charge de travail Applications de science et analyse des données dans le programme d’installation de Visual Studio](media/data-science-workload.png)

R et Python sont deux des principaux langages de script utilisés pour la science des données. Ces deux langages sont faciles à apprendre et sont pris en charge par un écosystème étendu de packages. Ces packages permettent de répondre aux besoins de nombreux scénarios, comme l’acquisition de données, le nettoyage, l’apprentissage de modèle, le déploiement et le traçage. F# est également un puissant langage .NET fonctionnel qui convient pour effectuer une grande variété de tâches de traitement des données.

<!--Note link on the image because this one is large -->
[![Captures d’écran de Visual Studio avec R, Python et F #](media/data-science-workload-screens.png)](media/data-science-workload-screens.png)

## <a name="workload-options"></a>Options de la charge de travail

Par défaut, la charge de travail installe les options suivantes, que vous pouvez modifier dans la section Résumé de la charge de travail dans le programme d’installation de Visual Studio :

- Prise en charge du langage F#
- Python :
  - Prise en charge du langage Python
  - [Anaconda3 64 bits](https://www.continuum.io) (une distribution de Python qui inclut des bibliothèques étendues de science des données et un interpréteur Python)
  - Prise en charge de Python web
  - Prise en charge des modèles Cookiecutter
- R :
  - Prise en charge du langage R
  - Prise en charge du runtime pour les outils de développement R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (interpréteur R de Microsoft entièrement compatible, supporté par une communauté, avec des bibliothèques ScaleR permettant un calcul plus rapide sur des nœuds individuels ou des clusters. Vous pouvez également utiliser n’importe quelle implémentation de R du réseau [CRAN](https://cran.r-project.org/).)

Même si F# est fourni avec plusieurs autres charges de travail et que Python a sa propre charge de travail, Applications de science et analyse des données est actuellement la seule charge de travail à inclure R. Cela dit, vous pouvez aussi installer R indépendamment de la charge de travail. Sous l’onglet **Composants individuels** du programme d’installation, sélectionnez les options R suivantes :

- **Activités de développement > Prise en charge du langage R**
- **Activités de développement > Microsoft R Client**
- **Compilateurs, outils de génération et runtimes > Prise en charge du runtime pour les outils de développement R**

## <a name="sql-server-integration"></a>Intégration de SQL Server

SQL Server prend en charge l’utilisation de R et de Python pour effectuer de l’analytique avancée directement dans SQL Server. La prise en charge de R est incluse avec SQL Server 2016 et ultérieur ; la prise en charge de Python est disponible dans SQL Server 2017 CTP 2.0 et ultérieur.

Vous profitez des avantages suivants en exécutant votre code là où sont déjà vos données :

- **Élimination des déplacements des données** : au lieu de déplacer les données depuis la base de données vers votre application ou votre modèle, vous pouvez générer des applications R et Python dans la base de données. Cette fonctionnalité élimine les barrières en matière de sécurité, de conformité, de gouvernance, d’intégrité et de nombreux problèmes similaires liés au déplacement de quantités importantes de données. Vous pouvez aussi consommer des jeux de données qui ne tiendraient pas dans la mémoire d’un ordinateur client.

- **Déploiement facile** : une fois que votre modèle R ou Python est prêt, son déploiement en production consiste juste à l’incorporer dans un script T-SQL. Toute application cliente SQL écrite dans n’importe quel langage peut alors tirer parti des modèles et de l’analyse décisionnelle via un appel de procédure stockée. Aucune intégration spécifique de R ou de Python n’est nécessaire.

- **Performances et scalabilité de niveau entreprise** : vous pouvez utiliser des fonctionnalités avancées de SQL Server, comme les tables en mémoire et les index columnstore, avec des API évolutives à hautes performances dans les packages RevoScaleR et RevoScalePy. L’élimination du déplacement des données signifie également que vous évitez les contraintes de mémoire des clients quand la taille de vos données augmente ou quand vous voulez accroître les performances de l’application.

- **Extensibilité enrichie** : vous pouvez installer et exécuter les derniers packages R ou Python open source dans SQL Server pour créer des applications d’apprentissage long et d’intelligence artificielle sur de très grandes quantités de données dans SQL Server. L’installation d’un package dans SQL Server est aussi simple que l’installation d’un package sur votre ordinateur local.

- **Disponibilité élevée sans coût supplémentaire** : les intégrations de R et de Python sont disponibles dans toutes les éditions de SQL Server 2017 et ultérieur, y compris l’édition Express. (La prise en charge de R est disponible dans SQL Server 2016 et ultérieur.)

Pour tirer pleinement parti de l’intégration de SQL Server, utilisez le programme d’installation de Visual Studio pour installer la charge de travail **Stockage et traitement des données** avec l’option **SQL Server Data Tools**. Cette option active SQL IntelliSense, la mise en surbrillance de la syntaxe et le déploiement.

![Charge de travail Stockage et traitement des données](media/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Options de la charge de travail Stockage et traitement des données](media/data-storage-workload-options.png)

Pour plus d'informations :

- [Utilisation de SQL Server et de R](../rtvs/sql-server.md)
- [In-database Advanced Analytics with R in SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
- [Python in SQL Server 2017: enhanced in-database machine learning (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Services et SDK supplémentaires

En plus de ce qui se trouve directement dans la charge de travail Applications de science et analyse des données, le service Azure Notebooks et le SDK Azure pour Python sont également très utiles pour la science des données.

Le kit SDK Azure pour Python facilite l’utilisation et la gestion des services Microsoft Azure à partir d’applications fonctionnant sur Windows, Mac et Linux. Pour plus d’informations, consultez [SDK Azure pour Python](../python/azure-sdk-for-python.md)

Azure Notebooks (actuellement en préversion) fournit un accès en ligne gratuit aux notebooks Jupyter qui s’exécutent dans le cloud sur Microsoft Azure. Le service inclut des exemples de notebooks en Python, R et F# pour vous aider à démarrer. Visitez [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Captures d’écran d’Azure Notebooks avec l’exemple d’introduction à R](media/data-science-workload-notebooks.png)](media/data-science-workload-notebooks.png)