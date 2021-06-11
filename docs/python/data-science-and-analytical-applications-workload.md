---
title: Charge de travail Applications de science et analyse des données
description: Cette charge de travail Visual Studio regroupe Python, F# et les distributions de leur runtime respectif, Anaconda inclus. (R est inclus dans Visual Studio 2017 uniquement.)
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: 2c12c8a0979ab081ea2f09faeeccdb5a8a9d2175
ms.sourcegitcommit: 398b4d4e5ce0f978720f11990db05b209766aedc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2021
ms.locfileid: "112016305"
---
# <a name="install-data-science-support-in-visual-studio"></a>Installer la prise en charge de la science des données dans Visual Studio

La charge de travail Applications de science et analyse des données, que vous sélectionnez et installez par le biais du programme d’installation de Visual Studio, regroupe plusieurs langages et les distributions de leur runtime respectif :

::: moniker range="vs-2017"
- [Python et Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F# avec .NET Framework](/dotnet/fsharp/)
- [R et Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [F# avec .NET Framework](/dotnet/fsharp/)
::: moniker-end

![Charge de travail Applications de science et analyse des données dans le programme d’installation de Visual Studio](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python et R sont deux des principaux langages de script utilisés pour la science des données. Ces deux langages sont faciles à apprendre et sont pris en charge par un écosystème étendu de packages. Ces packages permettent de répondre aux besoins de nombreux scénarios, comme l’acquisition de données, le nettoyage, l’apprentissage de modèle, le déploiement et le traçage. F# est également un puissant langage .NET fonctionnel qui convient pour effectuer une grande variété de tâches de traitement des données.
::: moniker-end

::: moniker range=">=vs-2019"
Python est l’un des principaux langages de script utilisés pour la science des données. Python est facile à apprendre et est pris en charge par un écosystème étendu de packages. Ces packages permettent de répondre aux besoins de nombreux scénarios, comme l’acquisition de données, le nettoyage, l’apprentissage de modèle, le déploiement et le traçage. F # est également un puissant langage .NET fonctionnel qui est adapté à une grande variété de tâches de traitement des données.)
::: moniker-end

<!--Note link on the image because this one is large -->
[![Captures d’écran de Visual Studio avec R, Python et F#](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Options de la charge de travail

Par défaut, la charge de travail installe les options suivantes, que vous pouvez modifier dans la section Résumé de la charge de travail dans le programme d’installation de Visual Studio :

::: moniker range=">=vs-2019"
- Prise en charge du langage F# pour poste de travail
- Python :
  - Prise en charge du langage Python
  - Prise en charge de Python web
::: moniker-end

::: moniker range="vs-2017"
- Prise en charge du langage F#
- Python :
  - Prise en charge du langage Python
  - [Anaconda3 64-bit](https://www.continuum.io), distribution Python qui comprend de nombreuses bibliothèques de science des données et un interpréteur Python.
  - Prise en charge de Python web
  - Prise en charge des modèles Cookiecutter
- R :
  - Prise en charge du langage R
  - Prise en charge du runtime pour les outils de développement R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (interpréteur R de Microsoft entièrement compatible, supporté par une communauté, avec des bibliothèques ScaleR permettant un calcul plus rapide sur des nœuds individuels ou des clusters. Vous pouvez également utiliser n’importe quelle implémentation de R du réseau [CRAN](https://cran.r-project.org/).)
::: moniker-end

## <a name="sql-server-integration"></a>Intégration de SQL Server

::: moniker range="vs-2017"
SQL Server prend en charge l’utilisation de Python et de R pour effectuer de l’analytique avancée directement dans SQL Server. La prise en charge de R est incluse avec SQL Server 2016 et ultérieur ; la prise en charge de Python est disponible dans SQL Server 2017 CTP 2.0 et ultérieur.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server prend en charge l’utilisation de Python pour effectuer de l’analytique avancée directement dans SQL Server. (La prise en charge de Python est disponible dans SQL Server 2017 CTP 2.0 et ultérieur.)
::: moniker-end

Vous profitez des avantages suivants en exécutant votre code là où sont déjà vos données :

- **Élimination du déplacement des données**: au lieu de déplacer les données de la base de données vers votre application ou modèle, vous pouvez créer des applications dans la base de données. Cette fonctionnalité élimine les barrières en matière de sécurité, de conformité, de gouvernance, d’intégrité et de nombreux problèmes similaires liés au déplacement de quantités importantes de données. Vous pouvez aussi consommer des jeux de données qui ne tiendraient pas dans la mémoire d’un ordinateur client.

- **Déploiement facile**: une fois que vous disposez d’un modèle prêt, le déploiement en production est un simple problème de l’incorporer dans un script T-SQL. Toute application cliente SQL écrite dans n’importe quel langage peut alors tirer parti des modèles et de l’analyse décisionnelle via un appel de procédure stockée. Aucune intégration spécifique au langage n’est nécessaire.

- **Performances et mise à l’échelle de classe entreprise**: vous pouvez utiliser les fonctionnalités avancées de SQL Server telles que les index de table et de stockage de colonnes en mémoire avec les API évolutives hautes performances dans les packages RevoScale. L’élimination du déplacement des données signifie également que vous évitez les contraintes de mémoire des clients quand la taille de vos données augmente ou quand vous voulez accroître les performances de l’application.

- **Extensibilité riche**: vous pouvez installer et exécuter l’un des derniers packages Open source dans SQL Server pour créer des applications d’apprentissage profond et d’intelligence artificielle sur de grandes quantités de données dans SQL Server. L’installation d’un package dans SQL Server est aussi simple que l’installation d’un package sur votre ordinateur local.

- **Grande disponibilité sans coût supplémentaire**: les intégrations de langage sont disponibles dans toutes les éditions de SQL Server 2017 et versions ultérieures, y compris l’édition Express.

Pour tirer pleinement parti de l’intégration de SQL Server, utilisez le programme d’installation de Visual Studio pour installer la charge de travail **Stockage et traitement des données** avec l’option **SQL Server Data Tools**. Cette option active SQL IntelliSense, la mise en surbrillance de la syntaxe et le déploiement.

![Charge de travail de stockage et traitement des données](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Options de la charge de travail Stockage et traitement des données](media/workload/data-storage-workload-options.png)

Pour plus d'informations :

::: moniker range="vs-2017"
- [Utiliser SQL Server et R](../rtvs/integrating-sql-server-with-r.md)
- [In-database Advanced Analytics with R in SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [Python in SQL Server 2017: enhanced in-database machine learning (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Services et SDK supplémentaires

En plus de ce qui se trouve directement dans la charge de travail Applications de science et analyse des données, le service Azure Notebooks et le SDK Azure pour Python sont également très utiles pour la science des données.

Le kit SDK Azure pour Python facilite l’utilisation et la gestion des services Microsoft Azure à partir d’applications fonctionnant sur Windows, Mac et Linux. Pour plus d’informations, consultez [Kit SDK Azure pour Python](/azure/python/).

Azure Notebooks (actuellement en préversion) fournit un accès en ligne gratuit aux notebooks Jupyter qui s’exécutent dans le cloud sur Microsoft Azure. Le service inclut des exemples de notebooks en Python, R et F# pour vous aider à démarrer. Visitez [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Captures d’écran d’Azure Notebooks avec l’exemple d’introduction à R](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
