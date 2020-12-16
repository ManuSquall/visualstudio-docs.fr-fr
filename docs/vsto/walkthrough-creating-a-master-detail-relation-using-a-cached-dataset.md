---
title: Créer une relation de détail maître à l’aide d’un jeu de données mis en cache
description: En savoir plus sur la création d’une relation maître/détail sur une feuille de calcul et la mise en cache des données afin que la solution puisse être utilisée en mode hors connexion.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: de7bf3ba34a2a7dd3e7db9ff549e4a839800d524
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524868"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Procédure pas à pas : créer une relation de détail maître à l’aide d’un DataSet mis en cache
  Cette procédure pas à pas illustre la création d’une relation maître/détail sur une feuille de calcul et la mise en cache des données afin que la solution puisse être utilisée en mode hors connexion.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Pendant cette procédure pas à pas, vous allez apprendre à :

- Ajoutez des contrôles à une feuille de calcul.

- Configurez un jeu de données à mettre en cache dans une feuille de calcul.

- Ajoutez du code pour permettre le défilement des enregistrements.

- Testez votre projet.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accès à l’exemple de base de données Northwind SQL Server. La base de données peut se trouver sur votre ordinateur de développement ou sur un serveur.

- Autorisations de lecture et d’écriture dans la base de données SQL Server.

## <a name="create-a-new-project"></a>Créer un projet
 Dans cette étape, vous allez créer un projet de classeur Excel.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de classeur Excel portant le nom **My Master-Detail**, en utilisant Visual Basic ou C#. Assurez-vous que l’option **créer un nouveau document** est sélectionnée. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet **My Master-Detail** à **Explorateur de solutions**.

## <a name="create-the-data-source"></a>Créer la source de données
 Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.

### <a name="to-create-the-data-source"></a>Pour créer la source de données

1. Si la fenêtre **sources de données** n’est pas visible, affichez-la en cliquant sur **Afficher** d'  >  **autres**  >  **sources de données** Windows dans la barre de menus.

2. Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

3. Sélectionnez **base de données** , puis cliquez sur **suivant**.

4. Sélectionnez une connexion de données à l’exemple Northwind SQL Server base de données ou ajoutez une nouvelle connexion à l’aide du bouton **nouvelle connexion** .

5. Après avoir sélectionné ou créé une connexion, cliquez sur **suivant**.

6. Désactivez l’option permettant d’enregistrer la connexion si elle est sélectionnée, puis cliquez sur **suivant**.

7. Développez le nœud **tables** dans la fenêtre **objets de base de données** .

8. Sélectionnez la table **Orders** et la table Order **Details** .

9. Cliquez sur **Terminer**.

   L’Assistant ajoute les deux tables à la fenêtre **sources de données** . Il ajoute également un DataSet typé à votre projet qui est visible dans **Explorateur de solutions**.

## <a name="add-controls-to-the-worksheet"></a>Ajouter des contrôles à la feuille de calcul
 Dans cette étape, vous allez ajouter une plage nommée, un objet de liste et deux boutons à la première feuille de calcul. Tout d’abord, ajoutez la plage nommée et l’objet de liste à partir de la fenêtre **sources de données** afin qu’elles soient automatiquement liées à la source de données. Ensuite, ajoutez les boutons de la **boîte à outils**.

### <a name="to-add-a-named-range-and-a-list-object"></a>Pour ajouter une plage nommée et un objet de liste

1. Vérifiez que le classeur **mon Master-Detail.xlsx** est ouvert dans le concepteur Visual Studio, avec **Feuil1** affiché.

2. Ouvrez la fenêtre **sources de données** et développez le nœud **Orders** .

3. Sélectionnez la colonne **OrderID** , puis cliquez sur la flèche déroulante qui s’affiche.

4. Cliquez sur **NamedRange** dans la liste déroulante, puis faites glisser la colonne **OrderID** vers la cellule **a2**.

     Un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle nommé `OrderIDNamedRange` est créé dans la cellule **a2**. En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `OrdersBindingSource` , un adaptateur de table et une <xref:System.Data.DataSet> instance sont ajoutés au projet. Le contrôle est lié au <xref:System.Windows.Forms.BindingSource> , qui est à son tour lié à l' <xref:System.Data.DataSet> instance.

5. Faites défiler vers le-delà des colonnes qui se trouvent sous la table **Orders** . La table **Order Details** est située en bas de la liste. C’est parce qu’il s’agit d’un enfant de la table **Orders** . Sélectionnez la table Order **Details** , mais pas celle qui se trouve au même niveau que la table **Orders** , puis cliquez sur la flèche déroulante qui s’affiche.

6. Dans la liste déroulante, cliquez sur **ListObject** , puis faites glisser la table **OrderDetails** vers la cellule **a6**.

7. Un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle nommé **Order_DetailsListObject** est créé dans la cellule **a6** et lié au <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-two-buttons"></a>Pour ajouter deux boutons

1. Dans l’onglet **contrôles communs** de la **boîte à outils**, ajoutez un <xref:System.Windows.Forms.Button> contrôle à la cellule **a3** de la feuille de calcul.

    Ce bouton est nommé `Button1` .

2. Ajoutez un autre <xref:System.Windows.Forms.Button> contrôle à la cellule **B3** de la feuille de calcul.

    Ce bouton est nommé `Button2` .

   Ensuite, marquez le jeu de données à mettre en cache dans le document.

## <a name="cache-the-dataset"></a>Mettre le DataSet en cache
 Marquez le jeu de données à mettre en cache dans le document en rendant le DataSet public et en définissant la propriété **CacheInDocument** .

### <a name="to-cache-the-dataset"></a>Pour mettre en cache le jeu de données

1. Sélectionnez **NorthwindDataSet** dans la barre d’état des composants.

2. Dans la fenêtre **Propriétés** , affectez à la propriété **modificateurs** la valeur **public**.

    Les jeux de données doivent être publics pour que la mise en cache soit activée.

3. Remplacez la valeur de la propriété **CacheInDocument** par **true**.

   L’étape suivante consiste à ajouter du texte aux boutons et, en C#, à ajouter du code pour raccorder les gestionnaires d’événements.

## <a name="initialize-the-controls"></a>Initialiser les contrôles
 Définissez le texte du bouton et ajoutez des gestionnaires d’événements au cours de l' <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> événement.

### <a name="to-initialize-the-data-and-the-controls"></a>Pour initialiser les données et les contrôles

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Feuil1. vb** ou **Sheet1.cs**, puis cliquez sur **afficher le code** dans le menu contextuel.

2. Ajoutez le code suivant à la `Sheet1_Startup` méthode pour définir le texte des boutons.

     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]

3. Pour C# uniquement, ajoutez des gestionnaires d’événements pour les événements de clic de bouton à la `Sheet1_Startup` méthode.

     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Ajouter du code pour permettre le défilement des enregistrements
 Ajoutez du code au <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de chaque bouton pour parcourir les enregistrements.

### <a name="to-scroll-through-the-records"></a>Pour faire défiler les enregistrements

1. Ajoutez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.Control.Click> événement de `Button1` et ajoutez le code suivant pour vous déplacer vers l’arrière dans les enregistrements :

     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]

2. Ajoutez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.Control.Click> événement de `Button2` et ajoutez le code suivant pour parcourir les enregistrements :

     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]

## <a name="test-the-application"></a>Test de l’application
 Vous pouvez maintenant tester votre classeur pour vous assurer que les données apparaissent comme prévu et que vous pouvez utiliser la solution en mode hors connexion.

### <a name="to-test-the-data-caching"></a>Pour tester la mise en cache des données

1. Appuyez sur **F5**.

2. Vérifiez que la plage nommée et l’objet de liste sont remplis avec les données de la source de données.

3. Faites défiler certains des enregistrements en cliquant sur les boutons.

4. Enregistrez le classeur, puis fermez le classeur et Visual Studio.

5. Désactivez la connexion à la base de données. Débranchez le câble réseau de votre ordinateur si la base de données se trouve sur un serveur, ou arrêtez le service SQL Server si la base de données se trouve sur votre ordinateur de développement.

6. Ouvrez Excel, puis ouvrez **mon Master-Detail.xlsx** à partir du *répertoire \bin* (*\Mes Master-Detail\bin* dans Visual Basic ou *\Mes Master-Detail\bin\debug* en C#).

7. Faites défiler certains enregistrements pour voir que la feuille de calcul fonctionne normalement lorsque vous êtes déconnecté.

8. Reconnectez-vous à la base de données. Reconnectez votre ordinateur au réseau si la base de données se trouve sur un serveur, ou démarrez le service SQL Server si la base de données se trouve sur votre ordinateur de développement.

## <a name="next-steps"></a>Étapes suivantes
 Cette procédure pas à pas montre les principes fondamentaux de la création d’une relation de données maître/détail sur une feuille de calcul et la mise en cache d’un DataSet. Voici quelques tâches susceptibles de venir après :

- déployer la solution ; Pour plus d’informations, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Voir aussi
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Données dans les solutions Office](../vsto/data-in-office-solutions.md)
- [Données de cache](../vsto/caching-data.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
