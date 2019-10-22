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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bef7c4be2f38d0f50b2a13c7745cb212204769b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670089"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Créer une base de données SQL à l’aide d’un script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous utilisez Visual Studio pour créer une petite base de données qui contient l’exemple de code pour [créer une application de données simple à l’aide de ADO.net](../data-tools/create-a-simple-data-application-by-using-adonet.md).

 **Dans cette rubrique**

- [Créer un script qui contient un schéma de base de données](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)

- [Créer un projet de base de données et importer un schéma](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)

- [Déployer la base de données](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)

## <a name="prerequisites"></a>Configuration requise
 Pour effectuer cette procédure pas à pas, vous devez disposer de SQL Server Express base de données locale ou d’une autre base de données SQL installée.

## <a name="CreateScript"></a>Créer un script qui contient un schéma de base de données

#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Pour créer un script à partir duquel vous pouvez importer un schéma

1. Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], dans la barre de menus, sélectionnez **fichier**  > **nouveau**  > **fichier**.

     La boîte **de dialogue nouveau fichier** s’affiche.

2. Dans la liste **catégories** , sélectionnez **général**.

3. Dans la liste **modèles** , sélectionnez **fichier SQL**, puis cliquez sur le bouton **ouvrir** .

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

5. Dans la barre de menus, sélectionnez **fichier**  > **Enregistrer SqlQuery_1. SQL sous**.

     La boîte de dialogue **enregistrer le fichier sous** s’affiche.

6. Dans la zone **nom de fichier** , entrez `SampleImportScript.sql`, notez l’emplacement où vous allez enregistrer le fichier, puis sélectionnez le bouton **Enregistrer** .

7. Dans la barre de menus, sélectionnez **fichier**  > **Fermer la solution**.

     Ensuite, créez un projet de base de données, puis importez le schéma à partir du script que vous avez créé.

## <a name="CreateProject"></a>Créer un projet de base de données et importer un schéma

#### <a name="to-create-a-database-project"></a>Pour créer un projet de base de données

1. Dans la barre de menus, sélectionnez **Fichier** > **Nouveau** > **Projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

2. Sous **installé**, développez le nœud **modèles** , développez le nœud **autres langages** , sélectionnez la catégorie **SQL Server** , puis sélectionnez le modèle **de projet de base de données SQL Server** .

    > [!NOTE]
    > Le nœud **autres langages** n’apparaît pas dans toutes les installations de Visual Studio.

3. Dans la zone **nom** , entrez `Small Database`.

4. Activez la case à cocher **créer le répertoire pour la solution** si elle n’est pas déjà sélectionnée.

5. Désactivez la case à cocher **Ajouter au contrôle de code source** si elle n’est pas déjà désactivée, puis sélectionnez le bouton **OK** .

     Le projet de base de données est créé et s’affiche dans **Explorateur de solutions**.

     Ensuite, importez le schéma de base de données à partir du script.

#### <a name="to-import-a-database-schema-from-a-script"></a>Pour importer un schéma de base de données à partir d’un script

1. Dans la barre de menus, sélectionnez **projet**  > **Importer**  > **script**.

2. Dans la page **Bienvenue** , examinez le texte, puis sélectionnez le bouton **suivant** .

3. Sélectionnez la case d’option **fichier unique** , puis cliquez sur le bouton **Parcourir** .

     La boîte de dialogue **Importer un script SQL** s’affiche.

4. Ouvrez le dossier dans lequel vous avez enregistré le fichier SampleImportScript. SQL, sélectionnez le fichier, puis sélectionnez le bouton **ouvrir** .

5. Sélectionnez le bouton **Terminer** pour fermer la boîte de dialogue **Importer un script SQL** .

     Le script est importé, et les objets définis par le script sont ajoutés à votre projet de base de données.

6. Passez en revue le résumé, puis cliquez sur le bouton **Terminer** pour fermer la boîte de dialogue **Importer un fichier de script SQL** .

7. Dans **Explorateur de solutions**, développez les dossiers Sales, scripts et Security de votre projet, puis vérifiez qu’ils contiennent des fichiers. Sql.

8. Dans **Explorateur d’objets SQL Server**, vérifiez que la base de données apparaît sous le nœud **projets** .

     À ce stade, la base de données contient uniquement des objets système, tels que des tables et des procédures stockées. Une fois la base de données déployée, elle contient les tables utilisateur et les procédures stockées que les scripts définissent.

## <a name="DeployDatabase"></a>Déployer la base de données
 Lorsque vous appuyez sur la touche **F5** , vous déployez (ou publiez) la base de données dans une base de données de base de données locale par défaut. Vous pouvez déployer la base de données à un autre emplacement en ouvrant la page de propriétés du projet, en sélectionnant l’onglet **Déboguer** , puis en modifiant la chaîne de connexion.
