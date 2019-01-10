---
title: Enregistrer des données avec les méthodes DBDirect du TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 88590c49938ef61344a1092dffb42565a81755d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920139"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Enregistrer des données avec les méthodes DBDirect du TableAdapter

Cette procédure pas à pas fournit des instructions détaillées pour l’exécution des instructions SQL directement sur une base de données en utilisant les méthodes DBDirect d’un TableAdapter. Les méthodes DBDirect d’un TableAdapter fournissent un niveau élevé de contrôle sur vos mises à jour de base de données. Vous pouvez les utiliser pour exécuter des instructions SQL et les procédures stockées en appelant l’individu `Insert`, `Update`, et `Delete` méthodes selon les besoins de votre application (par opposition à surchargées `Update` méthode qui effectue la mise à jour Instructions INSERT et DELETE dans un seul appel).

Pendant cette procédure pas à pas, vous allez apprendre à :

-   Créer une **application Windows Forms**.

-   Créer et configurer un jeu de données avec le [Assistant de Configuration de Source de données](../data-tools/media/data-source-configuration-wizard.png).

-   Sélectionner le contrôle à créer dans le formulaire lors du déplacement d’éléments depuis la fenêtre **Sources de données**. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Créer un formulaire lié aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** sur le formulaire.

-   Ajouter des méthodes pour accéder à la base de données directement et d’effectuer des insertions, mises à jour et suppressions.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1. Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le **le programme d’installation de Visual Studio**, vous pouvez installer SQL Server Express LocalDB dans le cadre de la **stockage de données et de traitement** charge de travail, ou comme un composant individuel.

2. Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans Visual Studio Installer.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée en cours d’exécution et la base de données Northwind est créé.

## <a name="create-a-windows-forms-application"></a>Créer une application Windows Forms

La première étape consiste à créer un **Windows Forms Application**.

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **New** > **projet**.

2. Développez le **Visual C#**  ou **Visual Basic** dans le volet gauche, puis sélectionnez **Windows Desktop**.

3. Dans le volet central, sélectionnez le **Windows Forms application** type de projet.

4. Nommez le projet **TableAdapterDbDirectMethodsWalkthrough**, puis choisissez **OK**.

     Le projet **TableAdapterDbDirectMethodsWalkthrough** est créé et ajouté à l’**Explorateur de solutions**.

## <a name="create-a-data-source-from-your-database"></a>Créer une source de données à partir de votre base de données

Cette étape utilise l’**Assistant Configuration de source de données** pour créer une source de données basée sur la table `Region` de l’exemple de base de données Northwind. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la configuration de la base de données Northwind, consultez [Comment : Installer les bases de données exemple](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-data-source"></a>Pour créer la source de données

1. Sur le **données** menu, sélectionnez **afficher les Sources de données**.

   La fenêtre **Sources de données** s’ouvre.

2. Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’**Assistant Configuration de source de données**.

3. Sur le **choisir un Type de Source de données** s’affiche, sélectionnez **base de données**, puis sélectionnez **suivant**.

4. Sur le **choisir votre connexion de données** , effectuez une des opérations suivantes :

    -   Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

         - ou -

    -   Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter/Modifier la connexion**.

5. Si votre base de données requiert un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis sélectionnez **suivant**.

6. Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** s’affiche, sélectionnez **suivant**.

7. Sur le **choisir vos objets de base de données** écran, développez le **Tables** nœud.

8. Sélectionnez le `Region` table, puis sélectionnez **Terminer**.

     **NorthwindDataSet** est ajouté à votre projet et la table `Region` apparaît dans la fenêtre **Sources de données**.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Ajouter des contrôles au formulaire pour afficher les données

Créez les contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** sur votre formulaire.

Pour créer des contrôles liés aux données sur le formulaire Windows, faites glisser le **région** nœud à partir de la **des Sources de données** fenêtre vers le formulaire.

Un contrôle <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent dans le formulaire. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Pour ajouter des boutons pour appeler les méthodes DbDirect individuelles de TableAdapter

1. Faites glisser trois contrôles <xref:System.Windows.Forms.Button> depuis la **Boîte à outils** vers **Form1** (sous la **RegionDataGridView**).

2. Définissez les propriétés **Name** et **Text** suivantes sur chaque bouton.

    |Name|Texte|
    |----------|----------|
    |`InsertButton`|**Insert**|
    |`UpdateButton`|**Mettre à jour**|
    |`DeleteButton`|**Supprimer**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Pour ajouter du code afin d'insérer de nouveaux enregistrements dans la base de données

1. Sélectionnez **InsertButton** pour créer un gestionnaire d’événements pour l’événement click et ouvrir votre formulaire dans l’éditeur de code.

2. Remplacez le gestionnaire d'événements `InsertButton_Click` par le code suivant :

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>Pour ajouter du code afin de mettre à jour des enregistrements dans la base de données

1. Double-cliquez sur **UpdateButton** pour créer un gestionnaire d’événements pour l’événement Click et ouvrir votre formulaire dans l’éditeur de code.

2. Remplacez le gestionnaire d'événements `UpdateButton_Click` par le code suivant :

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>Pour ajouter du code pour supprimer des enregistrements à partir de la base de données

1. Sélectionnez **DeleteButton** pour créer un gestionnaire d’événements pour l’événement click et ouvrir votre formulaire dans l’éditeur de code.

2. Remplacez le gestionnaire d'événements `DeleteButton_Click` par le code suivant :

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Exécuter l'application

-   Sélectionnez **F5** pour exécuter l’application.

-   Sélectionnez le **insérer** bouton et vérifiez que le nouvel enregistrement apparaît dans la grille.

-   Sélectionnez le **mise à jour** bouton, puis vérifiez que l’enregistrement est mis à jour dans la grille.

-   Sélectionnez le **supprimer** bouton et vérifiez que l’enregistrement est supprimé de la grille.

## <a name="next-steps"></a>Étapes suivantes

Selon les exigences de votre application, il existe plusieurs étapes, que vous souhaiterez peut-être effectuer après la création d’un formulaire lié aux données. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :

-   Ajout d'une fonctionnalité de recherche au formulaire.

-   Ajout de tables supplémentaires au dataset en sélectionnant **Configurer le DataSet à l’aide de l’Assistant** dans la fenêtre **Sources de données**. Vous pouvez ajouter des contrôles pour afficher les données associées en faisant glisser les nœuds associés vers le formulaire. Pour plus d’informations, consultez [relations dans les Datasets](relationships-in-datasets.md).

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)