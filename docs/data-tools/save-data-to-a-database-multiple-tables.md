---
title: Enregistrer des données dans une base de données (plusieurs tables)
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b512263cd5d0ca8c83b0ba6848fb16feca1a71f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281641"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Enregistrer des données dans une base de données (plusieurs tables)

L'un des scénarios les plus courants dans le développement d'applications consiste à afficher des données dans un formulaire d'une application Windows, à modifier ces données, puis à renvoyer les données mises à jour à la base de données. Cette procédure pas à pas crée un formulaire affichant les données de deux tables associées et indique comment modifier les enregistrements et enregistrer les modifications dans la base de données. Cet exemple utilise les tables `Customers` et `Orders` de l'exemple de base de données Northwind.

Vous pouvez enregistrer des données de votre application dans la base de données en appelant la méthode `Update` d'un TableAdapter. Lorsque vous faites glisser des tables depuis la fenêtre **sources de données** vers un formulaire, le code requis pour enregistrer les données est automatiquement ajouté. Toutes les tables supplémentaires ajoutées à un formulaire nécessitent l’ajout manuel de ce code. Cette procédure pas à pas indique comment ajouter du code pour enregistrer les mises à jour de plusieurs tables.

Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création et configuration d’une source de données dans votre application à l’aide de l' [Assistant Configuration de source de données](../data-tools/media/data-source-configuration-wizard.png).

- Définition des contrôles des éléments dans la [fenêtre sources de données](add-new-data-sources.md#data-sources-window). Pour plus d’informations, consultez [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Création de contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** vers votre formulaire.

- Modification de quelques enregistrements dans chaque table du DataSet.

- Modification du code pour renvoyer les données mises à jour dans le dataset à la base de données.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express base de données locale et l’exemple de base de données Northwind.

1. Si vous n’avez pas SQL Server Express base de données locale, installez-la à partir de la [page de téléchargement SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)ou via le **Visual Studio installer**. Dans le **Visual Studio installer**, vous pouvez installer SQL Server Express base de données locale dans le cadre de la charge de travail de **stockage et de traitement des données** , ou en tant que composant individuel.

2. Installez l’exemple de base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez la fenêtre de **Explorateur d’objets SQL Server** . (Explorateur d’objets SQL Server est installé dans le cadre de la charge de travail **stockage et traitement des données** dans le Visual Studio installer.) Développez le nœud **SQL Server** . Cliquez avec le bouton droit sur votre instance de base de données locale, puis sélectionnez **nouvelle requête**.

       Une fenêtre de l’éditeur de requête s’ouvre.

    2. Copiez le [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le bouton **exécuter** .

       Après un bref laps de temps, l’exécution de la requête se termine et la base de données Northwind est créée.

## <a name="create-the-windows-forms-application"></a>Créer l’application Windows Forms

Créez un projet d' **application Windows Forms** pour C# ou Visual Basic. Attribuez le nom **UpdateMultipleTablesWalkthrough** au projet.

## <a name="create-the-data-source"></a>Créer la source de données

Cette étape crée une source de données à partir de la base de données Northwind à l’aide de l’**Assistant Configuration de source de données**. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la configuration de l’exemple de base de données Northwind, consultez [Comment : installer des exemples de bases de données](../data-tools/installing-database-systems-tools-and-samples.md).

1. Dans le menu **données** , sélectionnez **afficher les sources de données**.

   La fenêtre **Sources de données** s’ouvre.

2. Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’**Assistant Configuration de source de données**.

3. Dans l’écran **choisir un type de source de données** , sélectionnez **base de**données, puis sélectionnez **suivant**.

4. Sur l’écran **choisir votre connexion de données** , effectuez l’une des opérations suivantes :

    - Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

         - ou -

    - Sélectionnez **Nouvelle connexion** pour ouvrir la boîte de dialogue **Ajouter/Modifier la connexion**.

5. Si votre base de données requiert un mot de passe, sélectionnez l’option permettant d’inclure des données sensibles, puis sélectionnez **suivant**.

6. Dans la **chaîne de connexion enregistrer dans le fichier de configuration de l’application**, sélectionnez **suivant**.

7. Dans l’écran **choisir vos objets de base de données** , développez le nœud **tables** .

8. Sélectionnez les tables **Customers** et **Orders** , puis sélectionnez **Finish**.

     **NorthwindDataSet** est ajouté à votre projet et les tables apparaissent dans la fenêtre **Sources de données**.

## <a name="set-the-controls-to-be-created"></a>Définir les contrôles à créer

Pour cette procédure pas à pas, les données de la `Customers` table sont dans une disposition des **Détails** où les données sont affichées dans des contrôles individuels. Les données de la `Orders` table sont dans une disposition en **grille** qui est affichée dans un <xref:System.Windows.Forms.DataGridView> contrôle.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Pour définir le type de déplacement des éléments de la fenêtre Sources de données

1. Dans la fenêtre **sources de données** , développez le nœud **Customers** .

2. Sur le nœud **Customers** , sélectionnez **Details** dans la liste de contrôle pour remplacer le contrôle de la table **Customers** par des contrôles individuels. Pour plus d’informations, consultez [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Créer le formulaire lié aux données

Vous pouvez créer les contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **sources de données** vers votre formulaire.

1. Faites glisser le nœud **Customers** depuis la fenêtre **Sources de données** vers **Form1**.

     Les contrôles liés aux données assortis d'étiquettes descriptives apparaissent dans le formulaire, ainsi qu'une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> apparaissent dans la barre d’état des composants.

2. Faites glisser le nœud **Orders** associé depuis la fenêtre **Sources de données** vers **Form1**.

    > [!NOTE]
    > Le nœud **Orders** associé est situé sous la colonne **Fax** et constitue un nœud enfant du nœud **Customers**.

     Un contrôle <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent dans le formulaire. `OrdersTableAdapter`Et <xref:System.Windows.Forms.BindingSource> apparaissent dans la barre d’état des composants.

## <a name="add-code-to-update-the-database"></a>Ajouter du code pour mettre à jour la base de données

Vous pouvez mettre à jour la base de données en appelant les méthodes `Update` des TableAdapters **Customers** et **Orders**. Par défaut, un gestionnaire d’événements pour le bouton **Enregistrer** de <xref:System.Windows.Forms.BindingNavigator> est ajouté au code du formulaire pour envoyer des mises à jour à la base de données. Cette procédure modifie le code pour envoyer les mises à jour dans le bon ordre. Cela élimine la possibilité de déclencher des erreurs d’intégrité référentielle. Le code implémente également la gestion des erreurs en enveloppant l'appel de mise à jour dans un bloc try-catch. Vous pouvez modifier le code pour répondre aux besoins de votre application.

> [!NOTE]
> Par souci de clarté, cette procédure pas à pas n’utilise pas de transaction. Toutefois, si vous mettez à jour au moins deux tables associées, vous devez inclure toute la logique de mise à jour dans une transaction. Une transaction est un processus qui garantit que toutes les modifications associées à une base de données réussissent avant que les modifications ne soient validées. Pour plus d’informations, consultez [transactions et accès concurrentiel](/dotnet/framework/data/adonet/transactions-and-concurrency).

### <a name="to-add-update-logic-to-the-application"></a>Pour ajouter une logique de mise à jour à l'application

1. Sélectionnez le bouton **Enregistrer** dans la <xref:System.Windows.Forms.BindingNavigator> . L’éditeur de code s’ouvre alors dans le `bindingNavigatorSaveItem_Click` Gestionnaire d’événements.

2. Remplacez le code dans le gestionnaire d'événements pour appeler les méthodes `Update` des TableAdapters associés. Le code suivant crée d'abord trois tables de données temporaires pour contenir les informations mises à jour pour chaque <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> et <xref:System.Data.DataRowState.Modified>). Les mises à jour sont exécutées dans le bon ordre. Le code doit se présenter comme suit :

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>Tester l’application

1. Appuyez sur **F5**.

2. Apportez quelques modifications aux données d'un ou plusieurs enregistrements dans chaque table.

3. Sélectionnez le bouton **Enregistrer**.

4. Vérifiez les valeurs figurant dans la base de données pour confirmer que les modifications ont bien été enregistrées.

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
