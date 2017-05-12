---
title: "Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es aux contr&#244;les dans un volet Actions Excel"
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
ms.assetid: 106c07bd-e931-4dc5-94dc-ca43900fe09d
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es aux contr&#244;les dans un volet Actions Excel
  Cette procédure pas à pas montre la liaison de données aux contrôles dans un volet Actions de Microsoft Office Excel.  Les contrôles illustrent une relation maître\/détail entre des tables dans une base de données SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout de contrôles à une feuille de calcul  
  
-   Création d'un contrôle de volet Actions  
  
-   Ajout de contrôles Windows Forms liés aux données à un contrôle de volet Actions  
  
-   Affichage du volet Actions lorsque l'application s'ouvre  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accès à un serveur sur lequel est installé l'exemple de base de données SQL Server Northwind.  
  
-   Autorisations d'accès en lecture et écriture à la base de données SQL Server  
  
## Création du projet  
 La première étape consiste à créer un projet de classeur Excel.  
  
#### Pour créer un projet  
  
1.  Créez un projet de classeur Excel et attribuez\-lui le nom Mon volet Actions Excel.  Dans l'Assistant, sélectionnez **Créer un nouveau document**.  Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet **Mon volet Actions Excel** à l'**Explorateur de solutions**.  
  
## Ajout d'une nouvelle source de données au projet  
  
#### Pour ajouter une nouvelle source de données au projet  
  
1.  Si la fenêtre **Sources de données** n'est pas visible, affichez\- la par, dans la barre de menus, choisissant **Afficher**, **Autres fenêtres**, **Sources de données**.  
  
2.  Choisissez **Ajouter une nouvelle source de données** pour démarrer **Assistant Configuration de source de données**.  
  
3.  Sélectionnez **Base de données**, puis cliquez sur **Suivant**.  
  
4.  Sélectionnez une connexion de données pour l'exemple de base de données Northwind dans SQL Server ou ajoutez une nouvelle connexion à l'aide du bouton **Nouvelle connexion**.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Désélectionnez l'option pour enregistrer la connexion si elle est sélectionnée, puis cliquez sur **Suivant**.  
  
7.  Développez le nœud **Tables** dans la fenêtre **Objets de base de données**.  
  
8.  Activez la case à cocher située à côté de la table **Suppliers**.  
  
9. Développez la table **Products** et sélectionnez **ProductName**, **SupplierID**, **QuantityPerUnit** et **UnitPrice**.  
  
10. Cliquez sur **Terminer**.  
  
 L'Assistant ajoute les tables **Suppliers** et **Products** à la fenêtre **Sources de données**.  Un groupe de données typé est également ajouté à votre projet, visible dans l'**Explorateur de solutions**.  
  
## Ajout de contrôles à la feuille de calcul  
 Ensuite, ajoutez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> et un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> à la première feuille de calcul.  
  
#### Pour ajouter un contrôle NamedRange et un contrôle ListObject  
  
1.  Vérifiez que le classeur **Mes actions Pane.xlsx excel** est ouvert dans le concepteur Visual Studio, avec `Sheet1` a affiché.  
  
2.  Dans la fenêtre **Sources de données**, développez la table **Suppliers**.  
  
3.  Cliquez sur la flèche de déroulement du nœud **Company Name**, puis cliquez sur **NamedRange**.  
  
4.  Faites glisser **Company Name** de la fenêtre **Sources de données** vers la cellule **A2** dans `Sheet1`.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> nommé `CompanyNameNamedRange` est créé, et le texte \<CompanyName\> apparaît dans la cellule **A2**.  En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `suppliersBindingSource`, un adaptateur de table et une instance de <xref:System.Data.DataSet> sont ajoutés au projet.  Le contrôle est lié à <xref:System.Windows.Forms.BindingSource>, qui est lié à son tour à l'instance de <xref:System.Data.DataSet>.  
  
5.  Dans la fenêtre **Sources de données**, faites défiler les colonnes qui sont sous la table **Suppliers**.  À la fin de la liste se trouve la table **Products** ; elle est située à cet endroit car il s'agit d'un enfant de la table **Suppliers**.  Sélectionnez cette table **Products**, et non celle située au même niveau que la table **Suppliers**, puis cliquez sur la flèche de déroulement qui apparaît.  
  
6.  Cliquez sur **ListObject** dans la liste déroulante, puis faites glisser la table **Products** vers la cellule **A6** dans `Sheet1`.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `ProductNameListObject` est créé dans la cellule **A6**.  En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `productsBindingSource` et un adaptateur de table sont ajoutés au projet.  Le contrôle est lié à <xref:System.Windows.Forms.BindingSource>, qui est lié à son tour à l'instance de <xref:System.Data.DataSet>.  
  
7.  Pour C\# uniquement, sélectionnez **suppliersBindingSource** dans la barre d'état des composants et remplacez la valeur de la propriété **Modifiers** par Internal dans la fenêtre **Propriétés**.  
  
## Ajout de contrôles au volet Actions  
 Ensuite, vous avez besoin d'un contrôle de volet Actions qui contient une zone de liste déroulante.  
  
#### Pour ajouter un contrôle de volet Actions  
  
1.  Sélectionnez le projet **Mon volet Actions Excel** dans l'**Explorateur de solutions**.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Contrôle de volet Actions**, attribuez\-lui le nom **ActionsControl**, puis cliquez sur **Ajouter**.  
  
#### Pour ajouter des contrôles Windows Forms liés aux données à un contrôle de volet Actions  
  
1.  À partir de l'onglet **Contrôles communs** de la **Boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.ComboBox> vers le contrôle de volet Actions.  
  
2.  Remplacez la valeur de la propriété **Size** par 171, 21.  
  
3.  Redimensionnez le contrôle utilisateur en fonction de la zone de liste déroulante.  
  
## Liaison du contrôle sur le volet Actions à des données  
 Dans cette section, vous ferez correspondre la source de données de <xref:System.Windows.Forms.ComboBox> et la source de données du contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> sur la feuille de calcul.  
  
#### Pour définir les propriétés de liaison de données du contrôle  
  
1.  Cliquez avec le bouton droit sur le contrôle de volet Actions, puis cliquez sur **Afficher le code**.  
  
2.  Ajoutez le code suivant à l'événement <xref:System.Windows.Forms.UserControl.Load> du contrôle de volet Actions.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ActionsControl.vb#1)]  
  
3.  En C\#, vous devez créer un gestionnaire d'événements pour `ActionsControl`.  Vous pouvez placer ce code dans le constructeur `ActionsControl`.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#2)]  
  
## Affichage du volet Actions  
 Le volet Actions n'est visible que lorsque vous ajoutez le contrôle au moment de l'exécution.  
  
#### Pour afficher le volet Actions  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur ThisWorkbook.vb ou ThisWorkbook.cs, puis cliquez sur **Afficher le code**.  
  
2.  Créez une instance du contrôle utilisateur dans la classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#3)]  
  
3.  Dans le gestionnaire d'événements <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> de `ThisWorkbook`, ajoutez le contrôle au volet Actions.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#4)]  
  
## Test de l'application  
 Vous pouvez à présent tester votre document pour vérifier que le volet Actions s'ouvre en même temps que le document et que les contrôles disposent d'une relation maître\/détail.  
  
#### Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Vérifiez que le volet Actions est visible.  
  
3.  Sélectionnez une société dans la zone de liste.  Vérifiez que le nom de la société est répertorié dans le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> et que les détails sur le produit sont affichés dans le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
4.  Sélectionnez plusieurs sociétés pour vérifier que le nom de la société et les détails sur le produit changent en conséquence.  
  
## Étapes suivantes  
 Vous devrez peut\-être ensuite exécuter les opérations suivantes :  
  
-   Liaison de données aux contrôles dans Word.  Pour plus d'informations, consultez [Procédure pas à pas : liaison de données aux contrôles dans un volet Actions Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   Déploiement du projet.  Pour plus d'informations, consultez [Déploiement d'une solution Office à l'aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Voir aussi  
 [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Comment : gérer la disposition des contrôles dans les volets Actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  