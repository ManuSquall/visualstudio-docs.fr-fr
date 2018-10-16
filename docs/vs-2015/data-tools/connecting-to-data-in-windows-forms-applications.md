---
title: Connexion aux données dans les Windows Forms Applications | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- System.Data.SqlClient.SqlConnection
- System.Data.Odbc.OdbcConnection
- System.Data.OleDb.OleDbConnection
- System.Data.OracleClient.OracleConnection
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connection objects, tools for working with
- OleDbConnection class, ADO.NET connection objects
- databases [Visual Studio], connecting to
- data adapters, connections
- connection pooling, ADO.NET connections
- connection strings [Visual Studio], ADO.NET
- connection objects, types of
- dynamic properties, ADO.NET connections
- connections, about connections
- data [Visual Studio], connecting
- design-time connections
- connections, design-time
- TableAdapters, connections
- connection objects
- SqlConnection class, ADO.NET connection objects
- connecting to databases, ADO.NET connections
- transactions, ADO.NET
- database connections [Visual Studio], ADO.NET
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d8da35b32f3dd25bd7ed47b25f722c6b0aa21ac7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208947"
---
# <a name="connecting-to-data-in-windows-forms-applications"></a>Connexion à des données dans des applications Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fournit des outils pour connecter votre application aux données de nombreuses sources différentes, telles que des bases de données, des services web et des objets. Si vous utilisez des outils de conception de données dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous n'avez souvent pas besoin de créer explicitement un objet de connexion pour votre forme ou composant. L'objet de connexion est généralement créé suite à l'exécution d'un Assistant de données ou du déplacement d'objets de données vers votre formulaire. Pour connecter votre application aux données dans une base de données, un service web ou un objet, exécutez le [Assistant de Configuration de Source de données](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) en sélectionnant **ajouter une nouvelle Source de données** à partir de la [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Le diagramme suivant illustre le flux d’opérations standard pendant la connexion aux données en exécutant une requête TableAdapter pour récupérer les données et les afficher dans un formulaire d’une application Windows.  
  
 ![Flux de données dans une application cliente](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Dans certains cas, il est pratique de créer un objet de connexion sans l'assistance d'un outil de conception de données. Pour plus d’informations sur la création de connexions par programmation, consultez [connexion à une Source de données](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e).  
  
> [!NOTE]
>  Pour plus d’informations sur la connexion des applications web aux données, consultez [ASP.NET Data Access Content Map](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## <a name="walkthroughs-for-connecting-windows-forms-applications-to-data"></a>Procédures pas à pas pour connecter des applications Windows Forms aux données  
 Les procédures pas à pas suivantes concernent la connexion aux données dans les applications Windows Forms :  
  
-   [Procédure pas à pas : Connexion aux données dans une base de données (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)  
  
-   [Procédure pas à pas : connexion à des données dans un fichier de base de données local (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [Procédure pas à pas : Connexion aux données dans un Service Web (Windows Forms)](http://msdn.microsoft.com/library/079fb9b0-c733-40c1-acd1-d0d68834354d)  
  
-   [Procédure pas à pas : Connexion aux données dans des objets (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)  
  
-   [Se connecter à des données dans une base de données Access (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## <a name="creating-connections"></a>Création de connexions  
 Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], les connexions sont configurées à l’aide de la **Ajouter/modifier la connexion** boîte de dialogue. Le **ajouter une connexion** boîte de dialogue s’affiche lorsque vous modifiez ou créez des connexions dans l’un des Assistants de données ou [Server Explorer/Database Explorer](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) ou quand vous modifiez des propriétés de connexion dans le **propriétés** fenêtre.  
  
 Les connexions de données sont automatiquement configurées quand vous effectuez l'une des actions suivantes :  
  
|Action|Description|  
|------------|-----------------|  
|Exécutez le [Assistant Configuration de Source de données](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).|Les connexions sont configurées lorsque le chemin d’accès de base de données est choisi dans la **Assistant de Configuration de Source de données**. Pour plus d'informations, consultez [How to: Connect to Data in a Database](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Exécutez le [Assistant Configuration de TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8).|Les connexions sont créées dans le **Assistant Configuration de TableAdapter**. Pour plus d’informations, consultez [créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Exécutez le [modifier des TableAdapters](../data-tools/editing-tableadapters.md).|Les connexions sont créées dans le **Assistant Configuration de requêtes TableAdapter**. Pour plus d’informations, consultez [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).|  
|Faites glisser des éléments à partir de la [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) sur un formulaire ou la [Component Designer](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282).|Objets de connexion sont créés lorsque vous faites glisser des éléments à partir de la **des Sources de données** fenêtre vers le **Windows Forms Designer** ou **Component Designer**. Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Ajouter de nouvelles connexions de données à [Server Explorer/Database Explorer](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d).|Connexions de données dans **Server Explorer/Database Explorer** apparaissent dans la liste des connexions disponibles dans les Assistants de données|  
  
## <a name="connection-strings"></a>Chaînes de connexion  
 Les chaines de connexion peuvent être stockées dans votre application compilée ou dans le fichier de configuration de l'application. Pour plus d’informations, consultez [Comment : enregistrer et modifier des chaînes de connexion](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
## <a name="connection-information-and-security"></a>Informations de connexion et sécurité  
 Comme l'ouverture d'une connexion implique l'accès à une ressource importante (une base de données), il existe souvent des problèmes de sécurité dans la configuration et l'utilisation d'une connexion.  
  
 La façon dont vous sécurisez l'application et son accès à la source de données dépend de l'architecture de votre système. Dans une application web, par exemple, les utilisateurs obtiennent généralement un accès anonyme à Internet Information Services (IIS) et, par conséquent, ne fournissent pas d'informations d'identification de sécurité. Dans ce cas, votre application tient à jour ses propres informations de connexion et les utilise, au lieu d'informations utilisateur spécifiques, pour ouvrir la connexion et accéder à la base de données.  
  
> [!IMPORTANT]
>  Le stockage des détails de la chaîne de connexion (comme un mot de passe) peut affecter la sécurité de votre application. Le recours à la sécurité intégrée de Windows est un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
 Dans les applications intranet ou multicouches, vous pouvez utiliser l'option de sécurité intégrée fournie par Windows, IIS et SQL Server. Dans ce modèle, les informations d'identification de l'utilisateur pour le réseau local sont également utilisées pour accéder aux ressources de base de données, et aucun nom d'utilisateur ou mot de passe explicite n'est utilisé dans la chaîne de connexion. En général, les autorisations sont établies sur l'ordinateur serveur de base de données au moyen de groupes et vous n'avez pas besoin d'établir des autorisations individuelles pour chaque utilisateur qui accède à la base de données. Dans ce modèle, vous n'avez pas besoin de stocker des informations de connexion et aucune autre étape n'est requise pour protéger les informations de la chaîne de connexion.  
  
 Pour plus d'informations sur la sécurité, consultez les rubriques suivantes :  
  
-   [Sécurisation des applications ADO.NET](http://msdn.microsoft.com/library/005a1d43-6ee5-471e-ad98-1d30a44d49d5)  
  
-   [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](http://msdn.microsoft.com/library/3cd3e55b-2f5e-40dd-835d-f50f7ce08967)  
  
## <a name="design-time-connections-in-server-explorerdatabase-explorer"></a>Connexions au moment du design dans l’Explorateur de serveurs/Explorateur de bases de données  
 **Server Explorer/Database Explorer** offre un moyen vous permettant de créer des connexions aux sources de données au moment du design. Cela vous permet de parcourir les sources de données disponibles, d'afficher les informations sur les tables, les colonnes et les autres éléments qu'elles contiennent, et de modifier et créer des éléments de base de données.  
  
 Votre application n’utilise pas directement les connexions disponibles dans **Server Explorer/Database Explorer**. Ces connexions servent à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour utiliser votre base de données au moment de la conception. Pour plus d’informations, consultez [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Par exemple, au moment du design, vous pouvez utiliser **Server Explorer/Database Explorer** pour créer une connexion à une base de données. Plus tard, lorsque vous concevez un formulaire, vous pouvez parcourir la base de données, sélectionnez les colonnes d’une table et les faire glisser dans le [Concepteur de Dataset](../data-tools/creating-and-editing-typed-datasets.md). Cette opération crée un [TableAdapter](../data-tools/tableadapter-overview.md) dans votre jeu de données. Cela crée aussi un objet de connexion, composant du TableAdapter récemment créé.  
  
 Les informations sur les connexions au moment du design sont stockées sur votre ordinateur local, indépendamment du projet ou de la solution. Par conséquent, une fois que vous avez établi une connexion au moment du design en travaillant dans une application, il apparaît dans **Server Explorer/Database Explorer** chaque fois que vous travaillez dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aussi longtemps que le serveur auquel la connexion points est disponible. Pour plus d’informations, consultez [Comment : se connecter à une base de données à partir de l’Explorateur de serveurs](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../includes/sqlobjectexplorer-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Comment : établir une connexion à des données d’une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Procédure pas à pas : Connexion aux données dans une base de données (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [ASP.NET Data Access Content Map](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Enregistrer des données](../data-tools/saving-data.md)