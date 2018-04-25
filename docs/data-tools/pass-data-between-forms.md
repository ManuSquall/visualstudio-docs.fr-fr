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
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0c308169ef8a0f75821c669fb2cf6876d2b91b06
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="pass-data-between-forms"></a>Passer des données entre des formulaires
Cette procédure pas à pas fournit des instructions détaillées pour passer des données d'un formulaire à l'autre. Les tables customers et orders de Northwind, un formulaire permet aux utilisateurs de sélectionner un client et un deuxième formulaire affiche les commandes du client sélectionné. Cette procédure pas à pas montre comment créer une méthode sur la deuxième forme qui reçoit des données du premier formulaire.

> [!NOTE]
>  Cette procédure pas à pas n'indique qu'un seul moyen de passer les données entre formulaires. Il existe d’autres options pour passer des données à un formulaire, y compris la création d’un deuxième constructeur pour recevoir des données, ou la création d’une propriété publique qui peut être définie avec les données du premier formulaire.

 Cette procédure pas à pas décrit notamment les tâches suivantes :

-   Création d’un **Application Windows Forms** projet.

-   Création et configuration d’un dataset avec le [Assistant de Configuration de Source de données](../data-tools/media/data-source-configuration-wizard.png).

-   Sélectionnez le contrôle à créer sur le formulaire lorsque vous faites glisser des éléments à partir de la **des Sources de données** fenêtre. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Création d’un contrôle lié aux données en faisant glisser des éléments depuis la **des Sources de données** fenêtre dans un formulaire.

-   Création d'un deuxième formulaire avec une grille pour afficher les données.

-   Création d'une requête TableAdapter pour extraire les commandes d'un client spécifique.

-   Transfert de données entre formulaires.

## <a name="prerequisites"></a>Prérequis
Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peut être installé dans le cadre de la **stockage de données et de traitement** charge de travail, ou sous la forme d’un composant individuel.

2.  Installer la base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez le **l’Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le programme d’installation Visual Studio.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête...** .

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée et la base de données Northwind est créé.

## <a name="create-the-windows-forms-application"></a>Créer l’Application Windows Forms

#### <a name="to-create-the-new-windows-project"></a>Pour créer un projet Windows

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau**, **projet...** .

2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **de bureau Windows classique**.

3. Dans le volet central, sélectionnez le **l’application Windows Forms** type de projet.

4. Nommez le projet **PassingDataBetweenForms**, puis choisissez **OK**.

     Le **PassingDataBetweenForms** projet est créé et ajouté à **l’Explorateur de solutions**.

## <a name="create-the-data-source"></a>Créer la source de données

#### <a name="to-create-the-data-source"></a>Pour créer la source de données

1.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

2.  Dans le **des Sources de données** fenêtre, sélectionnez **ajouter une nouvelle Source de données** pour démarrer le **Configuration de Source de données** Assistant.

3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.

4.  Sur le **choisir un modèle de base de données** page, vérifiez que **Dataset** est spécifié, puis cliquez sur **suivant**.

5.  Sur le **choisir votre connexion de données** page, effectuez l’une des opérations suivantes :

    -   Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

    -   Sélectionnez **nouvelle connexion** pour lancer le **Ajouter/modifier la connexion** boîte de dialogue.

6.  Si votre base de données requiert un mot de passe et si l’option permettant d’inclure les données sensibles est activée, sélectionnez l’option, puis **suivant**.

7.  Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** , cliquez sur **suivant**.

8.  Sur le **choisir vos objets de base de données** page, développez le **Tables** nœud.

9. Sélectionnez le **clients** et **commandes** tables, puis cliquez sur **Terminer**.

     Le **NorthwindDataSet** est ajouté à votre projet et le **clients** et **commandes** tables apparaissent dans le **des Sources de données** fenêtre.

## <a name="create-the-first-form-form1"></a>Créez le premier formulaire (Form1)
 Vous pouvez créer une grille liée aux données (un <xref:System.Windows.Forms.DataGridView> contrôle), en faisant glisser le **clients** nœud à partir de la **des Sources de données** fenêtre sur le formulaire.

#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Pour créer une grille liée aux données dans le formulaire

-   Faites glisser le **clients** nœud à partir de la **des Sources de données** fenêtre sur **Form1**.

     A <xref:System.Windows.Forms.DataGridView> et une barre d’outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent sur **Form1**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.

## <a name="create-the-second-form-form2"></a>Créer le deuxième formulaire (Form2)

#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Pour créer un deuxième formulaire auquel passer les données

1.  Dans le menu **Projet**, choisissez **Ajouter un formulaire Windows**.

2.  Laissez le nom par défaut **Form2**, puis cliquez sur **ajouter**.

3.  Faites glisser le **commandes** nœud à partir de la **des Sources de données** fenêtre sur **Form2**.

     A <xref:System.Windows.Forms.DataGridView> et une barre d’outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent sur **Form2**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.

4.  Supprimer le **OrdersBindingNavigator** à partir de la barre d’état du composant.

     Le **OrdersBindingNavigator** disparaît de **Form2**.

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Ajouter une requête TableAdapter à Form2 pour charger les commandes du client sélectionné sur Form1

#### <a name="to-create-a-tableadapter-query"></a>Pour créer une requête TableAdapter

1.  Double-cliquez sur le **NorthwindDataSet.xsd** fichier **l’Explorateur de solutions**.

2.  Cliquez sur le **OrdersTableAdapter**, puis sélectionnez **ajouter une requête**.

3.  Laissez l’option par défaut **utiliser des instructions SQL**, puis cliquez sur **suivant**.

4.  Laissez l’option par défaut **SELECT qui retourne des lignes**, puis cliquez sur **suivant**.

5.  Ajoutez une clause WHERE à la requête, pour retourner `Orders` selon le `CustomerID`. La requête doit ressembler à la suivante :

    ```
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    >  Vérifiez que la syntaxe du paramètre est correcte pour votre base de données. Par exemple, dans Microsoft Access, la clause WHERE est de type : `WHERE CustomerID = ?`.

6.  Cliquez sur **Suivant**.

7.  Pour le **remplir un nom DataTableMethod**, type `FillByCustomerID`.

8.  Désactivez le **retourner un DataTable** option, puis cliquez sur **suivant**.

9. Cliquez sur **Terminer**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Créer une méthode sur Form2 pour passer des données

#### <a name="to-create-a-method-to-pass-data-to"></a>Pour créer une méthode pour y passer les données

1.  Avec le bouton droit **Form2**, puis sélectionnez **afficher le Code** pour ouvrir **Form2** dans les **éditeur de Code**.

2.  Ajoutez le code suivant à **Form2** après le `Form2_Load` méthode :

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Créez une méthode sur Form1 pour passer des données et afficher Form2

#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Pour créer une méthode pour passer les données à Form2

1.  Dans **Form1**, avec le bouton droit de la grille de données client, puis cliquez sur **propriétés**.

2.  Dans le **propriétés** fenêtre, cliquez sur **événements**.

3.  Double-cliquez sur le **CellDoubleClick** événement.

     L'éditeur de code apparaît.

4.  Mettez à jour la définition de la méthode pour qu'elle corresponde à l'exemple suivant :

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-application"></a>Exécution de l'application

#### <a name="to-run-the-application"></a>Pour exécuter l'application

-   Appuyez sur F5 pour exécuter l'application.

-   Double-cliquez sur un enregistrement de client dans **Form1** pour ouvrir **Form2** avec les commandes de ce client.

## <a name="next-steps"></a>Étapes suivantes

Selon les exigences de votre application, vous pouvez exécuter différentes étapes après le transfert de données entre formulaires. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :

-   Modification du dataset pour ajouter ou supprimer des objets de base de données. Pour plus d’informations, consultez [Créer et configurer des datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Ajout d'une fonctionnalité pour enregistrer des données dans la base de données. Pour plus d’informations, consultez [enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)