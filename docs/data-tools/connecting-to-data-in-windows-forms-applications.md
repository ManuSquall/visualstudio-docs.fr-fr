---
title: "Connexion &#224; des donn&#233;es dans des applications Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "System.Data.SqlClient.SqlConnection"
  - "System.Data.Odbc.OdbcConnection"
  - "System.Data.OleDb.OleDbConnection"
  - "System.Data.OracleClient.OracleConnection"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "connecter à des bases de données, connexions ADO.NET"
  - "objets de connexion"
  - "objets de connexion, outils pour utiliser"
  - "objets de connexion, types de"
  - "regroupement de connexion, connexions ADO.NET"
  - "chaînes de connexion (Visual Studio), ADO.NET"
  - "connexions, à propos des connexions"
  - "connexions, en mode Design"
  - "données (Visual Studio), connecter"
  - "adaptateurs de données, connexions"
  - "connexions de base données (Visual Studio), ADO.NET"
  - "bases de données (Visual Studio), connecter à"
  - "connexions en mode Design"
  - "propriétés dynamiques, connexions ADO.NET"
  - "OleDbConnection (classe), ADO.NET (objets de connexion)"
  - "SqlConnection (classe), ADO.NET (objets de connexion)"
  - "TableAdapters, connexions"
  - "transactions, ADO.NET"
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Connexion &#224; des donn&#233;es dans des applications Windows Forms
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fournit des outils pour connecter votre application aux données de nombreuses sources différentes, telles que des bases de données, des services web et des objets.  Si vous utilisez des outils de conception de données dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous n'avez souvent pas besoin de créer explicitement un objet de connexion pour votre forme ou composant.  L'objet de connexion est généralement créé suite à l'exécution d'un Assistant de données ou du déplacement d'objets de données vers votre formulaire.  Pour connecter votre application aux données d'une base de données, d'un service web ou d'un objet, exécutez l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png) en sélectionnant **Ajouter une nouvelle source de données** dans la [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md).  
  
 Le diagramme suivant illustre le flux d'opérations standard pendant la connexion aux données en exécutant une requête TableAdapter pour extraire les données et les afficher dans un formulaire d'une application Windows.  
  
 ![Flux de données dans une application cliente](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Dans certains cas, il est pratique de créer un objet de connexion sans l'assistance d'un outil de conception de données.  Pour plus d'informations sur la création de connexions par programmation, consultez [Connexion à une source de données](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md).  
  
> [!NOTE]
>  Pour plus d'informations sur la connexion d'applications web aux données, consultez [ASP.NET Data Access Content Map](http://msdn.microsoft.com/fr-fr/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## Procédures pas à pas pour connecter des applications Windows Forms aux données  
 Les procédures pas à pas suivantes concernent la connexion aux données dans les applications Windows Forms :  
  
-   [Procédure pas à pas : connexion à des données dans une base de données \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)  
  
-   [Procédure pas à pas : connexion à des données dans un fichier de base de données local \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)  
  
-   [Procédure pas à pas : connexion à des données dans un service Web \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Web%20Service%20\(Windows%20Forms\).md)  
  
-   [Procédure pas à pas : connexion à des données dans des objets \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)  
  
-   [Procédure pas à pas : connexion à des données dans une base de données Access \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## Création de connexions  
 Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], les connexions sont configurées à l'aide de la boîte de dialogue **Ajouter\/Modifier une connexion**.  La boîte de dialogue **Ajouter une connexion** apparaît quand vous modifiez ou créez des connexions dans un Assistant de données ou l'[Explorateur de serveurs\/Explorateur de bases de données](../Topic/Server%20Explorer.md), ou quand vous modifiez des propriétés de connexion dans la fenêtre **Propriétés**.  
  
 Les connexions de données sont automatiquement configurées quand vous effectuez l'une des actions suivantes :  
  
|Action|Description|  
|------------|-----------------|  
|Exécutez l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png).|Les connexions sont configurées quand le chemin d'accès de la base de données est choisi dans l'**Assistant Configuration de source de données**.  Pour plus d'informations, consultez [Comment : établir une connexion à des données d'une base de données](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Exécutez l'[Configuration de TableAdapter \(Assistant\)](../Topic/TableAdapter%20Configuration%20Wizard.md).|Les connexions sont créées dans l'**Assistant Configuration de TableAdapter**.  Pour plus d'informations, consultez [Comment : créer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Exécutez l'[Configuration de requête TableAdapter \(Assistant\)](../data-tools/editing-tableadapters.md).|Les connexions sont créées dans l'**Assistant Configuration de requêtes TableAdapter**.  Pour plus d'informations, consultez [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).|  
|Faites glisser des éléments depuis la [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md) vers un formulaire ou le [Component Designer](../Topic/Component%20Designer.md).|Les objets de connexion sont créés quand vous faites glisser des éléments depuis la fenêtre **Sources de données** vers le **Concepteur Windows Forms** ou le **Concepteur de composants**.  Pour plus d'informations, consultez [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Ajoutez de nouvelles connexions de données à l'[Explorateur de serveurs\/Explorateur de bases de données](../Topic/Server%20Explorer.md).|Les connexions de données de l'**Explorateur de serveurs\/Explorateur de bases de données** apparaissent dans la liste des connexions disponibles des Assistants de données.|  
  
## Chaînes de connexion  
 Les chaines de connexion peuvent être stockées dans votre application compilée ou dans le fichier de configuration de l'application.  Pour plus d'informations, consultez [Comment : enregistrer et modifier des chaînes de connexion](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
## Informations de connexion et sécurité  
 Comme l'ouverture d'une connexion implique l'accès à une ressource importante \(une base de données\), il existe souvent des problèmes de sécurité dans la configuration et l'utilisation d'une connexion.  
  
 La façon dont vous sécurisez l'application et son accès à la source de données dépend de l'architecture de votre système.  Dans une application web, par exemple, les utilisateurs obtiennent généralement un accès anonyme à Internet Information Services \(IIS\) et, par conséquent, ne fournissent pas d'informations d'identification de sécurité.  Dans ce cas, votre application tient à jour ses propres informations de connexion et les utilise, au lieu d'informations utilisateur spécifiques, pour ouvrir la connexion et accéder à la base de données.  
  
> [!IMPORTANT]
>  Le stockage des détails de la chaîne de connexion \(comme un mot de passe\) peut affecter la sécurité de votre application.  Le recours à la sécurité intégrée de Windows est un moyen plus sûr de contrôler l'accès à une base de données.  Pour plus d'informations, consultez [Protection des informations de connexion](../Topic/Protecting%20Connection%20Information.md).  
  
 Dans les applications intranet ou multicouches, vous pouvez utiliser l'option de sécurité intégrée fournie par Windows, IIS et SQL Server.  Dans ce modèle, les informations d'identification de l'utilisateur pour le réseau local sont également utilisées pour accéder aux ressources de base de données, et aucun nom d'utilisateur ou mot de passe explicite n'est utilisé dans la chaîne de connexion.  En général, les autorisations sont établies sur l'ordinateur serveur de base de données au moyen de groupes et vous n'avez pas besoin d'établir des autorisations individuelles pour chaque utilisateur qui accède à la base de données.  Dans ce modèle, vous n'avez pas besoin de stocker des informations de connexion et aucune autre étape n'est requise pour protéger les informations de la chaîne de connexion.  
  
 Pour plus d'informations sur la sécurité, consultez les rubriques suivantes :  
  
-   [Sécurisation des applications ADO.NET](../Topic/Securing%20ADO.NET%20Applications.md)  
  
-   [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](../Topic/More%20Secure%20File%20and%20Data%20Access%20in%20Windows%20Forms.md)  
  
## Connexions au moment de la conception dans l'Explorateur de serveurs\/Explorateur de bases de données  
 L'**Explorateur de serveurs\/Explorateur de bases de données** vous fournit un moyen de créer des connexions aux sources de données au moment de la conception.  Cela vous permet de parcourir les sources de données disponibles, d'afficher les informations sur les tables, les colonnes et les autres éléments qu'elles contiennent, et de modifier et créer des éléments de base de données.  
  
 Votre application n'utilise pas directement les connexions disponibles dans l'**Explorateur de serveurs\/Explorateur de bases de données**.  Ces connexions servent à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour utiliser votre base de données au moment de la conception.  Pour plus d'informations, consultez [Visual Database Tools](http://msdn.microsoft.com/fr-fr/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Par exemple, au moment de la conception vous pouvez utiliser l'**Explorateur de serveurs\/Explorateur de bases de données** pour créer une connexion à une base de données.  Plus tard, quand vous concevez un formulaire, vous pouvez parcourir la base de données, sélectionner des colonnes dans une table et les faire glisser dans le [Concepteur de DataSet](../data-tools/creating-and-editing-typed-datasets.md).  Cela crée un [TableAdapter](../data-tools/tableadapter-overview.md) dans votre dataset.  Cela crée aussi un objet de connexion, composant du TableAdapter récemment créé.  
  
 Les informations sur les connexions au moment de la conception sont stockées sur votre ordinateur local, indépendamment du projet ou de la solution.  Par conséquent, dès que vous établissez une connexion au moment de la conception pendant que vous utilisez une application, elle apparaît dans l'**Explorateur de serveurs\/Explorateur de bases de données** si vous utilisez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], du moment que le serveur vers lequel pointe la connexion est disponible.  Pour plus d'informations, consultez [How to: Connect to a Database from Server Explorer](http://msdn.microsoft.com/fr-fr/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../data-tools/includes/sqlobjectexplorer_md.md)]  
  
## Voir aussi  
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Comment : établir une connexion à des données d'une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Procédure pas à pas : connexion à des données dans une base de données \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [ASP.NET Data Access Content Map](http://msdn.microsoft.com/fr-fr/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)