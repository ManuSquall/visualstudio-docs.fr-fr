---
title: Passer des données entre des formulaires
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 38d41b49335606d390440d11f6df2dc35c7d858b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950394"
---
# <a name="pass-data-between-forms"></a>Passer des données entre des formulaires

Cette procédure pas à pas fournit des instructions détaillées pour passer des données d'un formulaire à l'autre. Les tables customers et orders de Northwind, un formulaire permet aux utilisateurs de sélectionner un client et un deuxième formulaire affiche les commandes du client sélectionné. Cette procédure pas à pas montre comment créer une méthode sur la deuxième forme qui reçoit des données à partir de la première forme.

> [!NOTE]
> Cette procédure pas à pas n'indique qu'un seul moyen de passer les données entre formulaires. Il existe d’autres options pour passer des données à un formulaire, y compris la création d’un deuxième constructeur pour recevoir des données, ou création d’une propriété publique qui peut être définie avec des données à partir de la première forme.

Cette procédure pas à pas décrit notamment les tâches suivantes :

-   Création d’un nouveau **Windows Forms Application** projet.

-   Création et configuration d’un dataset avec le [Assistant de Configuration de Source de données](../data-tools/media/data-source-configuration-wizard.png).

-   Sélection du contrôle à créer dans le formulaire pendant le déplacement d’éléments depuis la fenêtre **Sources de données**. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Création de contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** vers un formulaire.

-   Création d'un deuxième formulaire avec une grille pour afficher les données.

-   Création d’une requête TableAdapter pour récupérer les commandes d’un client spécifique.

-   Transfert de données entre formulaires.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peuvent être installé dans le cadre de la **stockage de données et de traitement** charge de travail, ou comme un composant individuel.

2.  Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans Visual Studio Installer.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée en cours d’exécution et la base de données Northwind est créé.

## <a name="create-the-windows-forms-app-project"></a>Créer le projet d’application Windows Forms

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **New** > **projet**.

2. Développez le **Visual C#**  ou **Visual Basic** dans le volet gauche, puis sélectionnez **Windows Desktop**.

3. Dans le volet central, sélectionnez le **Windows Forms application** type de projet.

4. Nommez le projet **PassingDataBetweenForms**, puis choisissez **OK**.

     Le projet **PassingDataBetweenForms** est créé et ajouté à l’**Explorateur de solutions**.

## <a name="create-the-data-source"></a>Créer la source de données

1.  Pour ouvrir le **des Sources de données** fenêtre, dans le **données** menu, cliquez sur **afficher les Sources de données**.

2.  Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’Assistant **Configuration de source de données**.

3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.

4.  Dans la page **Choisir un modèle de base de données**, vérifiez que **Dataset** est spécifié, puis cliquez sur **Suivant**.

5.  Dans la page **Choisir votre connexion de données**, effectuez l’une des opérations suivantes :

    -   Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

    -   Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter/Modifier la connexion**.

6.  Si votre base de données nécessite un mot de passe et si l’option permettant d’inclure les données sensibles est activée, sélectionnez l’option, puis cliquez sur **Suivant**.

7.  Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** , cliquez sur **suivant**.

8.  Dans la page **Choisir vos objets de base de données**, développez le nœud **Tables**.

9. Sélectionnez les tables **Customers** et **Orders**, puis cliquez sur **Terminer**.

     **NorthwindDataSet** est ajouté à votre projet, et les tables **Customers** et **Orders** apparaissent dans la fenêtre **Sources de données**.

## <a name="create-the-first-form-form1"></a>Créer le premier formulaire (Form1)

Vous pouvez créer une grille liée aux données (un contrôle <xref:System.Windows.Forms.DataGridView>) en faisant glisser le nœud **Customers** depuis la fenêtre **Sources de données** vers le formulaire.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Pour créer une grille liée aux données dans le formulaire

-   Faites glisser le nœud **Customers** depuis la fenêtre **Sources de données** vers **Form1**.

     Un <xref:System.Windows.Forms.DataGridView> et une barre d’outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent sur **Form1**. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état des composants.

## <a name="create-the-second-form"></a>Créer la deuxième forme

Créer un deuxième formulaire auquel passer les données.

1.  Dans le menu **Projet**, choisissez **Ajouter un formulaire Windows**.

2.  Laissez le nom par défaut (**Form2**), puis cliquez sur **Ajouter**.

3.  Faites glisser le nœud **Orders** principal depuis la fenêtre **Sources de données** vers **Form2**.

     Un <xref:System.Windows.Forms.DataGridView> et une barre d’outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent sur **Form2**. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état des composants.

4.  Supprimez **OrdersBindingNavigator** de la barre d’état des composants.

     **OrdersBindingNavigator** disparaît de **Form2**.

## <a name="add-a-tableadapter-query"></a>Ajouter une requête TableAdapter

Ajouter une requête TableAdapter à Form2 pour charger les commandes du client sélectionné sur Form1.

1.  Double-cliquez sur le fichier **NorthwindDataSet.xsd** dans l’**Explorateur de solutions**.

2.  Cliquez avec le bouton droit sur **OrdersTableAdapter** et sélectionnez **Ajouter une requête**.

3.  Laissez l’option par défaut (**Utiliser des instructions SQL**), puis cliquez sur **Suivant**.

4.  Laissez l’option par défaut (**SELECT qui retourne des lignes**), puis cliquez sur **Suivant**.

5.  Ajoutez une clause WHERE à la requête pour retourner `Orders` en fonction de `CustomerID`. La requête doit ressembler à la suivante :

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Vérifiez que la syntaxe du paramètre est correcte pour votre base de données. Par exemple, dans Microsoft Access, la clause WHERE est de type : `WHERE CustomerID = ?`.

6.  Cliquez sur **Suivant**.

7.  Pour le **remplir un nom DataTableMethod**, type `FillByCustomerID`.

8.  Désactivez l’option **Retourner un DataTable**, puis cliquez sur **Suivant**.

9. Cliquez sur **Terminer**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Créez une méthode sur Form2 pour passer des données

1.  Cliquez avec le bouton droit sur **Form2** et sélectionnez **Afficher le code** pour ouvrir **Form2** dans l’**Éditeur de code**.

2.  Ajoutez le code suivant à **Form2** après la méthode `Form2_Load` :

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Créez une méthode sur Form1 pour passer des données et afficher Form2

1.  Dans **Form1**, cliquez avec le bouton droit sur la grille de données Customer, puis cliquez sur **Propriétés**.

2.  Dans la fenêtre **Propriétés**, cliquez sur **Événements**.

3.  Double-cliquez sur l’événement **CellDoubleClick**.

     L'éditeur de code apparaît.

4.  Mettez à jour la définition de la méthode pour qu'elle corresponde à l'exemple suivant :

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>Exécuter l'application

-   Appuyez sur **F5** pour exécuter l’application.

-   Double-cliquez sur un enregistrement client dans **Form1** pour ouvrir **Form2** avec les commandes de ce client.

## <a name="next-steps"></a>Étapes suivantes

Selon les exigences de votre application, vous pouvez exécuter différentes étapes après le transfert de données entre formulaires. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :

-   Modification du dataset pour ajouter ou supprimer des objets de base de données. Pour plus d’informations, consultez [Créer et configurer des datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Ajout d'une fonctionnalité pour enregistrer des données dans la base de données. Pour plus d’informations, consultez [enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)