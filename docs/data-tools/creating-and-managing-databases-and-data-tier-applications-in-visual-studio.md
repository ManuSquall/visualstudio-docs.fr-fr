---
title: Projets de base de données et de DAC
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ad784e0438e0b1f02607c3cb748c759b9266dbe6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824572"
---
# <a name="database-projects-and-data-tier-applications"></a>Projets de base de données et applications de couche données

Vous pouvez utiliser des projets de base de données pour créer de nouvelles bases de données nouvelles applications de couche données (DAC) et mettre à jour des bases de données existantes et les applications de couche données. Les projets de base de données et les projets DAC permettent d’appliquer des techniques de gestion de projet et de contrôle de version à vos efforts de développement de base de données de la même façon que vous appliquez ces techniques à code managé ou natif. Vous pouvez aider votre équipe de développement à gérer les modifications apportées aux bases de données et les serveurs de base de données en créant un projet DAC, projet de base de données ou un projet de serveur et en le mettant sous contrôle de version. Membres de votre équipe peuvent ensuite extraire des fichiers à rendre, générer et tester des modifications dans un environnement de développement isolé, ou bac à sable, avant de les partager avec l’équipe. Pour garantir la qualité du code, votre équipe peut terminer et tester toutes les modifications pour une version particulière de la base de données dans un environnement intermédiaire avant de déployer les modifications en production.

Pour obtenir la liste des fonctionnalités de base de données qui sont pris en charge par les applications de couche données, consultez [DAC prennent en charge pour les objets de SQL Server](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Si vous utilisez des fonctionnalités de votre base de données qui ne sont pas pris en charge par les applications de couche données, vous devez plutôt utiliser un projet de base de données pour gérer les modifications apportées à votre base de données.

## <a name="common-high-level-tasks"></a>Tâches courantes de haut niveau

| Tâches de haut niveau | Contenu de support |
| - | - |
| **Démarrer le développement d’une application de couche données :** Le concept d’une application de couche données (DAC) a été introduit avec SQL Server 2008. Une DAC contient la définition d’une base de données SQL Server et les objets d’instance prise en charge qui sont utilisés par un client-serveur ou une application de couche 3. Une DAC inclut des objets de base de données, tels que des tables et des vues, ainsi que les entités d’instance telles que les connexions. Vous pouvez utiliser Visual Studio pour créer un projet DAC, créer un fichier de package DAC et envoyez le fichier de package DAC à un administrateur de base de données pour le déploiement sur une instance du moteur de base de données SQL Server. | - [Applications de la couche Données](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Développement itératif de base de données en cours :** Les développeurs peuvent extraire des éléments du projet et les mettre à jour dans un environnement de développement isolé. À l’aide de ce type d’environnement, vous pouvez tester vos modifications sans affecter les autres membres de l’équipe. Une fois que les modifications sont terminées, vous vérifiez les fichiers au contrôle de version, où autres membres de l’équipe peuvent obtenir vos modifications et créer et les déployer sur un serveur de test. | - [Développement de base de données hors connexion orienté projet (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Débogueur Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Prototypage, la vérification des résultats des tests et la modification des scripts de base de données et des objets :** Vous pouvez utiliser l’éditeur Transact-SQL pour exécuter l’une de ces tâches courantes. | - [Éditeurs de requête et de texte (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)