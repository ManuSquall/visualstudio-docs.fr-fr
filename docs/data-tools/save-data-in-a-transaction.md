---
title: 'Procédure pas à pas : enregistrer des données dans une transaction'
description: Dans cette procédure pas à pas, consultez Comment enregistrer des données dans une transaction à l’aide de l’espace de noms System. transactions dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1bb0262139e2096cf55ae7581ef854a57c67d22a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434543"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Procédure pas à pas : enregistrer des données dans une transaction

Cette procédure pas à pas montre comment enregistrer des données dans une transaction à l’aide de l' <xref:System.Transactions> espace de noms. Dans cette procédure pas à pas, vous allez créer une application Windows Forms. Vous allez utiliser l’Assistant Configuration de source de données pour créer un jeu de données pour deux tables de l’exemple de base de données Northwind. Vous allez ajouter des contrôles liés aux données à un Windows Form et modifier le code du bouton enregistrer du BindingNavigator pour mettre à jour la base de données à l’intérieur d’une TransactionScope.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express base de données locale et l’exemple de base de données Northwind.

1. Si vous n’avez pas SQL Server Express base de données locale, installez-la à partir de la [page de téléchargement SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)ou via le **Visual Studio installer**. Dans le Visual Studio Installer, SQL Server Express base de données locale peut être installée dans le cadre de la charge de travail **développement .net Desktop** , ou en tant que composant individuel.

2. Installez l’exemple de base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez la fenêtre de **Explorateur d’objets SQL Server** . (Explorateur d’objets SQL Server est installé dans le cadre de la charge de travail **stockage et traitement des données** dans le Visual Studio installer.) Développez le nœud **SQL Server** . Cliquez avec le bouton droit sur votre instance de base de données locale, puis sélectionnez **nouvelle requête**.

       Une fenêtre de l’éditeur de requête s’ouvre.

    2. Copiez le [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le bouton **exécuter** .

       Après un bref laps de temps, l’exécution de la requête se termine et la base de données Northwind est créée.

## <a name="create-a-windows-forms-application"></a>Créer une application Windows Forms

La première étape consiste à créer une **Application Windows Forms**.

1. Dans Visual Studio, dans le menu **Fichier** , sélectionnez **Nouveau** > **Projet**.

2. Développez **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **Bureau Windows**.

3. Dans le volet central, sélectionnez le type de projet d' **application Windows Forms** .

4. Nommez le projet **SavingDataInATransactionWalkthrough** , puis choisissez **OK**.

     Le projet **SavingDataInATransactionWalkthrough** est créé et ajouté à l’ **Explorateur de solutions**.

## <a name="create-a-database-data-source"></a>Créer une source de données de base de données

Cette étape utilise l' **Assistant Configuration de source de données** pour créer une source de données basée sur les `Customers` `Orders` tables et de l’exemple de base de données Northwind.

1. Pour ouvrir la fenêtre **sources de données** , dans le menu **données** , sélectionnez Afficher les **sources de données**.

2. Dans la fenêtre **Sources de données** , sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’ **Assistant Configuration de source de données**.

3. Dans l’écran **choisir un type de source de données** , sélectionnez **base de** données, puis sélectionnez **suivant**.

4. Dans l’écran **choisir votre connexion de données** , effectuez l’une des opérations suivantes :

    - Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

         - ou -

    - Sélectionnez **Nouvelle connexion** pour lancer la boîte de dialogue **Ajouter/Modifier une connexion** et créez une connexion à la base de données Northwind.

5. Si votre base de données requiert un mot de passe, sélectionnez l’option permettant d’inclure des données sensibles, puis sélectionnez **suivant**.

6. Sur la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , sélectionnez **suivant**.

7. Dans l’écran **choisir vos objets de base de données** , développez le nœud **tables** .

8. Sélectionnez les `Customers` `Orders` tables et, puis sélectionnez **Terminer**.

     **NorthwindDataSet** est ajouté à votre projet et les tables `Customers` et `Orders` apparaissent dans la fenêtre **Sources de données**.

## <a name="add-controls-to-the-form"></a>Ajouter des contrôles au formulaire

Vous pouvez créer les contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **sources de données** vers votre formulaire.

1. Dans la fenêtre **sources de données** , développez le nœud **Customers** .

2. Faites glisser le nœud **Customers** depuis la fenêtre **Sources de données** vers **Form1**.

   Un contrôle <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent dans le formulaire. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> apparaissent dans la barre d’état des composants.

3. Faites glisser le nœud **Orders** associé (pas le nœud **Orders** principal, mais le nœud de la table enfant connexe sous la colonne **Fax** ) vers le formulaire sous **CustomersDataGridView**.

   Un <xref:System.Windows.Forms.DataGridView> s'affiche dans le formulaire. `OrdersTableAdapter`Et <xref:System.Windows.Forms.BindingSource> apparaissent dans la barre d’état des composants.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Ajouter une référence à l’assembly System. transactions

Les transactions utilisent l’espace de noms <xref:System.Transactions>. Une référence de project vers l'assembly system.transactions n'est pas ajoutée par défaut, vous devez donc l'ajouter manuellement.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Pour ajouter une référence au fichier DLL System.Transactions

1. Dans le menu **Projet** , sélectionnez **Ajouter une référence**.

2. Sélectionnez **System. transactions** (sous l’onglet **.net** ), puis sélectionnez **OK**.

     Une référence à **System.Transactions** est ajoutée au projet.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Modifier le code dans le bouton SaveItem du BindingNavigator

Pour la première table déplacée dans votre formulaire, du code est ajouté par défaut à l' `click` événement du bouton enregistrer sur le <xref:System.Windows.Forms.BindingNavigator> . Vous devez manuellement ajouter du code pour mettre à jour toutes les tables supplémentaires. Pour cette procédure pas à pas, nous refactorisons le code d’enregistrement existant en dehors du gestionnaire d’événements Click du bouton enregistrer. Nous créons également quelques méthodes supplémentaires pour fournir une fonctionnalité de mise à jour spécifique selon que la ligne doit être ajoutée ou supprimée.

### <a name="to-modify-the-auto-generated-save-code"></a>Pour modifier le code d'enregistrement généré automatiquement

1. Sélectionnez le bouton **Enregistrer** sur le **CustomersBindingNavigator** (le bouton avec l’icône de disquette).

2. Remplacez la méthode `CustomersBindingNavigatorSaveItem_Click` par le code suivant :

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

L'ordre de rapprochement des modifications des données associées est comme suit :

- Supprimer les enregistrements enfants. (Dans ce cas, supprimez les enregistrements de la `Orders` table.)

- Supprimer les enregistrements parents. (Dans ce cas, supprimez les enregistrements de la `Customers` table.)

- Insérez les enregistrements parents. (Dans ce cas, insérez des enregistrements dans la `Customers` table.)

- Insérer des enregistrements enfants. (Dans ce cas, insérez des enregistrements dans la `Orders` table.)

### <a name="to-delete-existing-orders"></a>Pour supprimer des commandes existantes

- Ajoutez la méthode `DeleteOrders` suivante à **Form1**  :

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>Pour supprimer des clients existants

- Ajoutez la méthode `DeleteCustomers` suivante à **Form1**  :

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>Pour ajouter de nouveaux clients

- Ajoutez la méthode `AddNewCustomers` suivante à **Form1**  :

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>Pour ajouter de nouvelles commandes

- Ajoutez la méthode `AddNewOrders` suivante à **Form1**  :

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Exécution de l'application

Appuyez sur **F5** pour exécuter l'application.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour enregistrer des données avec une transaction](../data-tools/save-data-by-using-a-transaction.md)
- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
