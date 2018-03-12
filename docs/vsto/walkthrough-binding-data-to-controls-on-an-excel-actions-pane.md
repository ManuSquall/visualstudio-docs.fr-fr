---
title: "Procédure pas à pas : Liaison de données aux contrôles dans un volet Actions Excel | Documents Microsoft"
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8588fef2fc5e9e4737a605e0767b8b68b2f721f4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-binding-data-to-controls-on-an-excel-actions-pane"></a>Procédure pas à pas : liaison de données aux contrôles dans un volet Actions Excel
  Cette procédure pas à pas illustre la liaison de données aux contrôles dans un volet actions dans Microsoft Office Excel. Les contrôles illustrent une relation Maître/Détail entre des tables dans une base de données SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout de contrôles à une feuille de calcul.  
  
-   Création d’un contrôle de volet actions.  
  
-   Ajout de contrôles Windows Forms liés à un contrôle de volet actions.  
  
-   Affichage du volet actions lorsque l’application s’ouvre.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accès à un serveur avec la base de données Northwind SQL Server.  
  
-   Autorisations pour lire et écrire dans la base de données SQL Server.  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer un projet de classeur Excel.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de classeur Excel portant le nom **Mon volet Actions Excel**. Dans l’Assistant, sélectionnez **créer un nouveau document**. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le **Mon volet Actions Excel** projet **l’Explorateur de solutions**.  
  
## <a name="adding-a-new-data-source-to-the-project"></a>Ajout d’une Source de données au projet  
  
#### <a name="to-add-a-new-data-source-to-the-project"></a>Pour ajouter une nouvelle source de données au projet  
  
1.  Si la fenêtre **Sources de données** n'est pas visible, affichez-la en choisissant, dans la barre de menus, **Affichage**, **Autres fenêtres**, **Sources de données**.  
  
2.  Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.  
  
3.  Sélectionnez **base de données** puis cliquez sur **suivant**.  
  
4.  Sélectionnez une connexion de données à la base de données Northwind exemple SQL Server ou ajouter une nouvelle connexion à l’aide de la **nouvelle connexion** bouton.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Désactivez l’option pour enregistrer la connexion si elle est activée, puis cliquez sur **suivant**.  
  
7.  Développez le **Tables** nœud dans le **objets de base de données** fenêtre.  
  
8.  Sélectionnez la case à cocher à côté du **fournisseurs** table.  
  
9. Développez le **produits** de table et sélectionnez **ProductName**, **SupplierID**, **QuantityPerUnit**, et **UnitPrice**.  
  
10. Cliquez sur **Terminer**.  
  
 L’Assistant ajoute les **fournisseurs** table et **produits** de la table vers le **des Sources de données** fenêtre. Il ajoute également un dataset typé à votre projet qui est visible dans **l’Explorateur de solutions**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Ajout de contrôles à la feuille de calcul  
 Ensuite, ajoutez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle et un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle à la première feuille de calcul.  
  
#### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Pour ajouter un contrôle NamedRange et un contrôle ListObject  
  
1.  Vérifiez que le **Pane.xlsx d’Actions Excel Mes** classeur est ouvert dans le concepteur Visual Studio, avec `Sheet1` affiché.  
  
2.  Dans le **des Sources de données** fenêtre, développez le **fournisseurs** table.  
  
3.  Cliquez sur la flèche déroulante du **nom de la société** nœud, puis cliquez sur **NamedRange**.  
  
4.  Faites glisser **nom de la société** à partir de la **des Sources de données** fenêtre pour la cellule **A2** dans `Sheet1`.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle nommé `CompanyNameNamedRange` est créé et le texte \<CompanyName > apparaît dans la cellule **A2**. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `suppliersBindingSource`, un adaptateur de table et un <xref:System.Data.DataSet> sont ajoutés au projet. Le contrôle est lié à la <xref:System.Windows.Forms.BindingSource>, qui à son tour est lié à la <xref:System.Data.DataSet> instance.  
  
5.  Dans le **des Sources de données** fenêtre, faites défiler vers le bas après les colonnes qui sont sous la **fournisseurs** table. Au bas de la liste est la **produits** table ; il est ici car il est un enfant de la **fournisseurs** table. Sélectionnez cette option **produits** table, pas celui qui se trouve au même niveau que le **fournisseurs** de table, puis cliquez sur la flèche déroulante qui s’affiche.  
  
6.  Cliquez sur **ListObject** dans la liste déroulante, puis faites glisser le **produits** table à cellule **A6** dans `Sheet1`.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle nommé `ProductNameListObject` est créé dans la cellule **A6**. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `productsBindingSource` et un adaptateur de table sont ajoutés au projet. Le contrôle est lié à la <xref:System.Windows.Forms.BindingSource>, qui à son tour est lié à la <xref:System.Data.DataSet> instance.  
  
7.  Pour c# uniquement, sélectionnez **suppliersBindingSource** sur la barre d’état du composant, puis remplacez le **modificateurs** propriété **interne** dans le **depropriétés** fenêtre.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Ajout de contrôles au volet Actions  
 Vous devez ensuite un contrôle de volet actions qui contient une zone de liste déroulante.  
  
#### <a name="to-add-an-actions-pane-control"></a>Pour ajouter un contrôle de volet actions  
  
1.  Sélectionnez le **Mon volet Actions Excel** projet **l’Explorateur de solutions**.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **contrôle de volet Actions**, nommez-le **ActionsControl**, puis cliquez sur **ajouter**.  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Pour ajouter des contrôles Windows Forms liés aux données à un contrôle de volet actions  
  
1.  À partir de la **contrôles communs** onglets de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.ComboBox> vers le contrôle de volet actions.  
  
2.  Modifier la **taille** propriété **171, 21**.  
  
3.  Redimensionner le contrôle utilisateur pour s’ajuster à la zone de liste déroulante.  
  
## <a name="binding-the-control-on-the-actions-pane-to-data"></a>Liaison du contrôle dans le volet Actions à des données  
 Dans cette section, vous allez définir la source de données de la <xref:System.Windows.Forms.ComboBox> à la même source de données en tant que le <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle sur la feuille de calcul.  
  
#### <a name="to-set-data-binding-properties-of-the-control"></a>Pour définir les propriétés de liaison de données du contrôle  
  
1.  Cliquez sur le contrôle de volet actions, puis cliquez sur **afficher le Code**.  
  
2.  Ajoutez le code suivant à la <xref:System.Windows.Forms.UserControl.Load> l’événement de contrôle de volet actions.  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  En c#, vous devez créer un gestionnaire d’événements pour le `ActionsControl`. Vous pouvez placer ce code dans le `ActionsControl` constructeur. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="showing-the-actions-pane"></a>Affichage du volet Actions  
 Le volet actions n’est pas visible jusqu'à ce que vous ajoutez le contrôle au moment de l’exécution.  
  
#### <a name="to-show-the-actions-pane"></a>Pour afficher le volet actions  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit ThisWorkbook.vb ou ThisWorkbook.cs, puis cliquez sur **afficher le Code**.  
  
2.  Créer une nouvelle instance du contrôle utilisateur dans la `ThisWorkbook` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  Dans le <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> Gestionnaire d’événements de `ThisWorkbook`, ajoutez le contrôle au volet actions.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester votre document pour vérifier que le volet actions s’ouvre lorsque le document est ouvert et que les contrôles ont une relation maître/détail.  
  
#### <a name="to-test-your-document"></a>Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Vérifiez que le volet actions est visible.  
  
3.  Sélectionnez une société dans la zone de liste. Vérifiez que le nom de la société est répertorié dans le <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle et que les détails du produit sont répertoriés dans le <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle.  
  
4.  Sélectionnez plusieurs sociétés pour vérifier le nom de la société et les détails sur le produit changent en conséquence.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Voici quelques tâches susceptibles de venir après :  
  
-   Liaison de données aux contrôles dans Word. Pour plus d’informations, consultez [procédure pas à pas : liaison de données aux contrôles dans un volet Actions Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   Déploiement du projet. Pour plus d’informations, consultez [déploiement d’une Solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Comment : gérer la disposition des contrôles dans les volets Actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  