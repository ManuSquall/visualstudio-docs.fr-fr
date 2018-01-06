---
title: "Procédure pas à pas : Liaison de données aux contrôles dans un volet Actions Word | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: "64"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: be9a2b19a8c9c34390a359fd8e3350d6af654fde
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-binding-data-to-controls-on-a-word-actions-pane"></a>Procédure pas à pas : liaison de données aux contrôles dans un volet Actions Word
  Cette procédure pas à pas illustre la liaison de données aux contrôles dans un volet actions dans Word. Les contrôles illustrent une relation Maître/Détail entre des tables dans une base de données SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un volet actions avec des contrôles Windows Forms liés aux données.  
  
-   À l’aide d’une relation maître/détail pour afficher des données dans les contrôles.  
  
-   Afficher le volet actions lorsque l’application s’ouvre.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Accès à un serveur avec la base de données Northwind SQL Server.  
  
-   Autorisations pour lire et écrire dans la base de données SQL Server.  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer un projet de document Word.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de Document Word portant le nom **Mon volet Actions de Word**. Dans l’Assistant, sélectionnez **créer un nouveau document**.  
  
     Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le **Mon volet Actions de Word** projet **l’Explorateur de solutions**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Ajout de contrôles au volet Actions  
 Pour cette procédure pas à pas, vous avez besoin d’un contrôle de volet actions qui contient des contrôles Windows Forms liés aux données. Ajouter une source de données au projet, puis faites glisser les contrôles à partir de la **des Sources de données** fenêtre pour le contrôle de volet actions.  
  
#### <a name="to-add-an-actions-pane-control"></a>Pour ajouter un contrôle de volet actions  
  
1.  Sélectionnez le **Mon volet Actions de Word** projet **l’Explorateur de solutions**.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **contrôle de volet Actions**, nommez-le **ActionsControl**, puis cliquez sur **ajouter**.  
  
#### <a name="to-add-a-data-source-to-the-project"></a>Pour ajouter une source de données au projet  
  
1.  Si la fenêtre **Sources de données** n'est pas visible, affichez-la en choisissant, dans la barre de menus, **Affichage**, **Autres fenêtres**, **Sources de données**.  
  
    > [!NOTE]  
    >  Si **afficher les Sources de données** n’est pas disponible, cliquez sur le document Word, puis vérifiez à nouveau.  
  
2.  Cliquez sur **ajouter une nouvelle Source de données** pour démarrer le **Assistant de Configuration de Source de données**.  
  
3.  Sélectionnez **base de données** puis cliquez sur **suivant**.  
  
4.  Sélectionnez une connexion de données à la base de données Northwind exemple SQL Server ou ajouter une nouvelle connexion à l’aide de la **nouvelle connexion** bouton.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Désactivez l’option pour enregistrer la connexion si elle est activée, puis cliquez sur **suivant**.  
  
7.  Développez le **Tables** nœud dans le **objets de base de données** fenêtre.  
  
8.  Sélectionnez la case à cocher à côté du **fournisseurs** et **produits** tables.  
  
9. Cliquez sur **Terminer**.  
  
 L’Assistant ajoute les **fournisseurs** table et **produits** de la table vers le **des Sources de données** fenêtre. Il ajoute également un dataset typé à votre projet qui est visible dans **l’Explorateur de solutions**.  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Pour ajouter des contrôles Windows Forms liés aux données à un contrôle de volet actions  
  
1.  Dans le **des Sources de données** fenêtre, développez le **fournisseurs** table.  
  
2.  Cliquez sur la flèche déroulante du **nom de la société** nœud et sélectionnez **ComboBox**.  
  
3.  Faites glisser **CompanyName** à partir de la **des Sources de données** fenêtre pour le contrôle de volet actions.  
  
     A <xref:System.Windows.Forms.ComboBox> contrôle est créé sur le contrôle de volet actions. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `SuppliersBindingSource`, un adaptateur de table et un <xref:System.Data.DataSet> sont ajoutés au projet dans la barre d’état du composant.  
  
4.  Sélectionnez `SuppliersBindingNavigator` dans les **composant** barre d’état et appuyez sur SUPPR. Vous n’utiliserez pas la `SuppliersBindingNavigator` dans cette procédure pas à pas.  
  
    > [!NOTE]  
    >  Suppression de la `SuppliersBindingNavigator` ne supprime pas la totalité du code qui a été généré pour lui. Vous pouvez supprimer ce code.  
  
5.  Déplacer la zone de liste déroulante afin qu’il soit sous l’étiquette et la modification de la **taille** propriété **171, 21**.  
  
6.  Dans le **des Sources de données** fenêtre, développez le **produits** de table qui est un enfant de la **fournisseurs** table.  
  
7.  Cliquez sur la flèche déroulante du **ProductName** nœud et sélectionnez **ListBox**.  
  
8.  Faites glisser **ProductName** au contrôle de volet actions.  
  
     A <xref:System.Windows.Forms.ListBox> contrôle est créé sur le contrôle de volet actions. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `ProductBindingSource` et un adaptateur de table sont ajoutés au projet dans la barre d’état du composant.  
  
9. Déplacer la zone de liste afin qu’il soit sous l’étiquette et la modification de la **taille** propriété **par 171,95**.  
  
10. Faites glisser un <xref:System.Windows.Forms.Button> à partir de la **boîte à outils** dans le volet actions contrôler et placez-le sous la zone de liste.  
  
11. Cliquez sur le <xref:System.Windows.Forms.Button>, cliquez sur **propriétés** dans le menu contextuel et modifiez les propriétés suivantes.  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**Insert**|  
    |**Text**|**Insert**|  
  
12. Redimensionner le contrôle utilisateur pour ajuster les contrôles.  
  
## <a name="setting-up-the-data-source"></a>Configuration de la Source de données  
 Pour configurer la source de données, ajoutez le code à la <xref:System.Windows.Forms.UserControl.Load> événement du contrôle de volet actions pour remplir le contrôle de données à partir de la <xref:System.Data.DataTable>et définissez la <xref:System.Windows.Forms.Binding.DataSource%2A> et <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriétés pour chaque contrôle.  
  
#### <a name="to-load-the-control-with-data"></a>Pour charger le contrôle de données  
  
1.  Dans le <xref:System.Windows.Forms.UserControl.Load> Gestionnaire d’événements de le `ActionsControl` de classe, ajoutez le code suivant.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  En c#, vous devez associer le Gestionnaire d’événements pour le <xref:System.Windows.Forms.UserControl.Load> événement. Vous pouvez placer ce code dans le `ActionsControl` constructeur, après l’appel à `InitializeComponent`. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
#### <a name="to-set-data-binding-properties-of-the-controls"></a>Pour définir les propriétés de liaison de données des contrôles  
  
1.  Sélectionnez le contrôle `CompanyNameComboBox`.  
  
2.  Dans le **propriétés** fenêtre, cliquez sur le bouton à droite de la **DataSource** propriété, puis sélectionnez **suppliersBindingSource**.  
  
3.  Cliquez sur le bouton à droite de la **DisplayMember** propriété, puis sélectionnez **CompanyName**.  
  
4.  Développez le **DataBindings** propriété, cliquez sur le bouton à droite de la **texte** propriété, puis sélectionnez **aucun**.  
  
5.  Sélectionnez le contrôle `ProductNameListBox`.  
  
6.  Dans le **propriétés** fenêtre, cliquez sur le bouton à droite de la **DataSource** propriété, puis sélectionnez **productsBindingSource**.  
  
7.  Cliquez sur le bouton à droite de la **DisplayMember** propriété, puis sélectionnez **ProductName**.  
  
8.  Développez le **DataBindings** propriété, cliquez sur le bouton à droite de la **SelectedValue** propriété, puis sélectionnez **aucun**.  
  
## <a name="adding-a-method-to-insert-data-into-a-table"></a>Ajout d’une méthode pour insérer des données dans une Table  
 La tâche suivante consiste à lire les données à partir de contrôles liés et remplir une table dans votre document Word. Tout d’abord, créez une procédure pour mettre en forme les en-têtes dans la table et puis ajoutez le `AddData` pour créer et mettre en forme un tableau Word.  
  
#### <a name="to-format-the-table-headings"></a>Pour mettre en forme les en-têtes de tableau  
  
1.  Dans la `ActionsControl` de classe, créez une méthode pour mettre en forme les en-têtes de la table.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
#### <a name="to-create-the-table"></a>Pour créer la table  
  
1.  Dans la `ActionsControl` de classe, écrivez une méthode qui crée une table s’il n’existe pas déjà et ajouter des données à partir du volet actions à la table.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
#### <a name="to-insert-text-into-a-word-table"></a>Pour insérer du texte dans un tableau Word  
  
1.  Ajoutez le code suivant à la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la **insérer** bouton.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  En c#, vous devez créer un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> événements du bouton.  Vous pouvez placer ce code dans le <xref:System.Windows.Forms.UserControl.Load> Gestionnaire d’événements de la `ActionsControl` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="showing-the-actions-pane"></a>Affichage du volet Actions  
 Le volet actions devient visible une fois que les contrôles sont ajoutés à ce dernier.  
  
#### <a name="to-show-the-actions-pane"></a>Pour afficher le volet actions  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **ThisDocument.vb** ou **ThisDocument.cs**, puis cliquez sur **afficher le Code** dans le menu contextuel.  
  
2.  Créer une nouvelle instance du contrôle en haut de la `ThisDocument` classe afin qu’il ressemble à l’exemple suivant.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  Ajoutez le code pour le <xref:Microsoft.Office.Tools.Word.Document.Startup> de gestionnaire d’événements `ThisDocument` afin qu’il ressemble à l’exemple suivant.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester votre document pour vérifier que le volet actions apparaît lorsque le document est ouvert. Tester pour la relation maître/détail dans les contrôles du volet actions et vous assurer que les données sont entrées dans un mot table lorsque la **insérer** bouton est activé.  
  
#### <a name="to-test-your-document"></a>Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Vérifiez que le volet actions est visible.  
  
3.  Sélectionnez une société dans la zone de liste déroulante et vérifiez que les éléments de la **produits** zone de liste changent.  
  
4.  Sélectionner un produit, cliquez sur **insérer** dans le volet actions et vérifiez que les détails du produit sont ajoutés à la table dans Word.  
  
5.  Insérez des produits supplémentaires provenant de différentes sociétés.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas illustre les principes fondamentaux de la liaison de données aux contrôles dans un volet actions dans Word. Voici quelques tâches susceptibles de venir après :  
  
-   Liaison de données aux contrôles dans Excel. Pour plus d’informations, consultez [procédure pas à pas : liaison de données aux contrôles dans un volet Actions Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Déploiement du projet. Pour plus d’informations, consultez [déploiement d’une Solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Comment : ajouter un volet Actions à des Documents Word ou des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  