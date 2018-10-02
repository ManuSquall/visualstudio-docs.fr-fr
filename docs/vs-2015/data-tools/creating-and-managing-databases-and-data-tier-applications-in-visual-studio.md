---
title: Création et gestion de bases de données et applications de couche données dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1ea5370349204765932baed828ffb9c9332b088f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505913"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Création et gestion de bases de données et applications de couche données dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [création et gestion de bases de données et applications de couche données](https://docs.microsoft.com/visualstudio/data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio).  
  
  
IMPORTANT]
>  Les projets de base de données qui ont été inclus dans les versions antérieures de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sont désormais disponibles dans [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] outils. Pour plus d’informations, consultez [SQL Server Developer Tools](http://go.microsoft.com/fwlink/?LinkId=228126).  
  
 Vous pouvez utiliser des projets de base de données pour créer de nouvelles bases de données nouvelles applications de couche données (DAC) et mettre à jour des bases de données existantes et les applications de couche données. Les projets de base de données et les projets DAC permettent d’appliquer des techniques de gestion de projet et de contrôle de version à vos efforts de développement de base de données de la même façon que vous appliquez ces techniques à code managé ou natif. Vous pouvez aider votre équipe de développement gérer les modifications apportées aux bases de données et les serveurs de base de données en créant un *projet DAC*, *projet de base de données*, ou un *projet server* et en le plaçant sous contrôle de version. Membres de votre équipe peuvent ensuite extraire les fichiers à rendre, générer et tester les modifications dans un *environnement de développement isolé*, ou bac à sable, avant de les partager avec l’équipe. Pour garantir la qualité du code, votre équipe peut terminer et tester toutes les modifications pour une version particulière de la base de données dans un environnement intermédiaire avant de déployer les modifications en production.  
  
 Pour obtenir la liste des fonctionnalités de base de données qui sont pris en charge par les Applications de couche données, consultez [fonctionnalités prises en charge dans les Applications de couche données](http://go.microsoft.com/fwlink/?LinkId=164239) sur le site web Microsoft. Si vous utilisez des fonctionnalités de votre base de données qui ne sont pas pris en charge par les Applications de couche données, vous devez plutôt utiliser un projet de base de données pour gérer les modifications apportées à votre base de données.  
  
## <a name="common-high-level-tasks"></a>Tâches courantes de haut niveau  
  
|Tâches de haut niveau|Contenu de support|  
|----------------------|------------------------|  
|**Démarrer le développement d’une application de couche données :** une DAC est un nouveau concept introduit avec [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] qui contient la définition d’un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] les objets qui sont utilisés par un client-serveur ou de la couche 3 d’instance de base de données et la prise en charge application. Une DAC inclut des objets de base de données, tels que des tables et des vues, ainsi que les entités d’instance telles que les connexions. Vous pouvez utiliser [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour créer un projet DAC, générer un fichier de package DAC et envoyer ce fichier de package à un administrateur de base de données pour le déploiement sur une instance de la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] moteur de base de données.|-   [Création et la gestion des Applications de couche données](http://go.microsoft.com/fwlink/?LinkId=160741) (site web de Microsoft)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**Son développement itératif :** si vous êtes un développeur ou testeur, extraire des éléments du projet et de mettre à jour dans un environnement de développement isolé. À l’aide de ce type d’environnement, vous pouvez tester vos modifications sans affecter les autres membres de l’équipe. Une fois que les modifications sont terminées, vous vérifiez les fichiers au contrôle de version, où autres membres de l’équipe peuvent obtenir vos modifications et créer et les déployer sur un serveur de test.|-   [Éditeurs de texte (SQL Server Management Studio) et de requête](http://go.microsoft.com/fwlink/?LinkId=227327) (site web de Microsoft)<br />-   [Débogueur Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) (site web de Microsoft)|  
|**Prototypage, vérification des résultats des tests et modification des scripts de base de données et objets :** vous pouvez utiliser le [!INCLUDE[tsql](../includes/tsql-md.md)] éditeur pour effectuer l’une de ces tâches courantes.|-   [Éditeurs de texte (SQL Server Management Studio) et de requête](http://go.microsoft.com/fwlink/?LinkId=227327) (site web de Microsoft)|  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

