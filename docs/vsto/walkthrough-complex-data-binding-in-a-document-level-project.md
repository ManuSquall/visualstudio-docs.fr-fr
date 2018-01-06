---
title: "Procédure pas à pas : Liaison de données complexe dans un projet au niveau du Document | Documents Microsoft"
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
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
ms.assetid: 32ffad3d-fba4-476a-99b8-ef440434f4e1
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 10d35a0cec1e927fbc264d64ef911503f68f1606
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Procédure pas à pas : liaison de données complexe dans un projet au niveau du document
  Cette procédure pas à pas illustre les principes fondamentaux de la liaison de données complexe dans un projet au niveau du document. Vous pouvez lier plusieurs cellules dans une feuille de calcul Microsoft Office Excel aux champs de la base de données Northwind SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout d’une source de données à votre projet de classeur.  
  
-   Ajout de contrôles liés aux données à une feuille de calcul.  
  
-   Enregistrer les modifications de données dans la base de données.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accès à un serveur avec la base de données Northwind SQL Server.  
  
-   Autorisations pour lire et écrire dans la base de données SQL Server.  
  
## <a name="creating-a-new-project"></a>Création d'un projet  
 La première étape consiste à créer un projet de classeur Excel.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de classeur Excel portant le nom **une liaison de données complexe Mes**. Dans l’Assistant, sélectionnez **créer un nouveau document**.  
  
     Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le **une liaison de données complexe Mes** projet **l’Explorateur de solutions**.  
  
## <a name="creating-the-data-source"></a>Création de la source de données  
 Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.  
  
#### <a name="to-create-the-data-source"></a>Pour créer la source de données  
  
1.  Si la fenêtre **Sources de données** n'est pas visible, affichez-la en choisissant, dans la barre de menus, **Affichage**, **Autres fenêtres**, **Sources de données**.  
  
2.  Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.  
  
3.  Sélectionnez **base de données** puis cliquez sur **suivant**.  
  
4.  Sélectionnez une connexion de données à la base de données Northwind exemple SQL Server ou ajouter une nouvelle connexion à l’aide de la **nouvelle connexion** bouton.  
  
5.  Une fois une connexion a été sélectionnée ou créée, cliquez sur **suivant**.  
  
6.  Désactivez l’option pour enregistrer la connexion si elle est activée, puis cliquez sur **suivant**.  
  
7.  Développez le **Tables** nœud dans le **objets de base de données** fenêtre.  
  
8.  Sélectionnez la case à cocher à côté du **employés** table.  
  
9. Cliquez sur **Terminer**.  
  
 L’Assistant ajoute les **employés** de la table vers le **des Sources de données** fenêtre. Il ajoute également un dataset typé à votre projet qui est visible dans **l’Explorateur de solutions**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Ajout de contrôles à la feuille de calcul  
 Affiche une feuille de calcul le **employés** table lorsque le classeur est ouvert. Les utilisateurs seront en mesure d’apporter des modifications aux données et enregistrez ensuite ces modifications sur la base de données en cliquant sur un bouton.  
  
 Pour lier la feuille de calcul à la table automatiquement, vous pouvez ajouter un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle à la feuille de calcul à partir de la **des Sources de données** fenêtre. Pour permettre à l’utilisateur la possibilité d’enregistrer les modifications, ajoutez un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils**.  
  
#### <a name="to-add-a-list-object"></a>Pour ajouter un objet de liste  
  
1.  Vérifiez que le **mes Binding.xlsx de données complexe** classeur est ouvert dans le concepteur Visual Studio, avec **Feuil1** affiché.  
  
2.  Ouvrez le **des Sources de données** et sélectionnez le **employés** nœud.  
  
3.  Cliquez sur la flèche déroulante qui s’affiche.  
  
4.  Sélectionnez **ListObject** dans la liste déroulante.  
  
5.  Faites glisser le **employés** table à cellule **A6**.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle nommé `EmployeesListObject` est créé dans la cellule **A6**. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `EmployeesBindingSource`, un adaptateur de table et un <xref:System.Data.DataSet> instance sont ajoutés au projet. Le contrôle est lié à la <xref:System.Windows.Forms.BindingSource>, qui à son tour est lié à la <xref:System.Data.DataSet> instance.  
  
#### <a name="to-add-a-button"></a>Pour ajouter un bouton  
  
1.  À partir de la **contrôles communs** onglet de la **boîte à outils**, ajouter un <xref:System.Windows.Forms.Button> contrôle cellule **A4** de la feuille de calcul.  
  
 L’étape suivante consiste à ajouter du texte au bouton lorsque la feuille de calcul s’ouvre.  
  
## <a name="initializing-the-control"></a>Initialisation du contrôle  
 Ajouter du texte au bouton dans le <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Gestionnaire d’événements.  
  
#### <a name="to-initialize-the-control"></a>Pour initialiser le contrôle  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **Sheet1.vb** ou **Sheet1.cs**, puis cliquez sur **afficher le Code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant à la `Sheet1_Startup` pour définir le texte de la b`utton`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]  
  
3.  Pour c# uniquement, ajoutez un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> événement à la `Sheet1_Startup` (méthode).  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]  
  
 Maintenant ajouter du code pour gérer les <xref:System.Windows.Forms.Control.Click> événements du bouton.  
  
## <a name="saving-changes-to-the-database"></a>Enregistrement des modifications apportées à la base de données  
 Des modifications ont été apportées pour les données existent uniquement dans le jeu de données local jusqu'à ce qu’elles sont enregistrées explicitement à la base de données.  
  
#### <a name="to-save-changes-to-the-database"></a>Pour enregistrer les modifications apportées à la base de données  
  
1.  Ajouter un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> l’événement de la b`utton`et ajoutez le code suivant pour valider toutes les modifications qui ont été apportées dans le jeu de données à la base de données.  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester votre classeur pour vérifier que les données s’affiche comme prévu, et que vous pouvez manipuler les données dans l’objet de liste.  
  
#### <a name="to-test-the-data-binding"></a>Pour tester la liaison de données  
  
-   Appuyez sur F5.  
  
     Vérifiez que lorsque le classeur s’ouvre, l’objet de liste est remplie avec des données à partir de la **employés** table.  
  
#### <a name="to-modify-data"></a>Pour modifier des données  
  
1.  Cliquez sur la cellule **B7**, qui doit contenir le nom **Davolio**.  
  
2.  Tapez le nom **Anderson**, puis appuyez sur ENTRÉE.  
  
#### <a name="to-modify-a-column-header"></a>Pour modifier un en-tête de colonne  
  
1.  Cliquez sur la cellule qui contient l’en-tête de colonne **LastName**.  
  
2.  Type **nom**, y compris un espace entre les deux mots, puis appuyez sur ENTRÉE.  
  
#### <a name="to-save-data"></a>Pour enregistrer des données  
  
1.  Cliquez sur **enregistrer** sur la feuille de calcul.  
  
2.  Quittez Excel. Cliquez sur **non** lorsque vous êtes invité à enregistrer les modifications apportées.  
  
3.  Appuyez sur F5 pour exécuter de nouveau le projet.  
  
     L’objet de liste est remplie avec les données à partir de la **employés** table.  
  
4.  Notez que le nom dans la cellule **B7** est toujours **Anderson**, qui correspond aux données de modification que vous effectuées et enregistrées dans la base de données. L’en-tête de colonne **LastName** a changé sa forme d’origine sans espace, car l’en-tête de colonne n’est pas lié à la base de données et vous n’avez pas enregistré les modifications apportées à la feuille de calcul.  
  
#### <a name="to-add-new-rows"></a>Pour ajouter de nouvelles lignes  
  
1.  Sélectionnez une cellule à l’intérieur de l’objet de liste.  
  
     Une nouvelle ligne apparaît au bas de la liste, avec un astérisque (**\***) dans la première cellule de la nouvelle ligne.  
  
2.  Ajoutez les informations suivantes dans la ligne vide.  
  
    |EmployeeID|LastName|FirstName|Titre|  
    |----------------|--------------|---------------|-----------|  
    |10|Ito|Shu|Responsable des ventes|  
  
#### <a name="to-delete-rows"></a>Pour supprimer des lignes  
  
-   Cliquez sur le nombre 16 (ligne 16) sur le côté gauche de la feuille de calcul, puis cliquez sur **supprimer**.  
  
#### <a name="to-sort-the-rows-in-the-list"></a>Pour trier les lignes dans la liste  
  
1.  Sélectionnez une cellule dans la liste.  
  
     Boutons fléchés apparaissent dans chaque en-tête de colonne.  
  
2.  Cliquez sur la flèche dans le **nom** en-tête de colonne.  
  
3.  Cliquez sur **tri croissant**.  
  
     Les lignes sont triées par ordre alphabétique par nom.  
  
#### <a name="to-filter-information"></a>Pour filtrer les informations  
  
1.  Sélectionnez une cellule dans la liste.  
  
2.  Cliquez sur la flèche dans le **titre** en-tête de colonne.  
  
3.  Cliquez sur **commercial**.  
  
     La liste affiche uniquement les lignes qui ont **représentant commercial** dans les **titre** colonne.  
  
4.  Cliquez sur la flèche dans le **titre** à nouveau les en-tête de colonne.  
  
5.  Cliquez sur **(tous)**.  
  
     Le filtrage est supprimé et toutes les lignes apparaissent.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas illustre les principes fondamentaux de la liaison d’une table dans une base de données à un objet de liste. Voici quelques tâches susceptibles de venir après :  
  
-   Mettre en cache les données afin qu’il peut être utilisé en mode hors connexion. Pour plus d’informations, consultez [Comment : les données du Cache pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Déployer la solution. Pour plus d’informations, consultez [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md).  
  
-   Créer une relation maître/détail entre un champ et une table. Pour plus d’informations, consultez [procédure pas à pas : création d’une Relation de détail de Master à l’aide d’un Dataset mis en cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Données dans les Solutions Office](../vsto/data-in-office-solutions.md)   
 [Procédure pas à pas : liaison de données simple dans un projet au niveau du document](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  