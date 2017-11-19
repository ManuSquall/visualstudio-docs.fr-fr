---
title: "Procédure pas à pas : Création d’une Relation de détail principale à l’aide d’un Dataset mis en cache | Documents Microsoft"
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
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
ms.assetid: 419f4e07-c67f-4fc9-973a-bc794f349ac3
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b392b4de0288478c73fba8cecd88be1f701cd5ae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-master-detail-relation-using-a-cached-dataset"></a>Procédure pas à pas : Création d’une Relation de détail principale à l’aide d’un Dataset mis en cache
  Cette procédure pas à pas illustre la création d’une relation maître/détail sur une feuille de calcul et de mise en cache les données afin que la solution puisse être utilisée en mode hors connexion.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Pendant cette procédure pas à pas, vous allez apprendre à :  
  
-   Ajouter des contrôles à une feuille de calcul.  
  
-   Définir un jeu de données mises en cache dans une feuille de calcul.  
  
-   Ajoutez du code pour activer le défilement des enregistrements.  
  
-   Votre projet de test.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accès à la base de données Northwind SQL Server. La base de données peut être sur votre ordinateur de développement ou sur un serveur.  
  
-   Autorisations pour lire et écrire dans la base de données SQL Server.  
  
## <a name="creating-a-new-project"></a>Création d'un projet  
 Dans cette étape, vous allez créer un projet de classeur Excel.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de classeur Excel portant le nom **maître / détail mon**, à l’aide de Visual Basic ou c#. Assurez-vous que **créer un nouveau document** est sélectionnée. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le **maître / détail Mes** projet **l’Explorateur de solutions**.  
  
## <a name="creating-the-data-source"></a>Création de la source de données  
 Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.  
  
#### <a name="to-create-the-data-source"></a>Pour créer la source de données  
  
1.  Si la fenêtre **Sources de données** n'est pas visible, affichez-la en choisissant, dans la barre de menus, **Affichage**, **Autres fenêtres**, **Sources de données**.  
  
2.  Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.  
  
3.  Sélectionnez **base de données** puis cliquez sur **suivant**.  
  
4.  Sélectionnez une connexion de données à la base de données Northwind exemple SQL Server ou ajouter une nouvelle connexion à l’aide de la **nouvelle connexion** bouton.  
  
5.  Après avoir sélectionné ou créé une connexion, cliquez sur **suivant**.  
  
6.  Désactivez l’option pour enregistrer la connexion si elle est activée, puis cliquez sur **suivant**.  
  
7.  Développez le **Tables** nœud dans le **objets de base de données** fenêtre.  
  
8.  Sélectionnez le **commandes** table et la **Order Details** table.  
  
9. Cliquez sur **Terminer**.  
  
 L’Assistant ajoute les deux tables à la **des Sources de données** fenêtre. Il ajoute également un dataset typé à votre projet qui est visible dans **l’Explorateur de solutions**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Ajout de contrôles à la feuille de calcul  
 Dans cette étape, vous allez ajouter une plage nommée, un objet de liste et deux boutons à la première feuille de calcul. Ajoutez d’abord la plage nommée et l’objet de liste à partir de la **des Sources de données** fenêtre afin qu’ils sont automatiquement liés à la source de données. Ensuite, ajoutez les boutons de la **boîte à outils**.  
  
#### <a name="to-add-a-named-range-and-a-list-object"></a>Pour ajouter une plage nommée et un objet de liste  
  
1.  Vérifiez que le **My Master-Detail.xlsx** classeur est ouvert dans le concepteur Visual Studio, avec **Feuil1** affiché.  
  
2.  Ouvrez le **des Sources de données** fenêtre et développez le **commandes** nœud.  
  
3.  Sélectionnez le **OrderID** colonne, puis cliquez sur la flèche déroulante qui s’affiche.  
  
4.  Cliquez sur **NamedRange** dans la liste déroulante, puis faites glisser le **OrderID** colonne à la cellule **A2**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle nommé `OrderIDNamedRange` est créé dans la cellule **A2**. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `OrdersBindingSource`, un adaptateur de table et un <xref:System.Data.DataSet> instance sont ajoutés au projet. Le contrôle est lié à la <xref:System.Windows.Forms.BindingSource>, qui à son tour est lié à la <xref:System.Data.DataSet> instance.  
  
5.  Faites défiler les colonnes qui sont sous la **commandes** table. Au bas de la liste est la **Order Details** table ; il est ici car il est un enfant de la **commandes** table. Sélectionnez cette option **Order Details** table, pas celui qui se trouve au même niveau que le **commandes** de table, puis cliquez sur la flèche déroulante qui s’affiche.  
  
6.  Cliquez sur **ListObject** dans la liste déroulante, puis faites glisser le **OrderDetails** table à cellule **A6**.  
  
7.  A <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle nommé **Order_DetailsListObject** est créé dans la cellule **A6**et lié à la <xref:System.Windows.Forms.BindingSource>.  
  
#### <a name="to-add-two-buttons"></a>Pour ajouter deux boutons  
  
1.  À partir de la **contrôles communs** onglet de la **boîte à outils**, ajouter un <xref:System.Windows.Forms.Button> contrôle cellule **A3** de la feuille de calcul.  
  
     Ce bouton est nommé `Button1`.  
  
2.  Ajoutez un autre <xref:System.Windows.Forms.Button> contrôle cellule **B3** de la feuille de calcul.  
  
     Ce bouton est nommé `Button2`.  
  
 Ensuite, sélectionnez le jeu de données doit être mis en cache dans le document.  
  
## <a name="caching-the-dataset"></a>La mise en cache le jeu de données  
 Marquer le jeu de données mises en cache dans le document en rendant le jeu de données publics et paramètre les **CacheInDocument** propriété.  
  
#### <a name="to-cache-the-dataset"></a>Pour mettre en cache le jeu de données  
  
1.  Sélectionnez **NorthwindDataSet** dans la barre d’état du composant.  
  
2.  Dans le **propriétés** fenêtre, de modifier le **modificateurs** propriété **Public**.  
  
     Jeux de données doit être publics avant la mise en cache est activée.  
  
3.  Modifier la **CacheInDocument** propriété **True**.  
  
 L’étape suivante consiste à ajouter du texte aux boutons et en c#, ajoutez le code pour raccorder les gestionnaires d’événements.  
  
## <a name="initializing-the-controls"></a>Initialisation des contrôles  
 Définir le texte du bouton et ajoutez des gestionnaires d’événements pendant la <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> événement.  
  
#### <a name="to-initialize-the-data-and-the-controls"></a>Pour initialiser les données et les contrôles  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **Sheet1.vb** ou **Sheet1.cs**, puis cliquez sur **afficher le Code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant à la `Sheet1_Startup` pour définir le texte des boutons.  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  Pour c# uniquement, ajouter des gestionnaires d’événements pour le bouton événements click à la `Sheet1_Startup` (méthode).  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>Ajout de Code pour activer le défilement des enregistrements  
 Ajoutez le code pour le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de chaque bouton pour parcourir les enregistrements.  
  
#### <a name="to-scroll-through-the-records"></a>Pour faire défiler les enregistrements  
  
1.  Ajouter un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> l’événement de `Button1`et ajoutez le code suivant pour vous déplacer vers l’arrière dans les enregistrements :  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  Ajouter un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> l’événement de `Button2`et ajoutez le code suivant pour faire défiler les enregistrements :  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester votre classeur pour vous assurer que les données apparaissent comme prévu et que vous pouvez utiliser la solution hors connexion.  
  
#### <a name="to-test-the-data-caching"></a>Pour tester la mise en cache de données  
  
1.  Appuyez sur **F5**.  
  
2.  Vérifiez que la plage nommée et l’objet de liste sont remplis avec des données à partir de la source de données.  
  
3.  Faites défiler quelques-uns des enregistrements en cliquant sur les boutons.  
  
4.  Enregistrez le classeur, puis fermez le classeur et Visual Studio.  
  
5.  Désactiver la connexion à la base de données. Déconnectez le câble réseau à partir de votre ordinateur si la base de données se trouve sur un serveur, ou arrêter le service SQL Server si la base de données se trouve sur votre ordinateur de développement.  
  
6.  Ouvrez Excel et ouvrez **My Master-Detail.xlsx** à partir du répertoire \bin (\My Master-Detail\bin en Visual Basic ou \My Master-Detail\bin\debug en c#).  
  
7.  Faire défiler des enregistrements pour vérifier que la feuille de calcul fonctionne normalement déconnecté.  
  
8.  Se reconnecter à la base de données. Connectez votre ordinateur au réseau à nouveau si la base de données se trouve sur un serveur, ou démarrer le service SQL Server si la base de données se trouve sur votre ordinateur de développement.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas illustre les principes fondamentaux de la création d’une relation de données maître/détail sur une feuille de calcul et de mise en cache d’un jeu de données. Voici quelques tâches susceptibles de venir après :  
  
-   Déployer la solution. Pour plus d’informations, consultez [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Données dans les Solutions Office](../vsto/data-in-office-solutions.md)   
 [Mise en cache de données](../vsto/caching-data.md)   
 [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  