---
title: Création et gestion des bases de données et des applications de la couche données
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2b1caf45235f9dd745841cb26a2fa10a148a7b5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299650"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Création et gestion de bases de données et d’applications de couche Données dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IMPORTANT]
> Les projets de base de données inclus dans les versions antérieures de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sont désormais fournis dans les outils de [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)]. Pour plus d’informations, consultez [SQL Server développeur Tools](https://go.microsoft.com/fwlink/?LinkId=228126).

 Vous pouvez utiliser des projets de base de données pour créer des bases de données, des applications de la couche données (DAC) et mettre à jour des applications de couche données et des bases de données existantes. Les projets de base de données et les projets DAC vous permettent d’appliquer le contrôle de version et les techniques de gestion de projet à vos efforts de développement de base de données à peu près de la même façon que vous appliquez ces techniques à du code managé ou natif. Vous pouvez aider votre équipe de développement à gérer les modifications apportées aux bases de données et aux serveurs de base de données en créant un projet *DAC*, un *projet de base de données*ou un *projet serveur* et en le plaçant sous contrôle de version. Les membres de votre équipe peuvent ensuite extraire des fichiers pour créer, générer et tester les modifications dans un *environnement de développement isolé*, ou bac à sable (sandbox), avant de les partager avec l’équipe. Pour garantir la qualité du code, votre équipe peut terminer et tester toutes les modifications apportées à une version particulière de la base de données dans un environnement intermédiaire avant de déployer les modifications en production.

 Pour obtenir la liste des fonctionnalités de base de données prises en charge par les applications de la couche données, consultez [fonctionnalités prises en charge dans les applications de la couche données](https://go.microsoft.com/fwlink/?LinkId=164239) sur le site Web de Microsoft. Si vous utilisez des fonctionnalités de votre base de données qui ne sont pas prises en charge par les applications de la couche données, vous devez plutôt utiliser un projet de base de données pour gérer les modifications apportées à votre base de données.

## <a name="common-high-level-tasks"></a>Tâches courantes de haut niveau

|Tâche de haut niveau|Contenu de support|
|----------------------|------------------------|
|**Démarrer le développement d’une application de la couche données :** Une DAC est un nouveau concept introduit avec [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] qui contient la définition d’une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les objets d’instance de prise en charge qui sont utilisés par une application client-serveur ou à 3 couches. Une DAC comprend des objets de base de données, tels que des tables et des vues, ainsi que des entités d’instance telles que des connexions. Vous pouvez utiliser [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour créer un projet DAC, créer un fichier de package DAC et envoyer ce fichier de package DAC à un administrateur de base de données en vue d’un déploiement sur une instance du moteur de base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|-   [création et gestion d’applications de la couche données](https://go.microsoft.com/fwlink/?LinkId=160741) (site Web Microsoft)<br />-   [SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=227328)|
|**Développement de base de données itérative en cours :** Si vous êtes un développeur ou un testeur, vous pouvez extraire des parties du projet, puis les mettre à jour dans un environnement de développement isolé. À l’aide de ce type d’environnement, vous pouvez tester vos modifications sans affecter les autres membres de l’équipe. Une fois les modifications terminées, vous archivez de nouveau les fichiers dans le contrôle de version, où d’autres membres de l’équipe peuvent obtenir vos modifications et les générer et les déployer sur un serveur de test.|-   [les éditeurs de requêtes et de texte (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (site Web Microsoft)<br />-   [le débogueur Transact-SQL](https://go.microsoft.com/fwlink/?LinkId=227324) (site Web Microsoft)|
|**Prototypage, vérification des résultats des tests et modification des scripts et des objets de base de données :** Vous pouvez utiliser l’éditeur de [!INCLUDE[tsql](../includes/tsql-md.md)] pour exécuter l’une de ces tâches courantes.|-   [les éditeurs de requêtes et de texte (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (site Web Microsoft)|

## <a name="see-also"></a>Voir aussi
 [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
