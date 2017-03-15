---
title: "Creating and Managing Databases and Data-tier Applications in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing change, databases"
  - "database features of Visual Studio, managing change"
  - "databases, managing change"
  - "managing change, database servers"
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 37
caps.handback.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating and Managing Databases and Data-tier Applications in Visual Studio
> [!IMPORTANT]
>  Les projets de base de données inclus dans les versions antérieures d' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sont maintenant disponibles dans les outils d' [!INCLUDE[sql_Denali_long](../data-tools/includes/sql_denali_long_md.md)] .  Pour plus d'informations, consultez [Outils de développement de SQL Server](http://go.microsoft.com/fwlink/?LinkId=228126).  
  
 Vous pouvez utiliser des projets de base de données pour créer et mettre à jour des bases de données et des applications de couche Données \(DAC\).  Les projets de base de données et d'applications de couche Données vous permettent d'appliquer les techniques de contrôle de version et de gestion de projet au développement de bases de données, de la même façon que vous les appliquez à du code managé ou du code natif.  Vous pouvez aider votre équipe de développement à gérer les modifications apportées aux bases de données et aux serveurs de base de données en créant un *projet d'application de couche Données*, un *projet de base de données* ou un *projet serveur*, et en le mettant sous contrôle de version.  Les membres de votre équipe peuvent alors extraire les fichiers à créer puis générer, et tester les modifications dans un *environnement de développement isolé* \(ou sandbox\), avant de les partager avec les autres membres de l'équipe.  Pour garantir la qualité du code, votre équipe peut tester toutes les modifications d'une version de base de données dans un environnement intermédiaire avant de déployer ces modifications en production.  
  
 Pour une liste des fonctionnalités de base de données qui sont prises en charge par les applications de couche Données, consultez [Fonctionnalités prises en charge dans les applications de couche Données](http://go.microsoft.com/fwlink/?LinkId=164239) sur le site Web Microsoft.  Si vous utilisez des fonctionnalités de votre base de données qui ne sont pas prises en charge par les applications de couche Données, vous devez utiliser un projet de base de données pour gérer les modifications apportées à votre base de données.  
  
## Tâches courantes de niveau supérieur  
  
|Tâches de niveau supérieur|Contenu de support|  
|--------------------------------|------------------------|  
|**Démarrer le développement d'une application de couche Données :** une application de couche Données est un nouveau concept introduit par [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)]. Elle contient la définition d'une base de données [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] et des objets d'instance de support utilisés par un client\-serveur ou une application à 3 niveaux.  Une application de couche Données comprend des objets de base de données, tels que des tables et des vues, ainsi que des entités d'instance telles que des connexions.  Vous pouvez utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour créer un projet d'application de couche Données, générer un fichier de package d'application de couche Données et envoyer ce fichier de package à un administrateur de base de données pour un déploiement sur une instance du moteur de base de données [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].|-   [Création et gestion d'applications de la couche Données](http://go.microsoft.com/fwlink/?LinkId=160741) \(site Web Microsoft\)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**Exécuter un développement de base de données itératif :** si vous êtes développeur ou testeur, vous devez extraire certaines parties du projet, puis les mettre à jour dans un environnement de développement isolé.  En utilisant ce type d'environnement, vous pouvez tester vos modifications sans affecter les autres membres de l'équipe.  Une fois les modifications terminées, mettez de nouveau les fichiers sous contrôle de version, où les autres membres de l'équipe pourront récupérer vos modifications, les générer et les déployer sur un serveur de test.|-   [requête et éditeurs de texte \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Site Web Microsoft\)<br />-   [Débogueur Transact\-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) \(Site Web Microsoft\)|  
|**Créer des prototypes, vérifier des résultats de tests et modifier des scripts et des objets de base de données :** vous pouvez utiliser l'éditeur [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] pour exécuter l'une de ces tâches courantes.|-   [requête et éditeurs de texte \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Site Web Microsoft\)|