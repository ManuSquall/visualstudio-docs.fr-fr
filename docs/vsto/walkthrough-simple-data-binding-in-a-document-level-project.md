---
title: "Procédure pas à pas : Liaison de données Simple dans un projet au niveau du Document | Documents Microsoft"
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
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 95029c946939bf0918e15034625ad31c1e5897b9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Procédure pas à pas : liaison de données simple dans un projet au niveau du document
  Cette procédure pas à pas illustre les principes fondamentaux de la liaison de données dans un projet au niveau du document. Un champ de données dans une base de données SQL Server est lié à une plage nommée dans Microsoft Office Excel. La procédure pas à pas montre également comment ajouter des contrôles qui vous permettent de faire défiler les enregistrements dans la table.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’une source de données pour un projet Excel.  
  
-   Ajout de contrôles à une feuille de calcul.  
  
-   Défilement des enregistrements de la base de données.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accès à un serveur avec la base de données Northwind SQL Server.  
  
-   Autorisations pour lire et écrire dans la base de données SQL Server.  
  
## <a name="creating-a-new-project"></a>Création d'un projet  
 Dans cette étape, vous allez créer un projet de classeur Excel.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de classeur Excel portant le nom **une liaison de données Simple Mes**, à l’aide de Visual Basic ou c#. Assurez-vous que **créer un nouveau document** est sélectionnée. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le **une liaison de données Simple Mes** projet **l’Explorateur de solutions**.  
  
## <a name="creating-the-data-source"></a>Création de la source de données  
 Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.  
  
#### <a name="to-create-the-data-source"></a>Pour créer la source de données  
  
1.  Si la fenêtre **Sources de données** n'est pas visible, affichez-la en choisissant, dans la barre de menus, **Affichage**, **Autres fenêtres**, **Sources de données**.  
  
2.  Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.  
  
3.  Sélectionnez **base de données** puis cliquez sur **suivant**.  
  
4.  Sélectionnez une connexion de données à la base de données Northwind exemple SQL Server ou ajouter une nouvelle connexion en utilisant le **nouvelle connexion** bouton.  
  
5.  Une fois une connexion a été sélectionnée ou créée, cliquez sur **suivant**.  
  
6.  Désactivez l’option pour enregistrer la connexion si elle est activée, puis cliquez sur **suivant**.  
  
7.  Développez le **Tables** nœud dans le **objets de base de données** fenêtre.  
  
8.  Sélectionnez la case à cocher à côté du **clients** table.  
  
9. Cliquez sur **Terminer**.  
  
 L’Assistant ajoute les **clients** de la table vers le **des Sources de données** fenêtre. Il ajoute également un dataset typé à votre projet qui est visible dans **l’Explorateur de solutions**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Ajout de contrôles à la feuille de calcul  
 Pour cette procédure pas à pas, vous avez besoin de deux plages nommées et quatre boutons sur la première feuille de calcul. Tout d’abord, ajoutez les deux plages nommées à partir de la **des Sources de données** fenêtre afin qu’ils sont automatiquement liés à la source de données. Ensuite, ajoutez les boutons de la **boîte à outils**.  
  
#### <a name="to-add-two-named-ranges"></a>Pour ajouter deux plages nommées  
  
1.  Vérifiez que le **mes Binding.xlsx de données Simple** classeur est ouvert dans le concepteur Visual Studio, avec **Feuil1** affiché.  
  
2.  Ouvrez le **des Sources de données** fenêtre et développez le **clients** nœud.  
  
3.  Sélectionnez le **CompanyName** colonne, puis cliquez sur la flèche déroulante qui s’affiche.  
  
4.  Sélectionnez **NamedRange** dans la liste déroulante, puis faites glisser le **CompanyName** colonne à la cellule **A1**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle nommé `companyNameNamedRange` est créé dans la cellule **A1**. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `customersBindingSource`, un adaptateur de table et un <xref:System.Data.DataSet> instance sont ajoutés au projet. Le contrôle est lié à la <xref:System.Windows.Forms.BindingSource>, qui à son tour est lié à la <xref:System.Data.DataSet> instance.  
  
5.  Sélectionnez le **CustomerID** colonne dans la **des Sources de données** fenêtre, puis cliquez sur la flèche déroulante qui s’affiche.  
  
6.  Cliquez sur **NamedRange** dans la liste déroulante, puis faites glisser le **CustomerID** colonne à la cellule **B1**.  
  
7.  Un autre <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle nommé `customerIDNamedRange` est créé dans la cellule **B1**et lié à la <xref:System.Windows.Forms.BindingSource>.  
  
#### <a name="to-add-four-buttons"></a>Pour ajouter quatre boutons  
  
1.  À partir de la **contrôles communs** onglet de la **boîte à outils**, ajouter un <xref:System.Windows.Forms.Button> contrôle cellule **A3** de la feuille de calcul.  
  
     Ce bouton est nommé `Button1`.  
  
2.  Ajouter trois boutons supplémentaires pour les cellules suivantes dans cet ordre, afin que les noms soient comme indiqué :  
  
    |Cellule|(Nom)|  
    |----------|--------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 L’étape suivante consiste à ajouter du texte aux boutons et ajouter des gestionnaires d’événements en c#.  
  
## <a name="initializing-the-controls"></a>Initialisation des contrôles  
 Définir le texte du bouton et ajoutez des gestionnaires d’événements pendant la <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> événement.  
  
#### <a name="to-initialize-the-controls"></a>Pour initialiser les contrôles  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **Sheet1.vb** ou **Sheet1.cs**, puis cliquez sur **afficher le Code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant à la `Sheet1_Startup` méthode pour définir le texte pour chaque bouton.  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3.  Pour c# uniquement, ajouter des gestionnaires d’événements pour le bouton événements click à la `Sheet1_Startup` (méthode).  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
 Maintenant ajouter du code pour gérer les <xref:System.Windows.Forms.Control.Click> événements des boutons afin que l’utilisateur peut parcourir les enregistrements.  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>Ajout de Code pour activer le défilement des enregistrements  
 Ajoutez le code pour le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de chaque bouton pour parcourir les enregistrements.  
  
#### <a name="to-move-to-the-first-record"></a>Pour déplacer vers le premier enregistrement  
  
1.  Ajouter un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> l’événement de la `Button1` bouton et ajoutez le code suivant à déplacer vers le premier enregistrement :  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
#### <a name="to-move-to-the-previous-record"></a>Pour déplacer vers l’enregistrement précédent  
  
1.  Ajouter un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> l’événement de la `Button2` bouton et ajoutez le code suivant afin de revenir à la position précédente :  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
#### <a name="to-move-to-the-next-record"></a>Pour déplacer vers l’enregistrement suivant  
  
1.  Ajouter un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> l’événement de la `Button3` bouton et ajoutez le code suivant pour passer à la position :  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
#### <a name="to-move-to-the-last-record"></a>Pour accéder au dernier enregistrement  
  
1.  Ajouter un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> l’événement de la `Button4` bouton et ajoutez le code suivant pour accéder au dernier enregistrement :  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester votre classeur pour vous assurer que vous pouvez parcourir les enregistrements dans la base de données.  
  
#### <a name="to-test-your-workbook"></a>Pour tester votre classeur  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Vérifiez que le premier enregistrement apparaît dans les cellules **A1** et **B1**.  
  
3.  Cliquez sur le  **>**  (`Button3`) bouton et vérifiez que l’enregistrement suivant apparaît dans la cellule **A1** et **B1**.  
  
4.  Cliquez sur les autres boutons de défilement pour confirmer que l’enregistrement est modifié comme prévu.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas illustre les principes fondamentaux de la liaison d’une plage nommée à un champ dans une base de données. Voici quelques tâches susceptibles de venir après :  
  
-   Mettre en cache les données afin qu’il peut être utilisé en mode hors connexion. Pour plus d’informations, consultez [Comment : les données du Cache pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Lier des cellules à plusieurs colonnes dans une table, au lieu d’à un champ. Pour plus d’informations, consultez [procédure pas à pas : liaison de données complexe dans un projet au niveau du Document](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Utilisez un <xref:System.Windows.Forms.BindingNavigator> pour faire défiler les enregistrements de contrôle. Pour plus d’informations, consultez [Comment : parcourir les données avec le contrôle BindingNavigator Windows Forms](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Données dans les Solutions Office](../vsto/data-in-office-solutions.md)   
 [Procédure pas à pas : liaison de données complexe dans un projet au niveau du document](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  