---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de proc&#233;dures stock&#233;es de mise &#224; jour pour la table Customers de Northwind | Microsoft Docs"
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
  - "Northwind (exemple de base de données)"
  - "Concepteur O/R, procédures stockées"
  - "procédures stockées (Visual Studio)"
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de proc&#233;dures stock&#233;es de mise &#224; jour pour la table Customers de Northwind
Certaines rubriques d'aide de la documentation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] requièrent des procédures stockées supplémentaires dans l'exemple de base de données Northwind pour effectuer des mises à jour \(insertions, mises à jour et suppressions\) de données dans la table Customers.  
  
 Cette procédure pas à pas fournit des instructions pour créer ces procédures stockées supplémentaires dans les exemples de base de données Northwind pour [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].  
  
 La section Étapes suivantes, plus loin dans cette rubrique, fournit des liens vers les rubriques qui décrivent comment utiliser ces procédures stockées supplémentaires.  
  
 Pendant cette procédure pas à pas, vous allez apprendre à effectuer les tâches suivantes :  
  
-   créer une connexion de données à l'exemple de base de données Northwind ;  
  
-   créer les procédures stockées.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Accès à la version SQL Server de l'exemple de base de données Northwind.  Pour plus d'informations, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
## Connexion à la base de données Northwind  
 Cette procédure pas à pas requiert une connexion à la version SQL Server de la base de données Northwind.  La procédure suivante fournit des instructions pour créer la connexion de données.  
  
> [!NOTE]
>  Si vous disposez déjà d'une connexion de données à la base de données Northwind, vous pouvez passer à la section suivante, Création des procédures stockées.  
  
#### Pour créer une connexion de données à la base de données Northwind SQL Server  
  
1.  Dans le menu **Affichage**, choisissez **Explorateur de serveurs**\/**Explorateur de bases de données**.  
  
2.  Cliquez avec le bouton droit sur **Connexions de données** et cliquez sur **Ajouter une connexion**.  
  
3.  Dans la boîte de dialogue **Choisir la source de données**, cliquez sur **Microsoft SQL Server**, puis sur **OK**.  
  
     Si la boîte de dialogue **Ajouter une connexion** s'ouvre et que la **Source de données** n'est pas **Microsoft SQL Server \(SqlClient\)**, cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Choisir\/Modifier la source de données**, sur **Microsoft SQL Server**, puis sur **OK**.  
  
4.  Cliquez sur un **Nom de serveur** dans la liste déroulante ou tapez le nom du serveur sur lequel se trouve la base de données Northwind.  
  
5.  Selon les spécifications de la base de données ou de l'application, cliquez sur **Utiliser l'authentification Windows** ou utilisez un nom d'utilisateur spécifique et un mot de passe pour vous connecter à l'ordinateur exécutant SQL Server \(**Authentification SQL Server**\).  
  
6.  Cliquez sur la base de données Northwind dans la liste **Sélectionner ou entrer un nom de base de données**.  
  
7.  Cliquez sur **OK**.  
  
     La connexion de données est ajoutée à l'**Explorateur de serveurs**\/**Explorateur de bases de données**.  
  
## Création des procédures stockées  
 Créez les procédures stockées en exécutant le script SQL fourni sur la base de données Northwind à l'aide de [Visual Database Tools](http://msdn.microsoft.com/fr-fr/6b145922-2f00-47db-befc-bf351b4809a1), disponible dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**.  
  
#### Pour créer les procédures stockées à l'aide d'un script SQL  
  
1.  Développez la base de données Northwind dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**.  
  
2.  Cliquez avec le bouton droit sur le nœud **Procédures stockées** et cliquez sur **Ajouter la nouvelle procédure stockée**.  
  
3.  Collez le code suivant dans le l'Éditeur de code, en remplaçant le modèle `CREATE PROCEDURE` :  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  Sélectionnez tout le texte dans l'Éditeur de code, cliquez avec le bouton droit sur le texte sélectionné et cliquez sur **Exécuter la sélection**.  
  
     Les procédures stockées SelectCustomers, InsertCustomers, UpdateCustomers et DeleteCustomers sont créées pour la base de données Northwind.  
  
## Étapes suivantes  
 Maintenant que vous avez créé les procédures stockées, essayez les procédures pas à pas suivantes, qui décrivent comment les utiliser :  
  
 [Procédure : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions \(Concepteur O\/R\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)  
  
 [Procédure pas à pas : personnalisation du comportement d'insertion, de mise à jour et de suppression de classes d'entité](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## Voir aussi  
 [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)