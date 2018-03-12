---
title: "Base de données des projets, des projets serveur et des projets DAC dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 8e599e1d309ab254c2b2d5a3a490c0cd912b8823
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>Projets de base de données et les applications de couche données dans Visual Studio  
Vous pouvez utiliser des projets de base de données pour créer de nouvelles bases de données, des applications de couche données (DAC) et mettre à jour les bases de données et les applications de couche données. Les projets de base de données et les projets DAC permettent d’appliquer des techniques de gestion de projet et le contrôle de version à vos efforts de développement de base de données de la même façon que vous appliquez ces techniques au code managé ou natif. Vous pouvez aider votre équipe de développement gérer les modifications apportées aux bases de données et les serveurs de base de données en créant un *projet DAC*, *projet de base de données*, ou un *projet server* et leur placement sous contrôle de version. Membres de votre équipe peuvent ensuite consulter les fichiers à apporter, générer et tester des modifications dans un *environnement de développement isolé*, ou bac à sable, avant de les partager avec l’équipe. Pour garantir la qualité du code, votre équipe peut terminer et toutes les modifications pour une version particulière de la base de données de test dans un environnement intermédiaire avant de déployer les modifications en production.  
  
Pour obtenir la liste des fonctionnalités de base de données qui sont prises en charge par les Applications de couche données, consultez [fonctionnalités prises en charge dans les Applications de couche données](http://go.microsoft.com/fwlink/?LinkId=164239) sur le site web Microsoft. Si vous utilisez des fonctionnalités de votre base de données qui ne sont pas pris en charge par les Applications de couche données, vous devez plutôt utiliser un projet de base de données pour gérer les modifications apportées à votre base de données.  
  
## <a name="common-high-level-tasks"></a>Tâches courantes de niveau supérieur  
  
|Tâches de niveau supérieur|Contenu de support|  
|----------------------|------------------------|  
|**Démarrer le développement d’une application de couche données :** une DAC est un nouveau concept introduit avec [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] qui contient la définition d’un [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] les objets qui sont utilisés par un client-serveur ou le niveau 3 d’instance de base de données et la prise en charge application. Une DAC inclut des objets de base de données, tels que des tables et des vues, ainsi que les entités telles que les connexions d’instance. Vous pouvez utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour créer un projet DAC, générer un fichier de package DAC et envoyer ce fichier de package à un administrateur de base de données pour le déploiement sur une instance de la [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] moteur de base de données.|-   [Création et la gestion des Applications de couche données](http://go.microsoft.com/fwlink/?LinkId=160741) (site web de Microsoft)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**Effectuer le développement itératif de base de données :** si vous êtes un développeur ou un testeur, extraire des parties du projet et de mettre à jour dans un environnement de développement isolé. À l’aide de ce type d’environnement, vous pouvez tester vos modifications sans affecter les autres membres de l’équipe. Une fois les modifications terminées, vous vérifiez les fichiers au contrôle de version, où autres membres de l’équipe peuvent obtenir vos modifications et générer et les déployer sur un serveur de test.|-   [Éditeurs de texte (SQL Server Management Studio) et de requête](http://go.microsoft.com/fwlink/?LinkId=227327) (site web de Microsoft)<br />-   [Débogueur Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) (site web de Microsoft)|  
|**Prototypage, vérification de résultats des tests et modification des scripts de base de données et objets :** que vous pouvez utiliser la [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] éditeur pour effectuer l’une de ces tâches courantes.|-   [Éditeurs de texte (SQL Server Management Studio) et de requête](http://go.microsoft.com/fwlink/?LinkId=227327) (site web de Microsoft)|  
  
## <a name="see-also"></a>Voir aussi
[Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
