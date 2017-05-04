---
title: "Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es aux contr&#244;les dans un volet Actions Word | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "volets Actions (développement Office dans Visual Studio), lier des contrôles"
  - "volets Actions (développement Office dans Visual Studio), liaison de données"
  - "contrôles (développement Office dans Visual Studio), liaison de données"
  - "liaison de données (développement Office dans Visual Studio), volets Actions"
  - "liaison de données (développement Office dans Visual Studio), documents dynamiques"
  - "documents dynamiques (développement Office dans Visual Studio), liaison de données"
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es aux contr&#244;les dans un volet Actions Word
  Cette procédure pas \- à \- pas montre la liaison de données aux contrôles dans un volet Actions dans Word.  Les contrôles illustrent une relation maître\/détail entre des tables dans une base de données SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un volet Actions avec des contrôles Windows Forms liés aux données.  
  
-   Utilisation d'une relation maître\/détail afin d'afficher des données dans les contrôles.  
  
-   Affichage du volet Actions à l'ouverture de l'application.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Accès à un serveur sur lequel est installé l'exemple de base de données SQL Server Northwind.  
  
-   Autorisations d'accès en lecture et écriture à la base de données SQL Server  
  
## Création du projet  
 La première étape consiste à créer un projet de document Word.  
  
#### Pour créer un projet  
  
1.  Créez un projet de document Word et appelez\-le My Word Actions Pane.  Dans l'Assistant, sélectionnez **Créer un nouveau document**.  
  
     Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le projet **My Word Actions Pane** à l'**Explorateur de solutions**.  
  
## Ajout de contrôles au volet Actions  
 Pour cette procédure pas à pas, vous avez besoin d'un contrôle de volet Actions qui contient des contrôles Windows Forms liés aux données.  Ajoutez une source de données au projet, puis faites glisser des contrôles de la fenêtre **Sources de données** vers le contrôle de volet Actions.  
  
#### Pour ajouter un contrôle de volet Actions  
  
1.  Sélectionnez le projet **My Word Actions Pane** dans l'**Explorateur de solutions**.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Contrôle de volet Actions**, attribuez\-lui le nom **ActionsControl** et cliquez sur **Ajouter**.  
  
#### Pour ajouter une source de données au projet  
  
1.  Si la fenêtre **Sources de données** n'est pas visible, affichez\- la par, dans la barre de menus, choisissant **Afficher**, **Autres fenêtres**, **Sources de données**.  
  
    > [!NOTE]  
    >  Si **Afficher les sources de données** n'est pas disponible, cliquez dans le document Word, puis vérifiez une nouvelle fois.  
  
2.  Cliquez sur **Ajouter une nouvelle source de données** pour démarrer l'**Assistant Configuration de source de données**.  
  
3.  Sélectionnez **Base de données**, puis cliquez sur **Suivant**.  
  
4.  Sélectionnez une connexion de données pour l'exemple de base de données Northwind dans SQL Server ou ajoutez une nouvelle connexion à l'aide du bouton **Nouvelle connexion**.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Désélectionnez l'option pour enregistrer la connexion si elle est sélectionnée, puis cliquez sur **Suivant**.  
  
7.  Développez le nœud **Tables** dans la fenêtre **Objets de base de données**.  
  
8.  Activez la case à cocher en regard des tables **Suppliers** et **Products**.  
  
9. Cliquez sur **Terminer**.  
  
 L'Assistant ajoute les tables **Suppliers** et **Products** à la fenêtre **Sources de données**.  Un groupe de données typé est également ajouté à votre projet, visible dans l'**Explorateur de solutions**.  
  
#### Pour ajouter des contrôles Windows Forms liés aux données à un contrôle de volet Actions  
  
1.  Dans la fenêtre **Sources de données**, développez la table **Suppliers**.  
  
2.  Cliquez sur la flèche de déroulement du nœud **Company Name** et sélectionnez **ComboBox**.  
  
3.  Faites glisser **CompanyName** de la fenêtre **Sources de données** vers le contrôle de volet Actions.  
  
     Un contrôle <xref:System.Windows.Forms.ComboBox> est créé sur le contrôle de volet Actions.  En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `SuppliersBindingSource`, un adaptateur de table et une instance de <xref:System.Data.DataSet> sont ajoutés à la barre d'état des composants du projet.  
  
4.  Sélectionnez `SuppliersBindingNavigator` dans la barre d'état **Composant** et appuyez sur SUPPR.  Vous n'utiliserez pas le `SuppliersBindingNavigator` dans cette procédure pas à pas.  
  
    > [!NOTE]  
    >  La suppression du `SuppliersBindingNavigator` ne supprime pas la totalité du code qui a été généré pour lui.  Vous pouvez supprimer ce code.  
  
5.  Déplacez la zone de liste déroulante afin qu'elle se trouve sous l'étiquette et remplacez la valeur de la propriété **Size** par 171, 21.  
  
6.  Dans la fenêtre **Sources de données**, développez la table **Products**, enfant de la table **Suppliers**.  
  
7.  Cliquez sur la flèche de déroulement du nœud **ProductName** et sélectionnez **ListBox**.  
  
8.  Faites glisser **ProductName** jusqu'au contrôle de volet Actions.  
  
     Un contrôle <xref:System.Windows.Forms.ListBox> est créé sur le contrôle de volet Actions.  En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `ProductBindingSource` et un adaptateur de table sont ajoutés à la barre d'état des composants du projet.  
  
9. Déplacez la zone de liste afin qu'elle se trouve sous l'étiquette et remplacez la valeur de la propriété **Size** par 171,95.  
  
10. Faites glisser un <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers le contrôle de volet Actions et placez\-le au\-dessous de la zone de liste.  
  
11. Cliquez avec le bouton droit sur <xref:System.Windows.Forms.Button>, cliquez sur **Propriétés** dans le menu contextuel et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**Insert**|  
    |**du texte ;**|**Insert**|  
  
12. Redimensionnez le contrôle utilisateur pour qu'il corresponde aux contrôles.  
  
## Installation de la source de données  
 Pour installer la source de données, ajoutez du code à l'événement <xref:System.Windows.Forms.UserControl.Load> du contrôle du volet Actions pour remplir le contrôle avec des données du <xref:System.Data.DataTable> et définissez les propriétés <xref:System.Windows.Forms.Binding.DataSource%2A> et <xref:System.Windows.Forms.BindingSource.DataMember%2A> pour chaque contrôle.  
  
#### Pour charger le contrôle avec les données  
  
1.  Dans le gestionnaire d'événements <xref:System.Windows.Forms.UserControl.Load> de la classe `ActionsControl`, ajoutez le code suivant.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#1)]  
  
2.  En C\#, vous devez attacher le gestionnaire d'événements à l'événement <xref:System.Windows.Forms.UserControl.Load>.  Vous pouvez placer ce code dans le constructeur `ActionsControl`, après l'appel à `InitializeComponent`.  Pour plus d'informations sur la création des gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#33)]  
  
#### Pour définir les propriétés de liaison de données des contrôles  
  
1.  Sélectionnez le contrôle `CompanyNameComboBox`.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur le bouton à droite de la propriété **DataSource** et sélectionnez **suppliersBindingSource**.  
  
3.  Cliquez sur le bouton à droite de la propriété **DisplayMember** et sélectionnez **CompanyName**.  
  
4.  Développez la propriété **DataBindings**, cliquez sur le bouton à droite de la propriété **Text** et sélectionnez **Aucun**.  
  
5.  Sélectionnez le contrôle `ProductNameListBox`.  
  
6.  Dans la fenêtre **Propriétés**, cliquez sur le bouton à droite de la propriété **DataSource** et sélectionnez **productsBindingSource**.  
  
7.  Cliquez sur le bouton à droite de la propriété **DisplayMember** et sélectionnez **ProductName**.  
  
8.  Développez la propriété **DataBindings**, cliquez sur le bouton à droite de la propriété **SelectedValue** et sélectionnez **Aucun**.  
  
## Ajout d'une méthode pour insérer des données dans un tableau  
 La tâche suivante consiste à lire les données des contrôles dépendants et à remplir un tableau dans votre document Word.  Commencez par créer une procédure pour mettre en forme les titres dans le tableau, puis ajoutez la méthode `AddData` pour créer et mettre en forme un tableau Word.  
  
#### Pour mettre en forme les titres du tableau  
  
1.  Dans la classe `ActionsControl`, créez une méthode pour mettre en forme les titres du tableau.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#2)]
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#2)]  
  
#### Pour créer le tableau  
  
1.  Dans la classe `ActionsControl`, écrivez une méthode qui créera un tableau s'il n'en existe pas déjà un, et ajoutera les données du volet Actions au tableau.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#3)]  
  
#### Pour insérer du texte dans un tableau Word  
  
1.  Ajoutez le code suivant au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du bouton **Insérer**.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#4)]  
  
2.  En C\#, vous devez créer un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> du bouton.  Vous pouvez placer ce code dans le gestionnaire d'événements <xref:System.Windows.Forms.UserControl.Load> de la classe `ActionsControl`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#5)]  
  
## Affichage du volet Actions  
 Le volet Actions devient visible une fois que des contrôles lui ont été ajoutés.  
  
#### Pour afficher le volet Actions  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **ThisDocument.vb** ou **ThisDocument.cs**, puis cliquez sur **Afficher le code** dans le menu contextuel.  
  
2.  Créez une nouvelle instance du contrôle en haut de la classe `ThisDocument` afin qu'elle ressemble à l'exemple suivant.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#6)]  
  
3.  Ajoutez du code au gestionnaire d'événements <xref:Microsoft.Office.Tools.Word.Document.Startup> de `ThisDocument` afin qu'il ressemble à l'exemple suivant.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#7)]  
  
## Test de l'application  
 Vous pouvez maintenant tester votre document pour vérifier que le volet Actions apparaît lorsque le document est ouvert.  Testez la relation maître\/détail dans les contrôles sur le volet Actions, et assurez\-vous que ces données sont insérées dans un tableau Word lorsque l'utilisateur clique sur le bouton **Insérer**.  
  
#### Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Vérifiez que le volet Actions est visible.  
  
3.  Sélectionnez une société dans la zone de liste déroulante et vérifiez que les éléments dans la zone de liste **Produits** changent.  
  
4.  Sélectionnez un produit, cliquez sur **Insérer** dans le volet Actions et vérifiez que les détails du produit sont ajoutés au tableau dans Word.  
  
5.  Insérez des produits supplémentaires de plusieurs sociétés.  
  
## Étapes suivantes  
 Cette procédure pas à pas présente les notions de base de la liaison des données aux contrôles dans un volet Actions dans Word.  Vous devrez peut\-être ensuite exécuter les opérations suivantes :  
  
-   Liaison de données aux contrôles dans Excel.  Pour plus d'informations, consultez [Procédure pas à pas : liaison de données aux contrôles dans un volet Actions Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Déploiement du projet.  Pour plus d'informations, consultez [Déploiement d'une solution Office à l'aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Voir aussi  
 [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  