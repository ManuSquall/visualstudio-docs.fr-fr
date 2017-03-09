---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un petit exemple de base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un petit exemple de base de donn&#233;es
Dans cette procédure pas à pas, vous utilisez Visual Studio pour créer une petite base de données qui contient l'exemple de code pour [Procédure pas à pas : création d'une application de données simple à l'aide d'ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **Dans cette rubrique**  
  
-   [Créer un script qui contient un schéma de base de données](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [Créer un projet de base de données et importer un schéma](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [Déployer la base de données](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez avoir installé [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  Vous devez pouvoir vous connecter à un serveur de base de données ou à une base de données LocalDB pour laquelle vous disposez des autorisations de création et de déploiement d'une base de données.  
  
##  <a name="CreateScript"></a> Créer un script qui contient un schéma de base de données  
  
#### Pour créer un script duquel vous pouvez importer un schéma  
  
1.  Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], dans la barre de menus, choisissez **Fichier**, **Nouveau**, **Fichier**.  
  
     La boîte de dialogue **Nouveau fichier** s'affiche.  
  
2.  Dans la liste **Catégories**, choisissez **Général**.  
  
3.  Dans la liste **Modèles**, sélectionnez **Fichier SQL**, puis cliquez sur le bouton **Ouvrir**.  
  
     L'éditeur Transact\-SQL apparaît.  
  
4.  Copiez le code Transact\-SQL suivant et collez\-le dans l'éditeur Transact\-SQL.  
  
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
  
5.  Dans la barre de menus, sélectionnez **Fichier**, puis cliquez sur **Enregistrer SqlQuery\_1.sql sous**.  
  
     La boîte de dialogue **Enregistrer le fichier sous** apparaît.  
  
6.  Dans la zone **Nom de fichier**, entrez `SampleImportScript.sql`, notez l'emplacement où vous enregistrerez le fichier, puis cliquez sur le bouton **Enregistrer**.  
  
7.  Dans la barre de menus, choisissez **Fichier**, **Fermer la solution**.  
  
     Créez ensuite un projet de base de données, puis importez le schéma depuis le script que vous avez créé.  
  
##  <a name="CreateProject"></a> Créer un projet de base de données et importer un schéma  
  
#### Pour créer un projet de base de données  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Sous **Installé**, développez le nœud **Modèles**, développez le nœud **Autres langages**, sélectionnez la catégorie **SQL Server**, puis choisissez le modèle **Projet de base de données SQL Server**.  
  
    > [!NOTE]
    >  Le nœud **Autres langages** n'apparaît pas dans toutes les installations de Visual Studio.  
  
3.  Dans la zone **Nom**, entrez `Petite base de données`.  
  
4.  Activez la case à cocher **Créer le répertoire pour la solution** si elle ne l'est pas déjà.  
  
5.  Désactivez la case à cocher **Ajouter au contrôle de code source** si elle ne l'est pas déjà, puis cliquez sur le bouton **OK**.  
  
     Le projet de base de données est créé et s'affiche dans l'**Explorateur de solutions**.  
  
     Importez ensuite le schéma de base de données à partir du script.  
  
#### Pour importer un schéma de base de données à partir d'un script  
  
1.  Dans la barre de menus, choisissez **Projet**, **Importer**, **Script**.  
  
2.  Dans la page d'accueil, examinez le texte, puis choisissez le bouton **Suivant**.  
  
3.  Sélectionnez la case d'option **Fichier unique**, puis choisissez le bouton **Parcourir**.  
  
     La boîte de dialogue **Importation de fichier de script SQL** s'affiche.  
  
4.  Ouvrez le dossier où vous avez enregistré le fichier SampleImportScript.sql, choisissez\-le, puis choisissez le bouton **Ouvrir**.  
  
5.  Cliquez sur le bouton **Terminer** pour fermer la boîte de dialogue **Importer le script SQL**.  
  
     Le script est importé, et les objets définis par le script sont ajoutés à votre projet de base de données.  
  
6.  Passez en revue les informations résumées, puis choisissez le bouton **Terminer** pour fermer la boîte de dialogue **Importation de fichier de script SQL**.  
  
7.  Dans l'**Explorateur de solutions**, développez les dossiers Sales, Scripts et Security de votre projet et vérifiez qu'ils contiennent les fichiers .sql.  
  
8.  Dans l'**Explorateur d'objets SQL Server**, vérifiez que la base de données apparaît sous le nœud **Projets**.  
  
     À ce stade, la base de données contient uniquement des objets système, tels que des tables et des procédures stockées.  Après avoir déployé la base de données, elle contiendra les tables utilisateur et les procédures stockées que les scripts définissent.  
  
##  <a name="DeployDatabase"></a> Déployer la base de données  
 Lorsque vous appuyez sur la touche F5, vous déployez \(ou publiez\) la base de données vers une base de données LocalDB par défaut.  Vous pouvez déployer la base de données sur un emplacement différent en ouvrant la page de propriétés du projet, en sélectionnant l'onglet **Déboguer**, puis en modifiant la chaîne de connexion.