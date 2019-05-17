---
title: Créer une base de données SQL à l’aide d’un script | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7c0dc7b406f7e04aaa9848e2f5dcb96f17430f6d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436958"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Créer une base de données SQL à l’aide d’un script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous utilisez Visual Studio pour créer une petite base de données qui contient l’exemple de code [créer une application de données simple à l’aide d’ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **Dans cette rubrique**  
  
- [Créer un script qui contient un schéma de base de données](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
- [Créez un projet de base de données et importer un schéma](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
- [Déployer la base de données](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure pas à pas, vous devez disposer de SQL Server Express LocalDB, ou une autre base de données SQL, installé.  
  
## <a name="CreateScript"></a> Créer un script qui contient un schéma de base de données  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Pour créer un script à partir de laquelle vous pouvez importer un schéma  
  
1. Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], dans la barre de menus, sélectionnez **fichier** > **New** > **fichier**.  
  
     Le **nouveau fichier** boîte de dialogue s’affiche.  
  
2. Dans le **catégories** liste, sélectionnez **général**.  
  
3. Dans le **modèles** liste, sélectionnez **fichier Sql**, puis sélectionnez le **Open** bouton.  
  
     L’éditeur Transact-SQL s’ouvre.  
  
4. Copiez le code Transact-SQL suivant, puis collez-le dans l’éditeur Transact-SQL.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5. Dans la barre de menus, sélectionnez **fichier** > **Enregistrer SqlQuery_1.sql sous**.  
  
     Le **enregistrer le fichier sous** boîte de dialogue s’affiche.  
  
6. Dans le **nom de fichier** , entrez `SampleImportScript.sql`, notez l’emplacement où vous allez enregistrer le fichier, puis sélectionnez le **enregistrer** bouton.  
  
7. Dans la barre de menus, sélectionnez **fichier** > **fermer la Solution**.  
  
     Ensuite, créez un projet de base de données, puis importez le schéma à partir du script que vous avez créée.  
  
## <a name="CreateProject"></a> Créez un projet de base de données et importer un schéma  
  
#### <a name="to-create-a-database-project"></a>Pour créer un projet de base de données  
  
1. Dans la barre de menus, sélectionnez **Fichier** > **Nouveau** > **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
2. Sous **installé**, développez le **modèles** nœud, développez le **autres langages** nœud, sélectionnez le **SQL Server** catégorie, puis Sélectionnez le **projet de base de données SQL Server** modèle.  
  
    > [!NOTE]
    > Le **autres langages** nœud n’apparaît pas dans toutes les installations de Visual Studio.  
  
3. Dans le **nom** , entrez `Small Database`.  
  
4. Sélectionnez le **créer le répertoire pour la solution** case à cocher s’il n’est pas déjà sélectionné.  
  
5. Effacer la **ajouter au contrôle de code source** case à cocher si elle n’est pas déjà effacés, puis sélectionnez le **OK** bouton.  
  
     Le projet de base de données est créé et apparaît dans **l’Explorateur de solutions**.  
  
     Ensuite, importez le schéma de base de données à partir du script.  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>Pour importer un schéma de base de données à partir d’un script  
  
1. Dans la barre de menus, sélectionnez **projet** > **importation** > **Script**.  
  
2. Sur le **Bienvenue** page, passez en revue le texte, puis sélectionnez le **suivant** bouton.  
  
3. Sélectionnez le **seul fichier** case d’option, puis sélectionnez le **Parcourir** bouton.  
  
     Le **importer le Script SQL** boîte de dialogue s’affiche.  
  
4. Ouvrez le dossier où vous avez enregistré le fichier SampleImportScript.sql, sélectionnez le fichier, puis le **Open** bouton.  
  
5. Sélectionnez le **Terminer** bouton pour fermer la **importer le Script SQL** boîte de dialogue.  
  
     Le script est importé, et les objets définis par le script sont ajoutés à votre projet de base de données.  
  
6. Passez en revue le résumé, puis cliquez sur le **Terminer** bouton pour fermer la **importation de fichier de Script SQL** boîte de dialogue.  
  
7. Dans **l’Explorateur de solutions**, développez le Sales, Scripts et la sécurité des dossiers de votre projet et vérifiez qu’ils contiennent des fichiers .sql.  
  
8. Dans **Explorateur d’objets SQL Server**, vérifiez que la base de données apparaît sous le **projets** nœud.  
  
     À ce stade, la base de données contient uniquement des objets système, tels que les tables et procédures stockées. Après avoir déployé la base de données, il contiendra les tables utilisateur et les procédures stockées qui définissent les scripts.  
  
## <a name="DeployDatabase"></a> Déployer la base de données  
 Quand vous appuyez sur la **F5** clé, vous déployez (ou publiez) la base de données à une base de données de base de données locale par défaut. Vous pouvez déployer la base de données vers un autre emplacement en ouvrant la page de propriétés pour le projet, en sélectionnant le **déboguer** onglet, puis en modifiant la chaîne de connexion.
