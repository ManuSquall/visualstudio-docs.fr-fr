---
title: 'Procédure pas à pas : liaison de données simple dans un projet au niveau du document'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f3b573842aee5f00f161213cf3e01dfcc4c8ba93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62981060"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Procédure pas à pas : liaison de données simple dans un projet au niveau du document
  Cette procédure pas à pas montre les concepts de base de la liaison de données dans un projet au niveau du document. Un champ de données unique dans une base de données SQL Server est lié à une plage nommée dans Microsoft Office Excel. La procédure pas à pas montre également comment ajouter des contrôles qui vous permettent de faire défiler tous les enregistrements de la table.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’une source de données pour un projet Excel.

- Ajout de contrôles à une feuille de calcul.

- Défilement dans les enregistrements de base de données.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accès à un serveur avec l’exemple de base de données Northwind SQL Server.

- Autorisations de lecture et d’écriture dans la base de données SQL Server.

## <a name="create-a-new-project"></a>Création d'un projet
 Dans cette étape, vous allez créer un projet de classeur Excel.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de classeur Excel portant le nom **My simple Binding Data**, en utilisant Visual Basic ou C#. Assurez-vous que l’option **créer un nouveau document** est sélectionnée. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet **My simple Data Binding** à **Explorateur de solutions**.

## <a name="create-the-data-source"></a>Créer la source de données
 Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.

### <a name="to-create-the-data-source"></a>Pour créer la source de données

1. Si la fenêtre **sources de données** n’est pas visible, affichez-la en cliquant sur **Afficher**d'  >  **autres**  >  **sources de données**Windows dans la barre de menus.

2. Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

3. Sélectionnez **base de données** , puis cliquez sur **suivant**.

4. Sélectionnez une connexion de données à l’exemple Northwind SQL Server base de données ou ajoutez une nouvelle connexion à l’aide du bouton **nouvelle connexion** .

5. Après avoir sélectionné ou créé une connexion, cliquez sur **suivant**.

6. Désactivez l’option permettant d’enregistrer la connexion si elle est sélectionnée, puis cliquez sur **suivant**.

7. Développez le nœud **tables** dans la fenêtre **objets de base de données** .

8. Activez la case à cocher en regard de la table **Customers** .

9. Cliquez sur **Terminer**.

   L’Assistant ajoute la table **Customers** à la fenêtre **sources de données** . Il ajoute également un DataSet typé à votre projet qui est visible dans **Explorateur de solutions**.

## <a name="add-controls-to-the-worksheet"></a>Ajouter des contrôles à la feuille de calcul
 Pour cette procédure pas à pas, vous avez besoin de deux plages nommées et de quatre boutons sur la première feuille de calcul. Tout d’abord, ajoutez les deux plages nommées à partir de la fenêtre **sources de données** afin qu’elles soient automatiquement liées à la source de données. Ensuite, ajoutez les boutons de la **boîte à outils**.

### <a name="to-add-two-named-ranges"></a>Pour ajouter deux plages nommées

1. Vérifiez que le classeur *My simple Data Binding.xlsx* est ouvert dans le concepteur Visual Studio, avec **Feuil1** affiché.

2. Ouvrez la fenêtre **sources de données** et développez le nœud **Customers** .

3. Sélectionnez la colonne **CompanyName** , puis cliquez sur la flèche déroulante qui s’affiche.

4. Sélectionnez **NamedRange** dans la liste déroulante, puis faites glisser la colonne **CompanyName** vers la cellule **a1**.

     Un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle nommé `companyNameNamedRange` est créé dans la cellule **a1**. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `customersBindingSource` , un adaptateur de table et une <xref:System.Data.DataSet> instance sont ajoutés au projet. Le contrôle est lié au <xref:System.Windows.Forms.BindingSource> , qui est à son tour lié à l' <xref:System.Data.DataSet> instance.

5. Sélectionnez la colonne **CustomerID** dans la fenêtre **sources de données** , puis cliquez sur la flèche déroulante qui s’affiche.

6. Cliquez sur **NamedRange** dans la liste déroulante, puis faites glisser la colonne **CustomerID** vers la cellule **B1**.

7. Un autre <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle nommé `customerIDNamedRange` est créé dans la cellule **B1**et lié au <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-four-buttons"></a>Pour ajouter quatre boutons

1. Dans l’onglet **contrôles communs** de la **boîte à outils**, ajoutez un <xref:System.Windows.Forms.Button> contrôle à la cellule **a3** de la feuille de calcul.

    Ce bouton est nommé `Button1` .

2. Ajoutez trois boutons supplémentaires aux cellules suivantes dans cet ordre, afin que les noms soient comme indiqué :

   |Cellule|(Nom)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   L’étape suivante consiste à ajouter du texte aux boutons et, dans C#, à ajouter des gestionnaires d’événements.

## <a name="initialize-the-controls"></a>Initialiser les contrôles
 Définissez le texte du bouton et ajoutez des gestionnaires d’événements au cours de l' <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> événement.

### <a name="to-initialize-the-controls"></a>Pour initialiser les contrôles

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Feuil1. vb** ou **Sheet1.cs**, puis cliquez sur **afficher le code** dans le menu contextuel.

2. Ajoutez le code suivant à la `Sheet1_Startup` méthode pour définir le texte de chaque bouton.

    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]

3. Pour C# uniquement, ajoutez des gestionnaires d’événements pour les événements de clic de bouton à la `Sheet1_Startup` méthode.

    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]

   À présent, ajoutez du code pour gérer les <xref:System.Windows.Forms.Control.Click> événements des boutons afin que l’utilisateur puisse parcourir les enregistrements.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Ajouter du code pour permettre le défilement des enregistrements
 Ajoutez du code au <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de chaque bouton pour parcourir les enregistrements.

### <a name="to-move-to-the-first-record"></a>Pour accéder au premier enregistrement

1. Ajoutez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.Control.Click> événement du `Button1` bouton, puis ajoutez le code suivant pour accéder au premier enregistrement :

     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]

### <a name="to-move-to-the-previous-record"></a>Pour passer à l’enregistrement précédent

1. Ajoutez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.Control.Click> événement du `Button2` bouton, puis ajoutez le code suivant pour déplacer la position d’une unité vers l’arrière :

     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]

### <a name="to-move-to-the-next-record"></a>Pour passer à l’enregistrement suivant

1. Ajoutez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.Control.Click> événement du `Button3` bouton, puis ajoutez le code suivant pour avancer la position d’une unité :

     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]

### <a name="to-move-to-the-last-record"></a>Pour accéder au dernier enregistrement

1. Ajoutez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.Control.Click> événement du `Button4` bouton, puis ajoutez le code suivant pour accéder au dernier enregistrement :

     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]

## <a name="test-the-application"></a>Tester l’application
 Vous pouvez maintenant tester votre classeur pour vous assurer que vous pouvez parcourir les enregistrements de la base de données.

### <a name="to-test-your-workbook"></a>Pour tester votre classeur

1. Appuyez sur **F5** pour exécuter votre projet.

2. Confirmez que le premier enregistrement apparaît dans les cellules **a1** et **b1**.

3. Cliquez sur **>** le `Button3` bouton () et vérifiez que l’enregistrement suivant apparaît dans la cellule **a1** et **B1**.

4. Cliquez sur les autres boutons de défilement pour confirmer que l’enregistrement change comme prévu.

## <a name="next-steps"></a>Étapes suivantes
 Cette procédure pas à pas montre les principes fondamentaux de la liaison d’une plage nommée à un champ dans une base de données. Voici quelques tâches susceptibles de venir après :

- Mettez en cache les données afin qu’elles puissent être utilisées en mode hors connexion. Pour plus d’informations, consultez [Comment : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Liez des cellules à plusieurs colonnes dans une table, plutôt qu’à un champ. Pour plus d’informations, consultez [procédure pas à pas : liaison de données complexe dans un projet au niveau du document](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).

- Utilisez un <xref:System.Windows.Forms.BindingNavigator> contrôle pour faire défiler les enregistrements. Pour plus d’informations, consultez [Comment : naviguer parmi les données avec le contrôle Windows Forms BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Voir aussi
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Données dans les solutions Office](../vsto/data-in-office-solutions.md)
- [Procédure pas à pas : liaison de données complexe dans un projet au niveau du document](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
