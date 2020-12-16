---
title: 'Procédure pas à pas : liaison de données à des contrôles dans un volet Actions Excel'
description: Lier des données à des contrôles dans un volet actions dans Microsoft Excel. Les contrôles illustrent une relation Maître/Détail entre des tables dans une base de données SQL Server.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c53f4c1dfe9838fe4522dcc71b675a7f6b868d4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524970"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Procédure pas à pas : liaison de données à des contrôles dans un volet Actions Excel
  Cette procédure pas à pas montre comment lier des données à des contrôles dans un volet actions dans Microsoft Office Excel. Les contrôles illustrent une relation Maître/Détail entre des tables dans une base de données SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Ajout de contrôles à une feuille de calcul.

- Création d’un contrôle de volet Actions.

- Ajout de contrôles de Windows Forms liés aux données à un contrôle de volet Actions.

- Affiche le volet actions lorsque l’application s’ouvre.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accès à un serveur avec l’exemple de base de données Northwind SQL Server.

- Autorisations de lecture et d’écriture dans la base de données SQL Server.

## <a name="create-the-project"></a>Créer le projet
 La première étape consiste à créer un projet de classeur Excel.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de classeur Excel avec le nom **My Excel Actions Pane**. Dans l’Assistant, sélectionnez **créer un nouveau document**. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet **My Excel Actions Pane** à **Explorateur de solutions**.

## <a name="add-a-new-data-source-to-the-project"></a>Ajouter une nouvelle source de données au projet

### <a name="to-add-a-new-data-source-to-the-project"></a>Pour ajouter une nouvelle source de données au projet

1. Si la fenêtre **sources de données** n’est pas visible, affichez-la en cliquant sur **Afficher** d'  >  **autres**  >  **sources de données** Windows dans la barre de menus.

2. Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

3. Sélectionnez **base de données** , puis cliquez sur **suivant**.

4. Sélectionnez une connexion de données à l’exemple Northwind SQL Server base de données ou ajoutez une nouvelle connexion à l’aide du bouton **nouvelle connexion** .

5. Cliquez sur **Suivant**.

6. Désactivez l’option permettant d’enregistrer la connexion si elle est sélectionnée, puis cliquez sur **suivant**.

7. Développez le nœud **tables** dans la fenêtre **objets de base de données** .

8. Activez la case à cocher en regard de la table **Suppliers** .

9. Développez la table **Products** et sélectionnez **ProductName**, **RéfFournisseur**, **QuantityPerUnit** et **UnitPrice**.

10. Cliquez sur **Terminer**.

    L’Assistant ajoute la table **Suppliers** et la table **Products** à la fenêtre **sources de données** . Il ajoute également un DataSet typé à votre projet qui est visible dans **Explorateur de solutions**.

## <a name="add-controls-to-the-worksheet"></a>Ajouter des contrôles à la feuille de calcul
 Ensuite, ajoutez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle et un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle à la première feuille de calcul.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Pour ajouter un contrôle NamedRange et un contrôle ListObject

1. Vérifiez que le classeur **mes actions Excel Pane.xlsx** est ouvert dans le concepteur Visual Studio, avec l' `Sheet1` affichage.

2. Dans la fenêtre **sources de données** , développez la table **Suppliers** .

3. Cliquez sur la flèche déroulante du nœud nom de l' **entreprise** , puis cliquez sur **NamedRange**.

4. Faites glisser nom de la **société** de la fenêtre **sources de données** vers la cellule **a2** dans `Sheet1` .

     Un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle nommé `CompanyNameNamedRange` est créé et le texte \<CompanyName> apparaît dans la cellule **a2**. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `suppliersBindingSource` , un adaptateur de table et un <xref:System.Data.DataSet> sont ajoutés au projet. Le contrôle est lié au <xref:System.Windows.Forms.BindingSource> , qui est à son tour lié à l' <xref:System.Data.DataSet> instance.

5. Dans la fenêtre **sources de données** , faites défiler vers le dessous les colonnes qui se trouvent sous la table **Suppliers** . La table **Products** est située en bas de la liste. C’est ici parce qu’il s’agit d’un enfant de la table **Suppliers** . Sélectionnez cette table **Products** , pas celle qui se trouve au même niveau que la table **Suppliers** , puis cliquez sur la flèche déroulante qui s’affiche.

6. Dans la liste déroulante, cliquez sur **ListObject** , puis faites glisser la table **Products** vers la cellule **a6** dans `Sheet1` .

     Un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle nommé `ProductNameListObject` est créé dans la cellule **a6**. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `productsBindingSource` et un adaptateur de table sont ajoutés au projet. Le contrôle est lié au <xref:System.Windows.Forms.BindingSource> , qui est à son tour lié à l' <xref:System.Data.DataSet> instance.

7. Pour C# uniquement, sélectionnez **suppliersBindingSource** dans la barre d’état des composants, puis modifiez **la propriété** Modifiers en **interne** dans la fenêtre **Propriétés** .

## <a name="add-controls-to-the-actions-pane"></a>Ajouter des contrôles au volet Actions
 Ensuite, vous avez besoin d’un contrôle de volet actions qui a une zone de liste déroulante.

### <a name="to-add-an-actions-pane-control"></a>Pour ajouter un contrôle de volet Actions

1. Sélectionnez le projet **mon volet Actions Excel** dans **Explorateur de solutions**.

2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **contrôle du volet Actions**, nommez-le **ActionsControl**, puis cliquez sur **Ajouter**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Pour ajouter des contrôles de Windows Forms liés aux données à un contrôle de volet Actions

1. Dans les onglets **contrôles communs** de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.ComboBox> contrôle vers le contrôle du volet Actions.

2. Remplacez la valeur de la propriété **Size** par **171, 21**.

3. Redimensionnez le contrôle utilisateur pour l’ajuster à la zone de liste déroulante.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Lier le contrôle du volet actions aux données
 Dans cette section, vous allez définir la source de données du <xref:System.Windows.Forms.ComboBox> sur la même source de données que le <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle sur la feuille de calcul.

### <a name="to-set-data-binding-properties-of-the-control"></a>Pour définir les propriétés de liaison de données du contrôle

1. Cliquez avec le bouton droit sur le contrôle du volet Actions, puis cliquez sur **afficher le code**.

2. Ajoutez le code suivant à l' <xref:System.Windows.Forms.UserControl.Load> événement du contrôle de volet Actions.

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3. En C#, vous devez créer un gestionnaire d’événements pour le `ActionsControl` . Vous pouvez placer ce code dans le `ActionsControl` constructeur. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>Afficher le volet Actions
 Le volet Actions n’est pas visible tant que vous n’ajoutez pas le contrôle au moment de l’exécution.

#### <a name="to-show-the-actions-pane"></a>Pour afficher le volet Actions

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur *ThisWorkbook. vb* ou *ThisWorkbook.cs*, puis cliquez sur **afficher le code**.

2. Créez une nouvelle instance du contrôle utilisateur dans la `ThisWorkbook` classe.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3. Dans le <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> Gestionnaire d’événements de `ThisWorkbook` , ajoutez le contrôle au volet Actions.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>Test de l’application
 Vous pouvez maintenant tester votre document pour vérifier que le volet actions s’ouvre lorsque le document est ouvert et que les contrôles ont une relation maître/détail.

### <a name="to-test-your-document"></a>Pour tester votre document

1. Appuyez sur **F5** pour exécuter votre projet.

2. Vérifiez que le volet actions est visible.

3. Sélectionnez une société dans la zone de liste. Vérifiez que le nom de la société est répertorié dans le <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle et que les détails du produit sont répertoriés dans le <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle.

4. Sélectionnez différentes sociétés pour vérifier le nom de la société et les détails du produit, le cas échéant.

## <a name="next-steps"></a>Étapes suivantes
 Voici quelques tâches susceptibles de venir après :

- Liaison de données à des contrôles dans Word. Pour plus d’informations, consultez [procédure pas à pas : liaison de données à des contrôles dans un volet Actions Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

- Déploiement du projet. Pour plus d’informations, consultez [déployer une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)
- [Comment : gérer la disposition des contrôles dans les volets actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
