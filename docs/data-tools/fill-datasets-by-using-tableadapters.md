---
title: "Remplissage de groupes de donn&#233;es avec des donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Visual Studio), groupes de données"
  - "données (Visual Studio), récupérer"
  - "récupération des données"
  - "groupes de données (Visual Basic)"
  - "groupes de données (Visual Basic), remplir"
  - "groupes de données (Visual Basic), charger des données"
  - "récupérer des données"
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 32
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Remplissage de groupes de donn&#233;es avec des donn&#233;es
Le TableAdapter est le mécanisme Visual Studio standard pour exécuter des requêtes Transact\-SQL et pour remplir des groupes de données.  
  
 Vous pouvez exécuter des instructions SQL ou des procédures stockées sur une source de données à l'aide de TableAdapters ou d'objets de commande \(par exemple, <xref:System.Data.SqlClient.SqlCommand>\).  Pour charger des données dans des groupes de données créés à l'aide d'outils de conception dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], utilisez des TableAdapters.  Pour charger des données dans des groupes de données créés par programmation, utilisez des adaptateurs de données.  Si votre application n'utilise pas de groupes de données, utilisez des objets de commande pour exécuter directement les instructions SQL ou les procédures stockées sur une base de données.  
  
 Les rubriques suivantes fournissent des détails sur le remplissage de groupes de données avec des données Visual Studio :  
  
|Rubrique|Description|  
|--------------|-----------------|  
|[Comment : remplir de données un groupe de données](../data-tools/how-to-fill-a-dataset-with-data.md)|Fournit des détails sur le chargement de données dans des groupes de données à l'aide de TableAdapters et de DataAdapters.|  
|[Comment : créer et exécuter une instruction SQL qui retourne des lignes](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)|Fournit des détails sur la création et l'exécution d'instructions SQL qui retournent des lignes à l'aide de requêtes TableAdapter et d'objets Command.|  
|[Comment : créer et exécuter une instruction SQL qui retourne une seule valeur](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)|Fournit des détails sur la création et l'exécution d'instructions SQL qui retournent des valeurs uniques à l'aide de requêtes TableAdapter et d'objets Command.|  
|[Comment : créer et exécuter une instruction SQL qui ne retourne aucune valeur](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)|Fournit des détails sur la création et l'exécution d'instructions SQL qui ne retournent aucune valeur à l'aide de requêtes TableAdapter et d'objets Command.|  
|[Comment : exécuter une procédure stockée qui retourne des lignes](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)|Fournit des détails sur l'exécution de procédures stockées qui retournent des lignes à l'aide de requêtes TableAdapter et d'objets Command.|  
|[Comment : exécuter une procédure stockée qui retourne une seule valeur](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)|Fournit des détails sur l'exécution de procédures stockées qui retournent des valeurs uniques à l'aide de requêtes TableAdapter et d'objets Command.|  
|[Comment : exécuter une procédure stockée qui ne retourne aucune valeur](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)|Fournit des détails sur l'exécution de procédures stockées qui ne retournent aucune valeur à l'aide de requêtes TableAdapter et d'objets Command.|  
|[Comment : définir et obtenir des paramètres pour des objets de commande](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)|Fournit des détails sur l'assignation de valeurs à des paramètres dans des requêtes et des procédures stockées, ainsi que sur la lecture des valeurs dans les paramètres retournés par des commandes exécutées.|  
|[Procédure pas à pas : remplissage d'un Dataset avec des données](../Topic/Walkthrough:%20Filling%20a%20Dataset%20with%20Data.md)|Fournit des informations sur la création d'un groupe de données et son remplissage avec des données provenant d'une base de données.|  
|[Procédure pas à pas : lecture des données XML dans un groupe de données](../data-tools/read-xml-data-into-a-dataset.md)|Fournit des détails sur la création d'une application Windows qui charge des données XML dans un groupe de données, puis affiche ce dernier dans un contrôle <xref:System.Windows.Forms.DataGridView>.|  
  
## Le remplissage de groupes de données  
 Si vous créez un groupe de données avec un outil de conception [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(tel que le [Concepteur de DataSet](../data-tools/creating-and-editing-typed-datasets.md) ou l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png)\), vous utilisez un TableAdapter pour le remplir.  Les TableAdapters exécutent vos instructions SQL ou vos procédures stockées.  
  
 Si vous créez un groupe de données sans outil de conception, vous devez utiliser des adaptateurs de données pour remplir et mettre à jour les données.  \(Les TableAdapters ne sont pas des classes réelles dans le [.NET Framework 4.6 et 4.5](../Topic/.NET%20Framework%204.6%20and%204.5.md) ; ils ne sont donc pas appropriés à l'utilisation de groupes de données créés sans outils de conception.\)  Pour plus d'informations sur la façon de charger des données dans des groupes de données avec des TableAdapters ou des adaptateurs de données, consultez [Comment : remplir de données un groupe de données](../data-tools/how-to-fill-a-dataset-with-data.md).  
  
## Requêtes TableAdapter  
 Vous pouvez exécuter des requêtes TableAdapter pour remplir des données dans des groupes de données \(en particulier pour charger des données dans les DataTables qui composent un groupe de données\).  Vous pouvez créer des requêtes TableAdapter à l'aide de l'[Configuration de requête TableAdapter \(Assistant\)](../data-tools/editing-tableadapters.md) dans le **Concepteur de DataSet**.  Les requêtes TableAdapter apparaissent en tant que méthodes nommées sur un TableAdapter et sont exécutées en appelant la méthode TableAdapter.  Pour plus d'informations sur la création et l'exécution des requêtes TableAdapter, consultez les pages suivantes :  
  
-   [Comment : créer et exécuter une instruction SQL qui retourne des lignes](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)  
  
-   [Comment : créer et exécuter une instruction SQL qui retourne une seule valeur](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)  
  
-   [Comment : créer et exécuter une instruction SQL qui ne retourne aucune valeur](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)  
  
-   [Comment : exécuter une procédure stockée qui retourne des lignes](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)  
  
-   [Comment : exécuter une procédure stockée qui retourne une seule valeur](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)  
  
-   [Comment : exécuter une procédure stockée qui ne retourne aucune valeur](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)  
  
## Objets de commande  
 Les objets de commande vous permettent d'exécuter directement des instructions SQL et des procédures stockées sur une base de données, sans avoir besoin d'un <xref:System.Data.DataSet>, d'un TableAdapter ou d'un <xref:System.Data.Common.DataAdapter>.  \(Le terme *objet de commande* fait référence à la commande propre au Fournisseur de données .NET Framework que votre application utilise.  Par exemple, si votre application utilise le fournisseur de données .NET Framework pour SQL Server, l'objet de commande est <xref:System.Data.SqlClient.SqlCommand>.\)  
  
 Pour configurer des commandes afin d'interroger des données à l'aide d'instructions SQL ou de procédures stockées, affectez à la propriété `CommandType` de la commande de données l'une des valeurs comprises dans l'énumération <xref:System.Data.IDbCommand.CommandType%2A>.  Affectez à `CommandType` la valeur <xref:System.Data.CommandType> pour exécuter des instructions SQL ou la valeur <xref:System.Data.CommandType> pour exécuter des procédures stockées.  Ensuite, affectez comme valeur à la propriété `CommandText` une instruction SQL ou le nom de la procédure stockée.  Vous pouvez maintenant exécuter la commande de données en appelant l'une de ses méthodes d'exécution \(`ExecuteReader`, `ExecuteScalar`, `ExecuteNonQuery`\).  
  
 Chacun des [Fournisseurs de données .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md) propose un objet de commande optimisé pour les bases de données spécifiques.  
  
 En utilisant les commandes de données, vous pouvez effectuer les opérations suivantes dans votre application :  
  
-   Exécuter des commandes Select qui retournent directement des résultats directement lisibles plutôt que de le charger dans le groupe de données.  Pour lire les résultats, utilisez un lecteur de données \(objet <xref:System.Data.OleDb.OleDbDataReader>, <xref:System.Data.SqlClient.SqlDataReader>, <xref:System.Data.Odbc.OdbcDataReader> ou <xref:System.Data.OracleClient.OracleDataReader>\) qui fonctionne comme un curseur avant uniquement en lecture seule auquel vous pouvez lier des contrôles.  Cette stratégie est utile pour réduire la quantité de mémoire utilisée et pour charger des données en lecture seule très rapidement.  
  
-   Exécuter des commandes du langage de définition des données \(DDL\) pour créer, modifier et supprimer des tables, des procédures stockées et d'autres structures de base de données.  \(Vous devez bien sûr avoir l'autorisation d'effectuer ces opérations\).  
  
-   Exécuter des commandes pour obtenir des informations sur le catalogue de base de données.  
  
-   Exécuter des commandes SQL dynamiques pour mettre à jour, insérer et supprimer des enregistrements, plutôt que de mettre à jour des tables de groupe de données et de copier ensuite les modifications dans la base de données.  
  
-   Exécuter des commandes qui retournent une valeur scalaire \(c'est\-à\-dire une valeur unique\), telle que les résultats d'une fonction d'agrégation \(SUM, COUNT, AVG, etc.\).  
  
-   Exécuter des commandes qui retournent des données d'une base de données SQL Server \(version 7.0 ou ultérieure\) au format XML.  Une utilisation courante consiste, par exemple, à exécuter une requête et à récupérer les données au format XML, à leur appliquer une transformation XSLT \(pour les convertir en données HTML\), puis à envoyer les résultats à un navigateur.  
  
 Les propriétés d'une commande contiennent toutes les informations nécessaires pour exécuter cette commande sur une base de données.  Et notamment :  
  
-   **Une connexion** La commande référence une connexion qu'elle utilise pour communiquer avec la base de données.  
  
-   **Le nom ou le texte d'une commande** La commande contient le texte réel d'une instruction SQL ou le nom d'une procédure stockée à exécuter.  
  
-   **Des paramètres** Une commande peut requérir que vous passiez avec elle des valeurs de paramètre \(paramètres d'entrée\).  La commande peut également retourner des valeurs sous la forme d'une valeur de retour ou de valeurs de paramètres de sortie.  Chaque commande possède une collection de paramètres que vous pouvez définir ou lire individuellement pour passer ou recevoir des valeurs.  Pour plus d'informations, consultez [Comment : définir et obtenir des paramètres pour des objets de commande](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 Une commande est exécutée en utilisant une méthode adaptée aux résultats que vous vous attendez à obtenir.  Si, par exemple, vous attendez des lignes, appelez la méthode `ExecuteReader` de la commande, qui retourne des enregistrements dans un lecteur de données.  Si vous exécutez une commande UPDATE, INSERT ou DELETE, appelez la méthode `ExecuteNonQuery` de la commande, qui retourne une valeur indiquant le nombre de lignes affectées.  Si vous exécutez une fonction d'agrégation, telle que le retour du nombre de commandes d'un client, vous devez appeler la méthode `ExecuteScalar`.  
  
### Jeux de résultats multiples  
 Une utilisation standard d'un objet de commande consiste à retourner une table de données unique \(un jeu de lignes\).  Toutefois, les commandes peuvent aussi exécuter des procédures retournant plusieurs jeux de résultats.  Cela peut se produire de différentes manières.  Par exemple, la commande peut référencer une procédure stockée retournant plusieurs jeux de résultats.  Ou encore, elle peut contenir au moins deux noms d'instruction ou de procédure stockée.  Dans ce cas, les instructions ou les procédures sont exécutées séquentiellement et elles retournent des jeux de résultats multiples à l'aide d'un seul appel.  
  
 Si vous spécifiez plusieurs instructions ou procédures pour une commande, elles doivent toutes appartenir au même type.  Par exemple, vous pouvez exécuter plusieurs instructions SQL ou procédures stockées successives.  Toutefois, vous ne pouvez pas mélanger des appels de procédure stockée et des instructions SQL dans la même commande.  Pour plus d'informations, consultez [Extraction de données à l'aide d'un DataReader](../Topic/Retrieving%20Data%20Using%20a%20DataReader.md).  
  
> [!NOTE]
>  Pour Oracle, le fournisseur de données .NET Framework pour Oracle ne prend pas en charge les instructions SQL par lots.  Cependant, il permet l'utilisation de plusieurs paramètres de sortie REF CURSOR pour remplir un groupe de données, chacun dans sa propre table de données.  Vous devez définir les paramètres, les marquer comme paramètres de sortie, puis indiquer qu'il s'agit de types de données REF CURSOR.  Remarquez que vous ne pouvez pas utiliser la méthode `Update` lorsque l'objet <xref:System.Data.OracleClient.OracleDataAdapter> est rempli à partir de paramètres REF CURSOR vers une procédure stockée, car Oracle ne fournit pas les informations nécessaires pour déterminer le nom de la table et des colonnes lors de l'exécution de l'instruction SQL.  
  
## Sécurité  
 Lorsque vous utilisez des commandes de données avec une propriété `CommandType` possédant la valeur <xref:System.Data.CommandType>, vérifiez attentivement les informations envoyées par un client avant de les passer à la base de données.  Des utilisateurs malveillants peuvent tenter d'envoyer \(injecter\) des instructions SQL modifiées ou supplémentaires afin d'accéder à la base de données ou de l'endommager.  Avant de transférer la saisie d'un utilisateur vers une base de données, vous devez toujours vérifier la validité des informations.  Il est recommandé de toujours utiliser des requêtes ou des procédures stockées paramétrées lorsque cela est possible.  
  
## Voir aussi  
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)   
 [Outils permettant d'utiliser des sources de données dans Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)