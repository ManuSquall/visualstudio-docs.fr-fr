---
title: 'Procédure : Enregistrer des données dans une transaction'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ec2ff00c4d355b2683c888fcdb6a333bf15e1b99
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Procédure : Enregistrer des données dans une transaction
Cette procédure pas à pas montre comment enregistrer les données dans une transaction à l’aide de la <xref:System.Transactions> espace de noms. Dans cette procédure pas à pas, vous allez créer une application Windows Forms. L’Assistant Configuration de Source de données vous permet de créer un jeu de données pour les deux tables dans la base de données Northwind. Vous allez ajouter des contrôles liés aux données à un Windows form, et vous allez modifier le code de BindingNavigator bouton Enregistrer Mettre à jour la base de données à l’intérieur de TransactionScope.

## <a name="prerequisites"></a>Prérequis
Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peut être installé dans le cadre de la **développement de bureau .NET** charge de travail, ou sous la forme d’un composant individuel.

2.  Installer la base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez le **l’Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le programme d’installation Visual Studio.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête...** .

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée et la base de données Northwind est créé.

## <a name="create-a-windows-forms-application"></a>Créer une application Windows Forms
 La première étape consiste à créer un **Application Windows Forms**.

#### <a name="to-create-the-new-windows-project"></a>Pour créer un projet Windows

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau**, **projet...** .

2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **de bureau Windows classique**.

3. Dans le volet central, sélectionnez le **l’application Windows Forms** type de projet.

4. Nommez le projet **SavingDataInATransactionWalkthrough**, puis choisissez **OK**.

     Le **SavingDataInATransactionWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**.

## <a name="create-a-database-data-source"></a>Créer une source de données de base de données
 Cette étape utilise la **Assistant de Configuration de Source de données** pour créer une source de données basée sur la `Customers` et `Orders` les tables dans la base de données Northwind.

#### <a name="to-create-the-data-source"></a>Pour créer la source de données

1.  Sur le **données** menu, sélectionnez **afficher les Sources de données**.

2.  Dans le **des Sources de données** fenêtre, sélectionnez **ajouter une nouvelle Source de données** pour démarrer le **Assistant de Configuration de Source de données**.

3.  Sur le **choisir un Type de Source de données** écran, sélectionnez **base de données**, puis sélectionnez **suivant**.

4.  Sur le **choisir votre connexion de données** écran, procédez comme suit :

    -   Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

         - ou -

    -   Sélectionnez **nouvelle connexion** pour lancer le **Ajouter/modifier la connexion** boîte de dialogue zone et créer une connexion à la base de données Northwind.

5.  Si votre base de données requiert un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis sélectionnez **suivant**.

6.  Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** écran, sélectionnez **suivant**.

7.  Sur le **choisir vos objets de base de données** écran, développez le **Tables** nœud.

8.  Sélectionnez le `Customers` et `Orders` tables, puis sélectionnez **Terminer**.

     Le **NorthwindDataSet** est ajouté à votre projet et le `Customers` et `Orders` tables apparaissent dans le **des Sources de données** fenêtre.

## <a name="add-controls-to-the-form"></a>Ajouter des contrôles au formulaire
 Vous pouvez créer les contrôles liés aux données en faisant glisser des éléments depuis la **des Sources de données** fenêtre vers votre formulaire.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Pour créer des données liées à des contrôles sur le formulaire Windows

-   Dans le **des Sources de données** fenêtre, développez le **clients** nœud.

-   Faites glisser le **clients** nœud à partir de la **des Sources de données** fenêtre sur **Form1**.

     Un contrôle <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent dans le formulaire. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.

-   Faites glisser le **commandes** nœud (pas le principal **commandes** nœud, mais le nœud de la table enfant connexe ci-dessous le **télécopie** colonne) vers le formulaire sous la  **CustomersDataGridView**.

     Un <xref:System.Windows.Forms.DataGridView> s'affiche dans le formulaire. Un `OrdersTableAdapter` et <xref:System.Windows.Forms.BindingSource> s’affichent dans la barre d’état du composant.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Ajoutez une référence à l’assembly System.Transactions
 Les transactions utilisent l'espace de noms <xref:System.Transactions>. Une référence de project vers l'assembly system.transactions n'est pas ajoutée par défaut, vous devez donc l'ajouter manuellement.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Pour ajouter une référence au fichier DLL System.Transactions

1.  Sur le **projet** menu, sélectionnez **ajouter une référence**.

2.  Sélectionnez **System.Transactions** (sur le **.NET** onglet), puis sélectionnez **OK**.

     Une référence à **System.Transactions** est ajouté au projet.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Modifier le code du bouton SaveItem de BindingNavigator
 Pour la première table déposée dans votre formulaire, le code est ajouté par défaut pour le `click` bouton d’événement de l’enregistrement sur le <xref:System.Windows.Forms.BindingNavigator>. Vous devez manuellement ajouter du code pour mettre à jour toutes les tables supplémentaires. Pour cette procédure pas à pas, nous refactoriser le code en dehors de l’enregistrement d’enregistrement existant Gestionnaire d’événements de clic du bouton. Nous avons également créer quelques méthodes supplémentaires pour fournir la fonctionnalité de mise à jour spécifique selon si la ligne doit être ajouté ou supprimé.

#### <a name="to-modify-the-auto-generated-save-code"></a>Pour modifier le code d'enregistrement généré automatiquement

1.  Sélectionnez le **enregistrer** bouton sur le **CustomersBindingNavigator** (le bouton avec l’icône de disquette).

2.  Remplacez la méthode `CustomersBindingNavigatorSaveItem_Click` par le code suivant :

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

L'ordre de rapprochement des modifications des données associées est comme suit :

-   Suppression des enregistrements enfants. (Dans ce cas, supprimer des enregistrements de la `Orders` table.)

-   Suppression des enregistrements parents. (Dans ce cas, supprimer des enregistrements de la `Customers` table.)

-   Insertion des enregistrements parents. (Dans ce cas, insérer des enregistrements dans la `Customers` table.)

-   Insertion des enregistrements enfants. (Dans ce cas, insérer des enregistrements dans la `Orders` table.)

#### <a name="to-delete-existing-orders"></a>Pour supprimer des commandes existantes

-   Ajoutez le code suivant `DeleteOrders` méthode **Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

#### <a name="to-delete-existing-customers"></a>Pour supprimer des clients existants

-   Ajoutez le code suivant `DeleteCustomers` méthode **Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

#### <a name="to-add-new-customers"></a>Pour ajouter de nouveaux clients

-   Ajoutez le code suivant `AddNewCustomers` méthode **Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

#### <a name="to-add-new-orders"></a>Pour ajouter de nouvelles commandes

-   Ajoutez le code suivant `AddNewOrders` méthode **Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Exécuter l'application

#### <a name="to-run-the-application"></a>Pour exécuter l’application

-   Sélectionnez **F5** pour exécuter l’application.

## <a name="see-also"></a>Voir aussi

- [Comment : enregistrer des données à l’aide d’une transaction](../data-tools/save-data-by-using-a-transaction.md)
- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)