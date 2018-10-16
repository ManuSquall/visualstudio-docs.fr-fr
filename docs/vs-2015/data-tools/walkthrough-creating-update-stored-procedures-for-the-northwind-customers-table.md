---
title: 'Procédure pas à pas : Mise à jour de création de procédures stockées pour la Table Customers de Northwind | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Northwind sample database
- stored procedures [Visual Studio]
- O/R Designer, stored procedures
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4972c1341490f78bba03bdd390ac13903c55be84
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204046"
---
# <a name="walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table"></a>Procédure pas à pas : création de procédures stockées de mise à jour pour la table Customers de Northwind
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Certaines rubriques d’aide dans le [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] documentation nécessitent des procédures stockées supplémentaires dans la base de données Northwind pour effectuer des mises à jour (insertions, mises à jour et suppressions) de données dans la table Customers.  
  
 Cette procédure pas à pas fournit des instructions pour créer ces procédures stockées supplémentaires dans les exemples de base de données Northwind pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 La section Étapes suivantes, plus loin dans cette rubrique, fournit des liens vers les rubriques qui décrivent comment utiliser ces procédures stockées supplémentaires.  
  
 Pendant cette procédure pas à pas, vous allez apprendre à effectuer les tâches suivantes :  
  
-   créer une connexion de données à l'exemple de base de données Northwind ;  
  
-   créer les procédures stockées.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Accès à la version SQL Server de l'exemple de base de données Northwind. Pour plus d’informations, consultez [Comment : installer Sample Databases](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="connecting-to-the-northwind-database"></a>Connexion à la base de données Northwind  
 Cette procédure pas à pas requiert une connexion à la version SQL Server de la base de données Northwind. La procédure suivante fournit des instructions pour créer la connexion de données.  
  
> [!NOTE]
>  Si vous disposez déjà d'une connexion de données à la base de données Northwind, vous pouvez passer à la section suivante, Création des procédures stockées.  
  
#### <a name="to-create-a-data-connection-to-the-northwind-sql-server-database"></a>Pour créer une connexion de données à la base de données Northwind SQL Server  
  
1.  Sur le **vue** menu, cliquez sur **Explorateur de serveurs**/**Database Explorer**.  
  
2.  Avec le bouton droit **des connexions de données** et cliquez sur **ajouter une connexion**.  
  
3.  Dans le **choisir la Source de données** boîte de dialogue, cliquez sur **Microsoft SQL Server**, puis cliquez sur **OK**.  
  
     Si le **ajouter une connexion** boîte de dialogue s’ouvre et le **source de données** n’est pas **Microsoft SQL Server (SqlClient)**, cliquez sur **modification** pour ouvrir le **Choisir/Modifier la Source de données** boîte de dialogue, cliquez sur **Microsoft SQL Server**, puis cliquez sur **OK**.  
  
4.  Cliquez sur un **nom du serveur** dans la liste déroulante liste ou tapez le nom du serveur sur lequel se trouve la base de données Northwind.  
  
5.  En fonction des exigences de la base de données ou d’une application, cliquez sur **utiliser l’authentification Windows** ou utilisez un nom d’utilisateur spécifique et un mot de passe pour vous connecter à l’ordinateur exécutant SQL Server (**del’authentificationSQLServer**).  
  
6.  Cliquez sur la base de données Northwind dans la **sélectionner ou entrer un nom de base de données** liste.  
  
7.  Cliquez sur **OK**.  
  
     La connexion de données est ajoutée à **Explorateur de serveurs**/**Database Explorer**.  
  
## <a name="creating-the-stored-procedures"></a>Création des procédures stockées  
 Créer les procédures stockées en exécutant le script SQL fourni par rapport à la base de données Northwind à l’aide de la [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) disponible dans **Explorateur de serveurs** /  **Explorateur de base de données**.  
  
#### <a name="to-create-the-stored-procedures-by-using-a-sql-script"></a>Pour créer les procédures stockées à l'aide d'un script SQL  
  
1.  Développez la base de données Northwind dans **Explorateur de serveurs**/**Database Explorer**.  
  
2.  Avec le bouton droit le **Stored Procedures** nœud et cliquez sur **ajouter une nouvelle procédure stockée**.  
  
3.  Collez le code suivant dans le l'Éditeur de code, en remplaçant le modèle `CREATE PROCEDURE` :  
  
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
  
4.  Sélectionnez tout le texte dans l’éditeur de Code, cliquez sur le texte sélectionné et cliquez sur **exécuter la sélection**.  
  
     Les procédures stockées SelectCustomers, InsertCustomers, UpdateCustomers et DeleteCustomers sont créées pour la base de données Northwind.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez créé les procédures stockées, essayez les procédures pas à pas suivantes, qui décrivent comment les utiliser :  
  
 [Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)  
  
 [Procédure pas à pas : personnalisation du comportement d’insertion, de mise à jour et de suppression de classes d’entité](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)