---
title: 'Procédure pas à pas : Liaison de données complexe dans un projet au niveau du document'
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
ms.openlocfilehash: aabd45871e55fd22b9b9e35597555fd13b15d6eb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052530"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Procédure pas à pas : Liaison de données complexe dans un projet au niveau du document
  Cette procédure pas à pas illustre les principes fondamentaux de la liaison de données complexe dans un projet au niveau du document. Vous pouvez lier plusieurs cellules dans une feuille de calcul Microsoft Office Excel aux champs dans la base de données Northwind SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Ajout d’une source de données à votre projet de classeur.

- Ajout de contrôles liés aux données à une feuille de calcul.

- Enregistrer les modifications apportées aux données dans la base de données.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accès à un serveur avec la base de données Northwind SQL Server.

- Autorisations pour lire et écrire dans la base de données SQL Server.

## <a name="create-a-new-project"></a>Créer un nouveau projet
 La première étape consiste à créer un projet de classeur Excel.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créer un projet de classeur Excel portant le nom **Ma liaison de données complexe**. Dans l’Assistant, sélectionnez **créer un nouveau document**.

     Pour plus d'informations, voir [Procédure : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le **Ma liaison de données complexe** projet **l’Explorateur de solutions**.

## <a name="create-the-data-source"></a>Créer la source de données
 Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.

### <a name="to-create-the-data-source"></a>Pour créer la source de données

1. Si le **des Sources de données** fenêtre n’est pas visible, affichez-la en, sur la barre de menus, choisissez **vue** > **Windows autres**  >   **Sources de données**.

2. Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

3. Sélectionnez **base de données** puis cliquez sur **suivant**.

4. Sélectionnez une connexion de données à la base de données Northwind exemple SQL Server, ou ajouter une nouvelle connexion à l’aide de la **nouvelle connexion** bouton.

5. Une fois une connexion a été sélectionnée ou créée, cliquez sur **suivant**.

6. Désactivez l’option pour enregistrer la connexion si elle est sélectionnée, puis cliquez sur **suivant**.

7. Développez le **Tables** nœud dans le **objets de base de données** fenêtre.

8. Sélectionnez la case à cocher à côté du **employés** table.

9. Cliquez sur **Terminer**.

   L’Assistant ajoute les **employés** de la table vers le **des Sources de données** fenêtre. Il ajoute également un dataset typé à votre projet qui est visible dans **l’Explorateur de solutions**.

## <a name="add-controls-to-the-worksheet"></a>Ajouter des contrôles à la feuille de calcul
 Une feuille de calcul affichera la **employés** table lorsque le classeur est ouvert. Les utilisateurs seront en mesure d’apporter des modifications aux données et puis enregistrer ces modifications dans la base de données en cliquant sur un bouton.

 Pour lier automatiquement la feuille de calcul à la table, vous pouvez ajouter un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle à la feuille de calcul à partir de la **des Sources de données** fenêtre. Pour permettre à l’utilisateur la possibilité d’enregistrer les modifications, ajoutez un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils**.

#### <a name="to-add-a-list-object"></a>Pour ajouter un objet de liste

1. Vérifiez que le **mes Binding.xlsx de données complexe** classeur est ouvert dans le concepteur Visual Studio, avec **Sheet1** affiché.

2. Ouvrez le **des Sources de données** fenêtre et sélectionnez le **employés** nœud.

3. Cliquez sur la flèche déroulante qui s’affiche.

4. Sélectionnez **ListObject** dans la liste déroulante.

5. Faites glisser le **employés** table à cellule **A6**.

     Un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle nommé `EmployeesListObject` est créé dans la cellule **A6**. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `EmployeesBindingSource`, un adaptateur de table et un <xref:System.Data.DataSet> instance sont ajoutés au projet. Le contrôle est lié à la <xref:System.Windows.Forms.BindingSource>, qui est à son tour lié à la <xref:System.Data.DataSet> instance.

### <a name="to-add-a-button"></a>Pour ajouter un bouton

1. À partir de la **contrôles communs** onglet de la **boîte à outils**, ajouter un <xref:System.Windows.Forms.Button> contrôle de cellule **A4** de la feuille de calcul.

   L’étape suivante consiste à ajouter du texte au bouton lorsque la feuille de calcul s’ouvre.

## <a name="initialize-the-control"></a>Initialiser le contrôle
 Ajouter du texte au bouton dans le <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Gestionnaire d’événements.

### <a name="to-initialize-the-control"></a>Pour initialiser le contrôle

1. Dans **l’Explorateur de solutions**, avec le bouton droit **Sheet1.vb** ou **Sheet1.cs**, puis cliquez sur **afficher le Code** dans le menu contextuel.

2. Ajoutez le code suivant à la `Sheet1_Startup` méthode pour définir le texte de b`utton`.

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. Pour c# uniquement, ajoutez un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> événement à la `Sheet1_Startup` (méthode).

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   Maintenant ajouter du code pour gérer le <xref:System.Windows.Forms.Control.Click> événements du bouton.

## <a name="save-changes-to-the-database"></a>Enregistrer les modifications dans la base de données
 Des modifications ont été apportées pour les données existent uniquement dans le jeu de données local jusqu'à ce qu’ils sont volontairement enregistrés dans la base de données.

### <a name="to-save-changes-to-the-database"></a>Pour enregistrer les modifications apportées à la base de données

1. Ajouter un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> événements de la `button`et ajoutez le code suivant pour valider toutes les modifications qui ont été apportées dans le jeu de données à la base de données.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>Tester l’application
 Vous pouvez maintenant tester votre classeur pour vérifier que les données s’affichent comme prévu, et que vous pouvez manipuler les données dans l’objet de liste.

### <a name="to-test-the-data-binding"></a>Pour tester la liaison de données

- Appuyez sur **F5**.

     Vérifiez que lorsque le classeur s’ouvre, l’objet de liste est remplie avec les données à partir de la **employés** table.

### <a name="to-modify-data"></a>Pour modifier des données

1. Cliquez sur la cellule **B7**, qui doit contenir le nom **Davolio**.

2. Tapez le nom **Anderson**, puis appuyez sur **entrée**.

### <a name="to-modify-a-column-header"></a>Pour modifier un en-tête de colonne

1. Cliquez sur la cellule qui contient l’en-tête de colonne **LastName**.

2. Type **nom**, y compris un espace entre les deux mots, puis appuyez sur **entrée**.

### <a name="to-save-data"></a>Pour enregistrer les données

1. Cliquez sur **enregistrer** sur la feuille de calcul.

2. Quittez Excel. Cliquez sur **non** lorsque vous êtes invité à enregistrer les modifications apportées.

3. Appuyez sur **F5** à exécuter à nouveau le projet.

     L’objet de liste est remplie avec les données à partir de la **employés** table.

4. Notez que le nom dans la cellule **B7** est toujours **Anderson**, c'est-à-dire les données modifier apportées et de nouveau enregistré dans la base de données. L’en-tête de colonne **LastName** a changé sa forme d’origine sans espace, car l’en-tête de colonne n’est pas lié à la base de données et vous n’avez pas enregistré les modifications apportées à la feuille de calcul.

### <a name="to-add-new-rows"></a>Pour ajouter de nouvelles lignes

1. Sélectionnez une cellule à l’intérieur de l’objet de liste.

    Une nouvelle ligne apparaît en bas de la liste, avec un astérisque (**\\***) dans la première cellule de la nouvelle ligne.

2. Ajoutez les informations suivantes dans la ligne vide.

   |EmployeeID|LastName|FirstName|Titre|
   |----------------|--------------|---------------|-----------|
   |10|Ito|Shu|Responsable des ventes|

### <a name="to-delete-rows"></a>Pour supprimer des lignes

- Cliquez sur le nombre 16 (ligne 16) sur le côté gauche de la feuille de calcul, puis cliquez sur **supprimer**.

### <a name="to-sort-the-rows-in-the-list"></a>Pour trier les lignes dans la liste

1. Sélectionnez une cellule dans la liste.

     Boutons fléchés apparaissent dans chaque en-tête de colonne.

2. Cliquez sur la flèche dans le **nom** en-tête de colonne.

3. Cliquez sur **tri croissant**.

     Les lignes sont triées par ordre alphabétique par nom de famille.

### <a name="to-filter-information"></a>Pour filtrer les informations

1. Sélectionnez une cellule dans la liste.

2. Cliquez sur la flèche dans le **titre** en-tête de colonne.

3. Cliquez sur **commercial**.

     La liste affiche uniquement les lignes qui ont **représentant commercial** dans le **titre** colonne.

4. Cliquez sur la flèche dans le **titre** en-tête de colonne à nouveau.

5. Cliquez sur **(All)**.

     De filtrage est supprimé et toutes les lignes apparaissent.

## <a name="next-steps"></a>Étapes suivantes
 Cette procédure pas à pas montre les principes fondamentaux de la liaison d’une table dans une base de données à un objet de liste. Voici quelques tâches susceptibles de venir après :

- Mettre en cache les données afin qu’il peut être utilisé en mode hors connexion. Pour plus d'informations, voir [Procédure : Mettre en cache les données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Déployer la solution. Pour plus d’informations, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md).

- Créer une relation maître/détail entre un champ et une table. Pour plus d’informations, consultez [Procédure pas à pas : Créer une relation maître/détail à l’aide d’un dataset mis en cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).

## <a name="see-also"></a>Voir aussi
- [Lier des données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Données dans les solutions Office](../vsto/data-in-office-solutions.md)
- [Procédure pas à pas : Liaison de données simple dans un projet au niveau du document](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
