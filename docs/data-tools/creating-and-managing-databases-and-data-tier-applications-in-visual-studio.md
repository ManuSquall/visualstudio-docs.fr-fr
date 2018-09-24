---
title: Projets de base de données, les projets de serveur et les projets DAC dans Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6ca08103614989ddbfd096a08a1531e756c9f67c
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176101"
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>Projets de base de données et applications de couche données dans Visual Studio

Vous pouvez utiliser des projets de base de données pour créer de nouvelles bases de données nouvelles applications de couche données (DAC) et mettre à jour des bases de données existantes et les applications de couche données. Les projets de base de données et les projets DAC permettent d’appliquer des techniques de gestion de projet et de contrôle de version à vos efforts de développement de base de données de la même façon que vous appliquez ces techniques à code managé ou natif. Vous pouvez aider votre équipe de développement à gérer les modifications apportées aux bases de données et les serveurs de base de données en créant un projet DAC, projet de base de données ou un projet de serveur et en le mettant sous contrôle de version. Membres de votre équipe peuvent ensuite extraire des fichiers à rendre, générer et tester des modifications dans un environnement de développement isolé, ou bac à sable, avant de les partager avec l’équipe. Pour garantir la qualité du code, votre équipe peut terminer et tester toutes les modifications pour une version particulière de la base de données dans un environnement intermédiaire avant de déployer les modifications en production.

Pour obtenir la liste des fonctionnalités de base de données qui sont pris en charge par les Applications de couche données, consultez [fonctionnalités prises en charge dans les applications de couche données](/previous-versions/visualstudio/visual-studio-2010/ee362013(v=vs.100)). Si vous utilisez des fonctionnalités de votre base de données qui ne sont pas pris en charge par les Applications de couche données, vous devez plutôt utiliser un projet de base de données pour gérer les modifications apportées à votre base de données.

## <a name="common-high-level-tasks"></a>Tâches courantes de haut niveau

|Tâches de haut niveau|Contenu de support|
|----------------------|------------------------|
|**Démarrer le développement d’une application de couche données :** une DAC est un nouveau concept introduit avec [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] qui contient la définition d’un [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] les objets qui sont utilisés par un client-serveur ou de la couche 3 d’instance de base de données et la prise en charge application. Une DAC inclut des objets de base de données, tels que des tables et des vues, ainsi que les entités d’instance telles que les connexions. Vous pouvez utiliser Visual Studio pour créer un projet DAC, générer un fichier de package DAC et envoyer ce fichier de package à un administrateur de base de données pour le déploiement sur une instance de la [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] moteur de base de données.|-   [Créer et gérer des Applications de couche données](http://go.microsoft.com/fwlink/?LinkId=160741)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Son développement itératif :** si vous êtes un développeur ou testeur, extraire des éléments du projet et de mettre à jour dans un environnement de développement isolé. À l’aide de ce type d’environnement, vous pouvez tester vos modifications sans affecter les autres membres de l’équipe. Une fois que les modifications sont terminées, vous vérifiez les fichiers au contrôle de version, où autres membres de l’équipe peuvent obtenir vos modifications et créer et les déployer sur un serveur de test.|-   [Requête et les éditeurs de texte (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327)<br />-   [Débogueur Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324)|
|**Prototypage, vérification des résultats des tests et modification des scripts de base de données et objets :** vous pouvez utiliser le [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] éditeur pour effectuer l’une de ces tâches courantes.|-   [Requête et les éditeurs de texte (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327)|

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
