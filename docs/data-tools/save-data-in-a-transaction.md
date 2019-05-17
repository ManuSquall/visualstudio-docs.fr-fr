---
title: 'Procédure pas à pas : Enregistrer des données dans une transaction'
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ea312ca2858a02bc8a70c3e41dbb525c9d222adc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565715"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Procédure pas à pas : Enregistrer des données dans une transaction

Cette procédure pas à pas montre comment enregistrer des données dans une transaction à l’aide de la <xref:System.Transactions> espace de noms. Dans cette procédure pas à pas, vous allez créer une application Windows Forms. Vous utiliserez l’Assistant de Configuration de Source de données pour créer un jeu de données pour les deux tables dans la base de données Northwind. Vous allez ajouter des contrôles liés aux données à un formulaire Windows, et vous allez modifier le code de BindingNavigator bouton Enregistrer Mettre à jour de la base de données à l’intérieur d’un TransactionScope.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1. Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peuvent être installé dans le cadre de la **développement .NET desktop** charge de travail, ou comme un composant individuel.

2. Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans Visual Studio Installer.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée en cours d’exécution et la base de données Northwind est créé.

## <a name="create-a-windows-forms-application"></a>Créer une application Windows Forms

La première étape consiste à créer un **Windows Forms Application**.

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **New** > **projet**.

2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **Windows Desktop**.

3. Dans le volet central, sélectionnez le **Windows Forms application** type de projet.

4. Nommez le projet **SavingDataInATransactionWalkthrough**, puis choisissez **OK**.

     Le projet **SavingDataInATransactionWalkthrough** est créé et ajouté à l’**Explorateur de solutions**.

## <a name="create-a-database-data-source"></a>Créer une source de données de base de données

Cette étape utilise le **Assistant de Configuration de Source de données** pour créer une source de données basée sur le `Customers` et `Orders` tables dans la base de données Northwind.

1. Pour ouvrir le **des Sources de données** fenêtre, dans le **données** menu, sélectionnez **afficher les Sources de données**.

2. Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’**Assistant Configuration de source de données**.

3. Sur le **choisir un Type de Source de données** s’affiche, sélectionnez **base de données**, puis sélectionnez **suivant**.

4. Sur le **choisir votre connexion de données** écran, procédez comme suit :

    - Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

         - ou -

    - Sélectionnez **Nouvelle connexion** pour lancer la boîte de dialogue **Ajouter/Modifier une connexion** et créez une connexion à la base de données Northwind.

5. Si votre base de données requiert un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis sélectionnez **suivant**.

6. Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** s’affiche, sélectionnez **suivant**.

7. Sur le **choisir vos objets de base de données** écran, développez le **Tables** nœud.

8. Sélectionnez le `Customers` et `Orders` tables, puis sélectionnez **Terminer**.

     **NorthwindDataSet** est ajouté à votre projet et les tables `Customers` et `Orders` apparaissent dans la fenêtre **Sources de données**.

## <a name="add-controls-to-the-form"></a>Ajouter des contrôles au formulaire

Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers votre formulaire.

1. Dans le **des Sources de données** fenêtre, développez le **clients** nœud.

2. Faites glisser le nœud **Customers** depuis la fenêtre **Sources de données** vers **Form1**.

   Un contrôle <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent dans le formulaire. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.

3. Faites glisser le **commandes** nœud (pas le principal **commandes** nœud, mais le nœud de table enfant associé ci-dessous le **télécopie** colonne) vers le formulaire sous la  **CustomersDataGridView**.

   Un <xref:System.Windows.Forms.DataGridView> s'affiche dans le formulaire. Un `OrdersTableAdapter` et <xref:System.Windows.Forms.BindingSource> s’affichent dans la barre d’état du composant.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Ajoutez une référence à l’assembly System.Transactions

Les transactions utilisent l’espace de noms <xref:System.Transactions>. Une référence de project vers l'assembly system.transactions n'est pas ajoutée par défaut, vous devez donc l'ajouter manuellement.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Pour ajouter une référence au fichier DLL System.Transactions

1. Sur le **projet** menu, sélectionnez **ajouter une référence**.

2. Sélectionnez **System.Transactions** (sur le **.NET** onglet), puis sélectionnez **OK**.

     Une référence à **System.Transactions** est ajoutée au projet.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Modifier le code du bouton SaveItem de BindingNavigator

Pour la première table déposée dans votre formulaire, le code est ajouté par défaut pour le `click` événement de sauvegarde situé dans le <xref:System.Windows.Forms.BindingNavigator>. Vous devez manuellement ajouter du code pour mettre à jour toutes les tables supplémentaires. Pour cette procédure pas à pas, nous refactoriser le code en dehors de l’enregistrement d’enregistrement existant de clic du bouton Gestionnaire d’événements. Nous créons également quelques méthodes supplémentaires pour fournir des fonctionnalités de mise à jour spécifique en fonction de si la ligne doit être ajouté ou supprimé.

### <a name="to-modify-the-auto-generated-save-code"></a>Pour modifier le code d'enregistrement généré automatiquement

1. Sélectionnez le **enregistrer** bouton sur le **CustomersBindingNavigator** (le bouton avec l’icône de disquette).

2. Remplacez la méthode `CustomersBindingNavigatorSaveItem_Click` par le code suivant :

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

L'ordre de rapprochement des modifications des données associées est comme suit :

- Supprimer des enregistrements enfants. (Dans ce cas, supprimer des enregistrements de la `Orders` table.)

- Supprimer des enregistrements parents. (Dans ce cas, supprimer des enregistrements de la `Customers` table.)

- Insérer des enregistrements parents. (Dans ce cas, insérer des enregistrements dans la `Customers` table.)

- Insérer des enregistrements enfants. (Dans ce cas, insérer des enregistrements dans la `Orders` table.)

### <a name="to-delete-existing-orders"></a>Pour supprimer des commandes existantes

- Ajoutez la méthode `DeleteOrders` suivante à **Form1** :

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>Pour supprimer des clients existants

- Ajoutez la méthode `DeleteCustomers` suivante à **Form1** :

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>Pour ajouter de nouveaux clients

- Ajoutez la méthode `AddNewCustomers` suivante à **Form1** :

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>Pour ajouter de nouvelles commandes

- Ajoutez la méthode `AddNewOrders` suivante à **Form1** :

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Exécuter l'application

Appuyez sur **F5** pour exécuter l’application.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour enregistrer des données avec une transaction](../data-tools/save-data-by-using-a-transaction.md)
- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)