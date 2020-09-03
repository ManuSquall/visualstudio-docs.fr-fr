---
title: Enregistrer des données dans une transaction | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30f51da001c62166a97c954b1416e35fd8b540f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671088"
---
# <a name="save-data-in-a-transaction"></a>Enregistrer des données dans une transaction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment enregistrer des données dans une transaction à l’aide de l' <xref:System.Transactions> espace de noms. Cet exemple utilise les tables `Customers` et `Orders` de l'exemple de base de données Northwind.

## <a name="prerequisites"></a>Prérequis
 Cette procédure pas à pas requiert un accès à l'exemple de base de données Northwind.

## <a name="create-a-windows-application"></a>Créer une application Windows
 La première étape consiste à créer une **application Windows**.

#### <a name="to-create-the-new-windows-project"></a>Pour créer un projet Windows

1. Dans Visual Studio, dans le menu **fichier** , créez un nouveau **projet**.

2. Nommez le projet **SavingDataInATransactionWalkthrough**.

3. Sélectionnez **application Windows**, puis cliquez sur **OK**. Pour plus d’informations, consultez [applications clientes](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Le projet **SavingDataInATransactionWalkthrough** est créé et ajouté à l’**Explorateur de solutions**.

## <a name="create-a-database-data-source"></a>Créer une source de données de base de données
 Cette étape utilise l' [Assistant Configuration de source de données](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) pour créer une source de données basée sur les `Customers` `Orders` tables et de l’exemple de base de données Northwind.

#### <a name="to-create-the-data-source"></a>Pour créer la source de données

1. Dans le menu **données** , sélectionnez**afficher les sources de données**.

2. Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’**Assistant Configuration de source de données**.

3. Dans l’écran **choisir un type de source de données**, sélectionnez **base de**données, puis sélectionnez **suivant**.

4. Dans l’écran **choisir votre connexion de données**, effectuez l’une des opérations suivantes :

    - Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

         - ou -

    - Sélectionnez **Nouvelle connexion** pour lancer la boîte de dialogue **Ajouter/Modifier une connexion** et créez une connexion à la base de données Northwind.

5. Si votre base de données requiert un mot de passe, sélectionnez l’option permettant d’inclure des données sensibles, puis sélectionnez **suivant**.

6. Sur la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , sélectionnez **suivant**.

7. Dans l’écran **choisir vos objets de base de données** , développez le nœud **tables** .

8. Sélectionnez les `Customers` `Orders` tables et, puis sélectionnez **Terminer**.

     **NorthwindDataSet** est ajouté à votre projet et les tables `Customers` et `Orders` apparaissent dans la fenêtre **Sources de données**.

## <a name="addcontrols-to-the-form"></a>Addcontrols au formulaire
 Vous pouvez créer les contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **sources de données** vers votre formulaire.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Pour créer des contrôles liés aux données dans le Windows Form

- Dans la fenêtre **sources de données** , développez le nœud **Customers** .

- Faites glisser le nœud **Customers** depuis la fenêtre **Sources de données** vers **Form1**.

     Un contrôle <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent dans le formulaire. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état des composants.

- Faites glisser le nœud **Orders** associé (pas le nœud **Orders** principal, mais le nœud de la table enfant connexe sous la colonne **Fax** ) vers le formulaire sous **CustomersDataGridView**.

     Un <xref:System.Windows.Forms.DataGridView> s'affiche dans le formulaire. Un OrdersTableAdapter et <xref:System.Windows.Forms.BindingSource> s’affiche dans la barre d’état des composants.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Ajouter une référence à l’assembly System. transactions
 Les transactions utilisent l’espace de noms <xref:System.Transactions>. Une référence de projet à l’assembly System. transactions n’est pas ajoutée par défaut. vous devez donc l’ajouter manuellement.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Pour ajouter une référence au fichier DLL System.Transactions

1. Dans le menu **projet** , sélectionnez**Ajouter une référence**.

2. Sélectionnez **System. transactions**(sous l’onglet **.net** ), puis sélectionnez **OK**.

     Une référence à **System.Transactions** est ajoutée au projet.

## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Code Modifythe dans le bouton SaveItem du BindingNavigator
 Pour la première table déplacée dans votre formulaire, du code est ajouté par défaut à l' `click` événement du bouton enregistrer sur le <xref:System.Windows.Forms.BindingNavigator> . Vous devez manuellement ajouter du code pour mettre à jour toutes les tables supplémentaires. Pour cette procédure pas à pas, nous refactorisons le code d’enregistrement existant en dehors du gestionnaire d’événements Click du bouton enregistrer. Nous créons également quelques méthodes supplémentaires pour fournir une fonctionnalité de mise à jour spécifique selon que la ligne doit être ajoutée ou supprimée.

#### <a name="to-modify-the-auto-generated-save-code"></a>Pour modifier le code d'enregistrement généré automatiquement

1. Sélectionnez le bouton **Enregistrer** sur le **CustomersBindingNavigator** (le bouton avec l’icône de disquette).

2. Remplacez la méthode `CustomersBindingNavigatorSaveItem_Click` par le code suivant :

    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]

   L'ordre de rapprochement des modifications des données associées est comme suit :

- Supprimer les enregistrements enfants. (Dans ce cas, supprimez les enregistrements de la `Orders` table.)

- Supprimer les enregistrements parents. (Dans ce cas, supprimez les enregistrements de la `Customers` table.)

- Insérez les enregistrements parents. (Dans ce cas, insérez des enregistrements dans la `Customers` table.)

- Insérer des enregistrements enfants. (Dans ce cas, insérez des enregistrements dans la `Orders` table.)

#### <a name="to-delete-existing-orders"></a>Pour supprimer des commandes existantes

- Ajoutez la méthode `DeleteOrders` suivante à **Form1** :

     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]

#### <a name="to-delete-existing-customers"></a>Pour supprimer des clients existants

- Ajoutez la méthode `DeleteCustomers` suivante à **Form1** :

     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]

#### <a name="to-add-new-customers"></a>Pour ajouter de nouveaux clients

- Ajoutez la méthode `AddNewCustomers` suivante à **Form1** :

     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]

#### <a name="to-add-new-orders"></a>Pour ajouter de nouvelles commandes

- Ajoutez la méthode `AddNewOrders` suivante à **Form1** :

     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]

## <a name="run-the-application"></a>Exécution de l'application

#### <a name="to-run-the-application"></a>Pour exécuter l’application

- Appuyez sur **F5** pour exécuter l’application.

## <a name="see-also"></a>Voir aussi
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
