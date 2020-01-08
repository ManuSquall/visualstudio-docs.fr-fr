---
title: Projets de base de données et projets DAC
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cc8d32ddcc332264278cf76392ac69a6188ca51c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586729"
---
# <a name="database-projects-and-data-tier-applications"></a>Projets de base de données et applications de la couche données

Vous pouvez utiliser des projets de base de données pour créer des bases de données, des applications de la couche données (DAC) et mettre à jour des applications de couche données et des bases de données existantes. Les projets de base de données et les projets DAC vous permettent d’appliquer le contrôle de version et les techniques de gestion de projet à vos efforts de développement de base de données à peu près de la même façon que vous appliquez ces techniques à du code managé ou natif. Vous pouvez aider votre équipe de développement à gérer les modifications apportées aux bases de données et aux serveurs de base de données en créant un projet DAC, un projet de base de données ou un projet serveur et en le plaçant sous contrôle de version. Les membres de votre équipe peuvent ensuite extraire des fichiers pour créer, générer et tester les modifications dans un environnement de développement isolé, ou bac à sable (sandbox), avant de les partager avec l’équipe. Pour garantir la qualité du code, votre équipe peut terminer et tester toutes les modifications apportées à une version particulière de la base de données dans un environnement intermédiaire avant de déployer les modifications en production.

Pour obtenir la liste des fonctionnalités de base de données prises en charge par les applications de la couche données, consultez [prise en charge DAC pour les objets SQL Server](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Si vous utilisez des fonctionnalités de votre base de données qui ne sont pas prises en charge par les applications de la couche données, vous devez plutôt utiliser un projet de base de données pour gérer les modifications apportées à votre base de données.

## <a name="common-high-level-tasks"></a>Tâches courantes de haut niveau

| Tâche de haut niveau | Contenu de support |
| - | - |
| **Démarrer le développement d’une application de la couche données :** Le concept d’application de la couche données (DAC) a été introduit avec SQL Server 2008. Une DAC contient la définition d’une base de données SQL Server et les objets d’instance de prise en charge qui sont utilisés par une application client-serveur ou 3 couches. Une DAC comprend des objets de base de données, tels que des tables et des vues, ainsi que des entités d’instance telles que des connexions. Vous pouvez utiliser Visual Studio pour créer un projet DAC, créer un fichier de package DAC et envoyer le fichier de package DAC à un administrateur de base de données pour le déploiement sur une instance du moteur de base de données SQL Server. | - [Applications de la couche Données](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Développement de base de données itérative en cours :** Les développeurs peuvent extraire des parties du projet et les mettre à jour dans un environnement de développement isolé. À l’aide de ce type d’environnement, vous pouvez tester vos modifications sans affecter les autres membres de l’équipe. Une fois les modifications terminées, vous archivez de nouveau les fichiers dans le contrôle de version, où d’autres membres de l’équipe peuvent obtenir vos modifications et les générer et les déployer sur un serveur de test. | - [le développement de bases de données hors connexion orientées projet (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [le débogueur Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Prototypage, vérification des résultats des tests et modification des scripts et des objets de base de données :** Vous pouvez utiliser l’éditeur Transact-SQL pour exécuter l’une de ces tâches courantes. | - [les éditeurs de requêtes et de texte (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
