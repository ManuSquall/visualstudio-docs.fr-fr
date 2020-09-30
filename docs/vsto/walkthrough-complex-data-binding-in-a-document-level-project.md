---
title: 'Procédure pas à pas : liaison de données complexe dans un projet au niveau du document'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7aba307bcd76cc055e42c11418d42f3dd0cfba1f
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584319"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Procédure pas à pas : liaison de données complexe dans un projet au niveau du document
  Cette procédure pas à pas montre les concepts de base de la liaison de données complexe dans un projet au niveau du document. Vous pouvez lier plusieurs cellules d’un Microsoft Office feuille de calcul Excel aux champs de la base de données Northwind SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Ajout d’une source de données à votre projet de classeur.

- Ajout de contrôles liés aux données à une feuille de calcul.

- Enregistrement des modifications apportées aux données dans la base de données.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accès à un serveur avec l’exemple de base de données Northwind SQL Server.

- Autorisations de lecture et d’écriture dans la base de données SQL Server.

## <a name="create-a-new-project"></a>Créer un projet
 La première étape consiste à créer un projet de classeur Excel.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de classeur Excel portant le nom **mes liaisons de données complexes**. Dans l’Assistant, sélectionnez **créer un nouveau document**.

     Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet de **liaison de données complexe** à **Explorateur de solutions**.

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

8. Activez la case à cocher en regard de la table **Employees** .

9. Cliquez sur **Terminer**.

   L’Assistant ajoute la table **Employees** à la fenêtre **sources de données** . Il ajoute également un DataSet typé à votre projet qui est visible dans **Explorateur de solutions**.

## <a name="add-controls-to-the-worksheet"></a>Ajouter des contrôles à la feuille de calcul
 Une feuille de calcul affiche la table **Employees** lorsque le classeur est ouvert. Les utilisateurs seront en mesure d’apporter des modifications aux données, puis d’enregistrer ces modifications dans la base de données en cliquant sur un bouton.

 Pour lier automatiquement la feuille de calcul à la table, vous pouvez ajouter un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle à la feuille de calcul à partir de la fenêtre **sources de données** . Pour permettre à l’utilisateur d’enregistrer les modifications, ajoutez un <xref:System.Windows.Forms.Button> contrôle à partir de la **boîte à outils**.

#### <a name="to-add-a-list-object"></a>Pour ajouter un objet de liste

1. Vérifiez que le classeur **My Complex Data Binding.xlsx** est ouvert dans le concepteur Visual Studio, avec **Feuil1** affiché.

2. Ouvrez la fenêtre **sources de données** et sélectionnez le nœud **Employees** .

3. Cliquez sur la flèche déroulante qui s’affiche.

4. Sélectionnez **ListObject** dans la liste déroulante.

5. Faites glisser la table **Employees** vers la cellule **a6**.

     Un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle nommé `EmployeesListObject` est créé dans la cellule **a6**. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `EmployeesBindingSource` , un adaptateur de table et une <xref:System.Data.DataSet> instance sont ajoutés au projet. Le contrôle est lié au <xref:System.Windows.Forms.BindingSource> , qui est à son tour lié à l' <xref:System.Data.DataSet> instance.

### <a name="to-add-a-button"></a>Pour ajouter un bouton

1. À partir de l’onglet **contrôles communs** de la **boîte à outils**, ajoutez un <xref:System.Windows.Forms.Button> contrôle à la cellule **a4** de la feuille de calcul.

   L’étape suivante consiste à ajouter du texte au bouton lorsque la feuille de calcul s’ouvre.

## <a name="initialize-the-control"></a>Initialiser le contrôle
 Ajoutez du texte au bouton dans le <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Gestionnaire d’événements.

### <a name="to-initialize-the-control"></a>Pour initialiser le contrôle

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Feuil1. vb** ou **Sheet1.cs**, puis cliquez sur **afficher le code** dans le menu contextuel.

2. Ajoutez le code suivant à la `Sheet1_Startup` méthode pour définir le texte pour le b `utton` .

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. Pour C# uniquement, ajoutez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.Control.Click> événement à la `Sheet1_Startup` méthode.

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   Ajoutez maintenant le code pour gérer l' <xref:System.Windows.Forms.Control.Click> événement du bouton.

## <a name="save-changes-to-the-database"></a>Enregistrer les modifications apportées à la base de données
 Toutes les modifications apportées aux données existent uniquement dans le DataSet local jusqu’à ce qu’elles soient explicitement enregistrées dans la base de données.

### <a name="to-save-changes-to-the-database"></a>Pour enregistrer les modifications apportées à la base de données

1. Ajoutez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.Control.Click> événement du `button` , puis ajoutez le code suivant pour valider toutes les modifications apportées dans le DataSet à la base de données.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>Test de l’application
 Vous pouvez maintenant tester votre classeur pour vérifier que les données apparaissent comme prévu et que vous pouvez manipuler les données dans l’objet de liste.

### <a name="to-test-the-data-binding"></a>Pour tester la liaison de données

- Appuyez sur **F5**.

     Vérifiez que lorsque le classeur s’ouvre, l’objet de liste est rempli avec les données de la table **Employees** .

### <a name="to-modify-data"></a>Pour modifier des données

1. Cliquez sur la cellule **B7**, qui doit contenir le nom **Davolio**.

2. Tapez le nom **Anderson**, puis appuyez sur **entrée**.

### <a name="to-modify-a-column-header"></a>Pour modifier un en-tête de colonne

1. Cliquez sur la cellule qui contient l’en-tête de colonne **LastName**.

2. Tapez **Last Name**, y compris un espace entre les deux mots, puis appuyez sur **entrée**.

### <a name="to-save-data"></a>Pour enregistrer des données

1. Cliquez sur **Enregistrer** dans la feuille de calcul.

2. Quittez Excel. Cliquez sur **non** lorsque vous y êtes invité pour enregistrer les modifications que vous avez apportées.

3. Appuyez sur **F5** pour réexécuter le projet.

     L’objet de liste est rempli avec les données de la table **Employees** .

4. Notez que le nom dans la cellule **B7** est toujours **Anderson**, ce qui correspond à la modification de données que vous avez apportée et enregistrée dans la base de données. L’en-tête de colonne **LastName** est revenu à sa forme d’origine sans espace, car l’en-tête de colonne n’est pas lié à la base de données et vous n’avez pas enregistré les modifications que vous avez apportées à la feuille de calcul.

### <a name="to-add-new-rows"></a>Pour ajouter de nouvelles lignes

1. Sélectionnez une cellule à l’intérieur de l’objet de liste.

    Une nouvelle ligne apparaît en bas de la liste, avec un astérisque ( **\*** ) dans la première cellule de la nouvelle ligne.

2. Ajoutez les informations suivantes dans la ligne vide.

   |EmployeeID (IDEmployé)|LastName|FirstName|Titre|
   |----------------|--------------|---------------|-----------|
   |10|Ito|Shu|Directeur commercial|

### <a name="to-delete-rows"></a>Suppression de lignes

- Cliquez avec le bouton droit sur le nombre 16 (ligne 16) situé à l’extrême gauche de la feuille de calcul, puis cliquez sur **supprimer**.

### <a name="to-sort-the-rows-in-the-list"></a>Pour trier les lignes de la liste

1. Sélectionnez une cellule à l’intérieur de la liste.

     Les boutons fléchés s’affichent dans chaque en-tête de colonne.

2. Cliquez sur le bouton fléché dans l’en-tête de colonne **Last Name** .

3. Cliquez sur **Tri croissant**.

     Les lignes sont triées par ordre alphabétique par nom.

### <a name="to-filter-information"></a>Pour filtrer les informations

1. Sélectionnez une cellule à l’intérieur de la liste.

2. Cliquez sur le bouton fléché dans l’en-tête de colonne **titre** .

3. Cliquez **sur commercial.**

     La liste affiche uniquement les lignes qui ont un **commercial** dans la colonne **titre** .

4. Cliquez à nouveau sur le bouton fléché dans l’en-tête de colonne **titre** .

5. Cliquez sur **(tout)**.

     Le filtrage est supprimé et toutes les lignes s’affichent.

## <a name="next-steps"></a>Étapes suivantes
 Cette procédure pas à pas montre les principes fondamentaux de la liaison d’une table dans une base de données à un objet de liste. Voici quelques tâches susceptibles de venir après :

- Mettez en cache les données afin qu’elles puissent être utilisées en mode hors connexion. Pour plus d’informations, consultez [Comment : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- déployer la solution ; Pour plus d’informations, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md).

- Créer une relation maître/détail entre un champ et une table. Pour plus d’informations, consultez [procédure pas à pas : créer une relation de détail maître à l’aide d’un DataSet mis en cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).

## <a name="see-also"></a>Voir aussi
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Données dans les solutions Office](../vsto/data-in-office-solutions.md)
- [Procédure pas à pas : liaison de données simple dans un projet au niveau du document](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
