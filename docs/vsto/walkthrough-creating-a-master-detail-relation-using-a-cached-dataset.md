---
title: 'Procédure pas à pas : Créer une relation maître/détail à l’aide d’un dataset mis en cache'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3380b9c5302ed6e8a1bf6965f5fb1f259e3a6682
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438551"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Procédure pas à pas : Créer une relation maître/détail à l’aide d’un dataset mis en cache
  Cette procédure pas à pas montre comment créer une relation maître/détail sur une feuille de calcul et la mise en cache les données afin que la solution puisse être utilisée hors connexion.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Pendant cette procédure pas à pas, vous allez apprendre à :

- Ajouter des contrôles à une feuille de calcul.

- Configurer un jeu de données doit être mis en cache dans une feuille de calcul.

- Ajoutez du code pour activer le défilement des enregistrements.

- Votre projet de test.

> [!NOTE]
> Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accès à la base de données Northwind SQL Server. La base de données peut être sur votre ordinateur de développement ou sur un serveur.

- Autorisations pour lire et écrire dans la base de données SQL Server.

## <a name="create-a-new-project"></a>Créer un nouveau projet
 Dans cette étape, vous allez créer un projet de classeur Excel.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créer un projet de classeur Excel portant le nom **maître-détail mon**, à l’aide de Visual Basic ou c#. Assurez-vous que l’option **créer un nouveau document** est sélectionné. Pour plus d'informations, voir [Procédure : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le **maître-détail mon** projet **l’Explorateur de solutions**.

## <a name="create-the-data-source"></a>Créer la source de données
 Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.

### <a name="to-create-the-data-source"></a>Pour créer la source de données

1. Si le **des Sources de données** fenêtre n’est pas visible, affichez-la en, sur la barre de menus, choisissez **vue** > **Windows autres**  >   **Sources de données**.

2. Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

3. Sélectionnez **base de données** puis cliquez sur **suivant**.

4. Sélectionnez une connexion de données à la base de données Northwind exemple SQL Server, ou ajouter une nouvelle connexion à l’aide de la **nouvelle connexion** bouton.

5. Après avoir sélectionné ou créé une connexion, cliquez sur **suivant**.

6. Désactivez l’option pour enregistrer la connexion si elle est sélectionnée, puis cliquez sur **suivant**.

7. Développez le **Tables** nœud dans le **objets de base de données** fenêtre.

8. Sélectionnez le **commandes** table et le **Order Details** table.

9. Cliquez sur **Terminer**.

   L’Assistant ajoute les deux tables à la **des Sources de données** fenêtre. Il ajoute également un dataset typé à votre projet qui est visible dans **l’Explorateur de solutions**.

## <a name="add-controls-to-the-worksheet"></a>Ajouter des contrôles à la feuille de calcul
 Dans cette étape, vous ajouterez une plage nommée, un objet de liste et deux boutons à la première feuille de calcul. Tout d’abord, ajoutez la plage nommée et l’objet de liste à partir de la **des Sources de données** fenêtre afin qu’ils sont automatiquement liés à la source de données. Ensuite, ajoutez les boutons de la **boîte à outils**.

### <a name="to-add-a-named-range-and-a-list-object"></a>Pour ajouter une plage nommée et un objet de liste

1. Vérifiez que le **mes Master-Detail.xlsx** classeur est ouvert dans le concepteur Visual Studio, avec **Sheet1** affiché.

2. Ouvrez le **des Sources de données** fenêtre et développez le **commandes** nœud.

3. Sélectionnez le **OrderID** colonne, puis cliquez sur la flèche déroulante qui s’affiche.

4. Cliquez sur **NamedRange** dans la liste déroulante, puis faites glisser le **OrderID** colonne à la cellule **A2**.

     Un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle nommé `OrderIDNamedRange` est créé dans la cellule **A2**. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `OrdersBindingSource`, un adaptateur de table et un <xref:System.Data.DataSet> instance sont ajoutés au projet. Le contrôle est lié à la <xref:System.Windows.Forms.BindingSource>, qui est à son tour lié à la <xref:System.Data.DataSet> instance.

5. Faites défiler vers le bas les colonnes qui sont sous la **commandes** table. En bas de la liste est la **Order Details** table ; il est ici, car c’est un enfant de la **commandes** table. Sélectionnez cette option **Order Details** table, pas celui qui se trouve au même niveau que le **commandes** de table, puis cliquez sur la flèche déroulante qui s’affiche.

6. Cliquez sur **ListObject** dans la liste déroulante, puis faites glisser le **OrderDetails** table à cellule **A6**.

7. Un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle nommé **Order_DetailsListObject** est créé dans la cellule **A6**et liée à la <xref:System.Windows.Forms.BindingSource>.

### <a name="to-add-two-buttons"></a>Pour ajouter deux boutons

1. À partir de la **contrôles communs** onglet de la **boîte à outils**, ajouter un <xref:System.Windows.Forms.Button> contrôle de cellule **A3** de la feuille de calcul.

    Ce bouton était nommé `Button1`.

2. Ajoutez un autre <xref:System.Windows.Forms.Button> contrôle de cellule **B3** de la feuille de calcul.

    Ce bouton était nommé `Button2`.

   Ensuite, sélectionnez le jeu de données doit être mis en cache dans le document.

## <a name="cache-the-dataset"></a>Mettre en cache le jeu de données
 Marquer le jeu de données à mettre en cache dans le document en rendant le jeu de données publics et paramètre les **CacheInDocument** propriété.

### <a name="to-cache-the-dataset"></a>Pour mettre en cache le jeu de données

1. Sélectionnez **NorthwindDataSet** dans la barre d’état du composant.

2. Dans le **propriétés** fenêtre, modifier le **modificateurs** propriété **Public**.

    Jeux de données doit être publiques avant la mise en cache est activée.

3. Modifier le **CacheInDocument** propriété **True**.

   L’étape suivante consiste à ajouter du texte aux boutons et en c#, ajoutez le code pour raccorder les gestionnaires d’événements.

## <a name="initialize-the-controls"></a>Initialiser les contrôles
 Définissez le texte du bouton et ajoutez des gestionnaires d’événements pendant la <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> événement.

### <a name="to-initialize-the-data-and-the-controls"></a>Pour initialiser les données et les contrôles

1. Dans **l’Explorateur de solutions**, avec le bouton droit **Sheet1.vb** ou **Sheet1.cs**, puis cliquez sur **afficher le Code** dans le menu contextuel.

2. Ajoutez le code suivant à la `Sheet1_Startup` méthode pour définir le texte pour les boutons.

     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]

3. Pour c# uniquement, ajoutez des gestionnaires d’événements pour le bouton événements click à la `Sheet1_Startup` (méthode).

     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Ajoutez du code pour activer le défilement des enregistrements
 Ajoutez le code pour le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de chaque bouton pour parcourir les enregistrements.

### <a name="to-scroll-through-the-records"></a>Pour faire défiler les enregistrements

1. Ajouter un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> événement de `Button1`et ajoutez le code suivant pour vous déplacer vers l’arrière dans les enregistrements :

     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]

2. Ajouter un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> événement de `Button2`et ajoutez le code suivant pour parcourir les enregistrements :

     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]

## <a name="test-the-application"></a>Tester l’application
 Vous pouvez maintenant tester votre classeur pour vous assurer que les données s’affichent comme prévu, et que vous pouvez utiliser la solution hors connexion.

### <a name="to-test-the-data-caching"></a>Pour tester la mise en cache de données

1. Appuyez sur **F5**.

2. Vérifiez que la plage nommée et l’objet de liste sont remplis avec des données à partir de la source de données.

3. Faites défiler quelques-uns des enregistrements en cliquant sur les boutons.

4. Enregistrez le classeur, puis fermez le classeur et Visual Studio.

5. Désactiver la connexion à la base de données. Débranchez le câble réseau de votre ordinateur si la base de données se trouve sur un serveur, ou arrêter le service SQL Server si la base de données se trouve sur votre ordinateur de développement.

6. Ouvrez Excel, puis ouvrez **mes Master-Detail.xlsx** à partir de la *\bin* répertoire ( *\My Master-Detail\bin* en Visual Basic ou *\My Master-Detail\bin\ déboguer* en c#).

7. Faire défiler des enregistrements pour vérifier que la feuille de calcul fonctionne normalement déconnecté.

8. Se reconnecter à la base de données. Connecter votre ordinateur au réseau à nouveau si la base de données se trouve sur un serveur, ou démarrer le service SQL Server si la base de données se trouve sur votre ordinateur de développement.

## <a name="next-steps"></a>Étapes suivantes
 Cette procédure pas à pas montre les principes fondamentaux de création d’une relation de données maître/détail sur une feuille de calcul et de mise en cache d’un jeu de données. Voici quelques tâches susceptibles de venir après :

- Déployer la solution. Pour plus d’informations, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Voir aussi
- [Lier des données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Données dans les solutions Office](../vsto/data-in-office-solutions.md)
- [Données du cache](../vsto/caching-data.md)
- [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
