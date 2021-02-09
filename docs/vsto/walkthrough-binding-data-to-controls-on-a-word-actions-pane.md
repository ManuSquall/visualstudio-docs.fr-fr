---
title: 'Procédure pas à pas : liaison de données à des contrôles dans un volet Actions Word'
description: Lier des données à des contrôles dans un volet actions dans Microsoft Word. Les contrôles illustrent une relation Maître/Détail entre des tables dans une base de données SQL Server.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7599348b0c44b7239305bb5af49ee2f5c51d882b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906589"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Procédure pas à pas : liaison de données à des contrôles dans un volet Actions Word
  Cette procédure pas à pas montre comment lier des données à des contrôles dans un volet actions dans Word. Les contrôles illustrent une relation Maître/Détail entre des tables dans une base de données SQL Server.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un volet actions avec des contrôles Windows Forms liés aux données.

- Utilisation d’une relation maître/détail pour afficher des données dans les contrôles.

- Affichez le volet actions lorsque l’application s’ouvre.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Accès à un serveur avec l’exemple de base de données Northwind SQL Server.

- Autorisations de lecture et d’écriture dans la base de données SQL Server.

## <a name="create-the-project"></a>Créer le projet
 La première étape consiste à créer un projet de document Word.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de document Word avec le nom **My Word Actions Pane**. Dans l’Assistant, sélectionnez **créer un nouveau document**.

     Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le projet **My Word Actions Pane** à **Explorateur de solutions**.

## <a name="add-controls-to-the-actions-pane"></a>Ajouter des contrôles au volet Actions
 Pour cette procédure pas à pas, vous avez besoin d’un contrôle de volet actions qui contient des contrôles de Windows Forms liés aux données. Ajoutez une source de données au projet, puis faites glisser les contrôles de la fenêtre **sources de données** vers le contrôle du volet Actions.

### <a name="to-add-an-actions-pane-control"></a>Pour ajouter un contrôle de volet Actions

1. Sélectionnez le projet **My Word Actions Pane** dans **Explorateur de solutions**.

2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **contrôle du volet Actions**, nommez-le **ActionsControl**, puis cliquez sur **Ajouter**.

### <a name="to-add-a-data-source-to-the-project"></a>Pour ajouter une source de données au projet

1. Si la fenêtre **sources de données** n’est pas visible, affichez-la en cliquant sur **Afficher** d'  >  **autres**  >  **sources de données** Windows dans la barre de menus.

   > [!NOTE]
   > Si l’option **afficher les sources de données** n’est pas disponible, cliquez sur le document Word, puis vérifiez à nouveau.

2. Cliquez sur **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

3. Sélectionnez **base de données** , puis cliquez sur **suivant**.

4. Sélectionnez une connexion de données à l’exemple Northwind SQL Server base de données ou ajoutez une nouvelle connexion à l’aide du bouton **nouvelle connexion** .

5. Cliquez sur **Suivant**.

6. Désactivez l’option permettant d’enregistrer la connexion si elle est sélectionnée, puis cliquez sur **suivant**.

7. Développez le nœud **tables** dans la fenêtre **objets de base de données** .

8. Activez la case à cocher en regard des tables **fournisseurs** et **produits** .

9. Cliquez sur **Terminer**.

   L’Assistant ajoute la table **Suppliers** et la table **Products** à la fenêtre **sources de données** . Il ajoute également un DataSet typé à votre projet qui est visible dans **Explorateur de solutions**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Pour ajouter des contrôles de Windows Forms liés aux données à un contrôle de volet Actions

1. Dans la fenêtre **sources de données** , développez la table **Suppliers** .

2. Cliquez sur la flèche déroulante du nœud nom de l' **entreprise** , puis sélectionnez **ComboBox**.

3. Faites glisser **CompanyName** de la fenêtre **sources de données** vers le contrôle du volet Actions.

     Un <xref:System.Windows.Forms.ComboBox> contrôle est créé sur le contrôle de volet Actions. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `SuppliersBindingSource` , un adaptateur de table et un <xref:System.Data.DataSet> sont ajoutés au projet dans la barre d’état des composants.

4. Sélectionnez `SuppliersBindingNavigator` dans la barre d’état des **composants** , puis appuyez sur la touche **Suppr**. Vous n’utiliserez pas le `SuppliersBindingNavigator` dans cette procédure pas à pas.

    > [!NOTE]
    > La suppression de `SuppliersBindingNavigator` n’entraîne pas la suppression de tout le code qui a été généré pour celui-ci. Vous pouvez supprimer ce code.

5. Déplacez la zone de liste déroulante afin qu’elle soit sous l’étiquette et remplacez la valeur de la propriété **Size** par **171, 21**.

6. Dans la fenêtre **sources de données** , développez la table **Products** qui est un enfant de la table **Suppliers** .

7. Cliquez sur la flèche déroulante du nœud **NomProduit** , puis sélectionnez **ListBox**.

8. Faites glisser **ProductName** dans le contrôle de volet Actions.

     Un <xref:System.Windows.Forms.ListBox> contrôle est créé sur le contrôle de volet Actions. En même temps, un <xref:System.Windows.Forms.BindingSource> adaptateur nommé `ProductBindingSource` et un adaptateur de table sont ajoutés au projet dans la barre d’état des composants.

9. Déplacez la zone de liste pour qu’elle se trouve sous l’étiquette et remplacez la valeur de la propriété **Size** par **171, 95**.

10. Faites glisser un <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le contrôle du volet Actions et placez-le sous la zone de liste.

11. Cliquez avec le bouton droit sur le <xref:System.Windows.Forms.Button> , cliquez sur **Propriétés** dans le menu contextuel, puis modifiez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**Insérer**|
    |**Text**|**Insérer**|

12. Redimensionnez le contrôle utilisateur pour l’ajuster aux contrôles.

## <a name="set-up-the-data-source"></a>Configurer la source de données
 Pour configurer la source de données, ajoutez du code à l' <xref:System.Windows.Forms.UserControl.Load> événement du contrôle de volet Actions pour remplir le contrôle avec les données du et <xref:System.Data.DataTable> définissez les <xref:System.Windows.Forms.Binding.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> Propriétés et pour chaque contrôle.

### <a name="to-load-the-control-with-data"></a>Pour charger le contrôle avec des données

1. Dans le <xref:System.Windows.Forms.UserControl.Load> Gestionnaire d’événements de la `ActionsControl` classe, ajoutez le code suivant.

     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]

2. En C#, vous devez attacher le gestionnaire d’événements à l' <xref:System.Windows.Forms.UserControl.Load> événement. Vous pouvez placer ce code dans le `ActionsControl` constructeur, après l’appel à `InitializeComponent` . Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]

### <a name="to-set-data-binding-properties-of-the-controls"></a>Pour définir les propriétés de liaison de données des contrôles

1. Sélectionnez le contrôle `CompanyNameComboBox`.

2. Dans la fenêtre **Propriétés** , cliquez sur le bouton à droite de la propriété **DataSource** , puis sélectionnez **suppliersBindingSource**.

3. Cliquez sur le bouton à droite de la propriété **DisplayMember** , puis sélectionnez **CompanyName**.

4. Développez la propriété **DataBindings** , cliquez sur le bouton à droite de la propriété **Text** , puis sélectionnez **aucun**.

5. Sélectionnez le contrôle `ProductNameListBox`.

6. Dans la fenêtre **Propriétés** , cliquez sur le bouton à droite de la propriété **DataSource** , puis sélectionnez **ProductsBindingSource**.

7. Cliquez sur le bouton à droite de la propriété **DisplayMember** , puis sélectionnez **ProductName**.

8. Développez la propriété **DataBindings** , cliquez sur le bouton à droite de la propriété **SelectedValue** , puis sélectionnez **aucun**.

## <a name="add-a-method-to-insert-data-into-a-table"></a>Ajouter une méthode pour insérer des données dans une table
 La tâche suivante consiste à lire les données des contrôles liés et à remplir une table dans votre document Word. Tout d’abord, créez une procédure pour mettre en forme les en-têtes de la table, puis ajoutez la `AddData` méthode pour créer et mettre en forme un tableau Word.

### <a name="to-format-the-table-headings"></a>Pour mettre en forme les en-têtes de tableau

1. Dans la `ActionsControl` classe, créez une méthode pour mettre en forme les en-têtes de la table.

     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]

### <a name="to-create-the-table"></a>Pour créer la table

1. Dans la `ActionsControl` classe, écrivez une méthode qui créera une table si elle n’existe pas déjà, et ajoutera des données du volet actions à la table.

     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]

### <a name="to-insert-text-into-a-word-table"></a>Pour insérer du texte dans un tableau Word

1. Ajoutez le code suivant au <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements du bouton **Insérer** .

     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]

2. En C#, vous devez créer un gestionnaire d’événements pour l' <xref:System.Windows.Forms.Control.Click> événement du bouton.  Vous pouvez placer ce code dans le <xref:System.Windows.Forms.UserControl.Load> Gestionnaire d’événements de la `ActionsControl` classe.

     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]

## <a name="show-the-actions-pane"></a>Afficher le volet Actions
 Le volet Actions devient visible après l’ajout de contrôles.

### <a name="to-show-the-actions-pane"></a>Pour afficher le volet Actions

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **ThisDocument. vb** ou **ThisDocument.cs**, puis cliquez sur **afficher le code** dans le menu contextuel.

2. Créez une nouvelle instance du contrôle en haut de la `ThisDocument` classe afin qu’elle ressemble à l’exemple suivant.

     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]

3. Ajoutez du code au <xref:Microsoft.Office.Tools.Word.Document.Startup> Gestionnaire d’événements de `ThisDocument` afin qu’il ressemble à l’exemple suivant.

     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

## <a name="test-the-application"></a>Tester l’application
 Vous pouvez maintenant tester votre document pour vérifier que le volet actions s’affiche lorsque le document est ouvert. Testez la relation maître/détail dans les contrôles du volet Actions et assurez-vous que les données sont renseignées dans un tableau Word quand l’utilisateur clique sur le bouton **Insérer** .

### <a name="to-test-your-document"></a>Pour tester votre document

1. Appuyez sur **F5** pour exécuter votre projet.

2. Vérifiez que le volet actions est visible.

3. Sélectionnez une société dans la zone de liste déroulante et vérifiez que les éléments de la zone de liste **produits** changent.

4. Sélectionnez un produit, cliquez sur **Insérer** dans le volet Actions et vérifiez que les détails du produit sont ajoutés au tableau dans Word.

5. Insérez des produits supplémentaires de différentes sociétés.

## <a name="next-steps"></a>Étapes suivantes
 Cette procédure pas à pas montre les concepts de base de la liaison de données à des contrôles dans un volet actions dans Word. Voici quelques tâches susceptibles de venir après :

- Liaison de données à des contrôles dans Excel. Pour plus d’informations, consultez [procédure pas à pas : liaison de données à des contrôles dans un volet Actions Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

- Déploiement du projet. Pour plus d’informations, consultez [déployer une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)
- [Comment : ajouter un volet actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
