---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;une relation ma&#238;tre/d&#233;tail &#224; l&#39;aide d&#39;un groupe de donn&#233;es mis en cache"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "mise en cache de données (développement Office dans Visual Studio), relation maître/détail"
  - "tables maître/détail (développement Office dans Visual Studio), procédures pas à pas"
ms.assetid: 419f4e07-c67f-4fc9-973a-bc794f349ac3
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;une relation ma&#238;tre/d&#233;tail &#224; l&#39;aide d&#39;un groupe de donn&#233;es mis en cache
  Cette procédure pas à pas montre la création d'une relation maître\/détail dans une feuille de calcul et la mise en cache des données afin que la solution puisse être utilisée hors connexion.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Au cours de cette procédure pas à pas, vous apprendrez à :  
  
-   ajouter des contrôles à une feuille de calcul ;  
  
-   configurer un groupe de données à mettre en cache dans une feuille de calcul ;  
  
-   ajouter du code pour activer le défilement des enregistrements ;  
  
-   tester votre projet.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accédez à l'exemple de base de données Northwind dans SQL Server.  La base de données peut se trouver sur votre ordinateur de développement ou sur un serveur.  
  
-   Autorisations d'accès en lecture et écriture à la base de données SQL Server  
  
## Création d'un projet  
 Dans cette étape, vous allez créer un projet de classeur Excel.  
  
#### Pour créer un projet  
  
1.  Créez un projet de classeur Excel et attribuez\-lui le nom **My Master\-Detail** à l'aide de Visual Basic ou de C\#.  Assurez\-vous d'avoir sélectionné **Créer un nouveau document**.  Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet My Master\-Detail à l'**Explorateur de solutions**.  
  
## Création de la source de données  
 Utilisez la fenêtre **Sources de données** pour ajouter un groupe de données typé à votre projet.  
  
#### Pour créer la source de données  
  
1.  Si la fenêtre **Sources de données** n'est pas visible, affichez\- la par, dans la barre de menus, choisissant **Afficher**, **Autres fenêtres**, **Sources de données**.  
  
2.  Choisissez **Ajouter une nouvelle source de données** pour démarrer **Assistant Configuration de source de données**.  
  
3.  Sélectionnez **Base de données**, puis cliquez sur **Suivant**.  
  
4.  Sélectionnez une connexion de données pour l'exemple de base de données Northwind dans SQL Server ou ajoutez une nouvelle connexion à l'aide du bouton **Nouvelle connexion**.  
  
5.  Après avoir sélectionné ou créé une connexion, cliquez sur **Suivant**.  
  
6.  Désélectionnez l'option pour enregistrer la connexion si elle est sélectionnée, puis cliquez sur **Suivant**.  
  
7.  Développez le nœud **Tables** dans la fenêtre **Objets de base de données**.  
  
8.  Sélectionnez les tables **Orders** et **Order Details**.  
  
9. Cliquez sur **Terminer**.  
  
 L'Assistant ajoute les deux tables à la fenêtre **Sources de données**.  Un groupe de données typé est également ajouté à votre projet, visible dans l'**Explorateur de solutions**.  
  
## Ajout de contrôles à la feuille de calcul  
 Dans cette étape, vous ajouterez une plage nommée, un objet de liste et deux boutons à la première feuille de calcul.  Commencez par ajouter la plage nommée et l'objet de liste à partir de la fenêtre **Sources de données** afin qu'ils soient automatiquement liés à la source de données.  Ensuite, ajoutez les boutons de la **Boîte à outils**.  
  
#### Pour ajouter une plage nommée et un objet de liste  
  
1.  Vérifiez que le classeur **Mon Master\-Detail.xlsx** est ouvert dans le concepteur Visual Studio, avec **Feuille1** a affiché.  
  
2.  Ouvrez la fenêtre **Sources de données** et développez le nœud **Orders**.  
  
3.  Sélectionnez la colonne **OrderID**, puis cliquez sur la flèche de déroulement qui apparaît.  
  
4.  Cliquez sur **NamedRange** dans la liste déroulante, puis faites glisser la colonne **OrderID** jusqu'à la cellule **A2**.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> nommé `OrderIDNamedRange` est créé dans la cellule **A2**.  En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `OrdersBindingSource`, un adaptateur de table et une instance de <xref:System.Data.DataSet> sont ajoutés au projet.  Le contrôle est lié à <xref:System.Windows.Forms.BindingSource>, qui est lié à son tour à l'instance de <xref:System.Data.DataSet>.  
  
5.  Faites défiler vers le bas les colonnes qui sont sous la table **Orders**.  À la fin de la liste se trouve la table **Order Details** ; elle est située à cet endroit, car il s'agit d'un enfant de la table **Orders**.  Sélectionnez cette table **Order Details**, et non celle située au même niveau que la table **Orders**, puis cliquez sur la flèche de déroulement qui apparaît.  
  
6.  Cliquez sur **ListObject** dans la liste déroulante, puis faites glisser la table **OrderDetails** vers la cellule **A6**.  
  
7.  Un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> nommé **Order\_DetailsListObject** est créé dans la cellule **A6** et lié à <xref:System.Windows.Forms.BindingSource>.  
  
#### Pour ajouter deux boutons  
  
1.  À partir de l'onglet **Contrôles communs** de la **Boîte à outils**, ajoutez un contrôle <xref:System.Windows.Forms.Button> à la cellule **A3** de la feuille de calcul.  
  
     Ce bouton est nommé `Button1`.  
  
2.  Ajoutez un autre contrôle <xref:System.Windows.Forms.Button> à la cellule **B3** de la feuille de calcul.  
  
     Ce bouton est nommé `Button2`.  
  
 Ensuite, marquez le groupe de données à mettre en cache dans le document.  
  
## Mise en cache du groupe de données  
 Marquez le groupe de données à mettre en cache dans le document en rendant public le groupe de données et en définissant la propriété **CacheInDocument**.  
  
#### Pour mettre en cache le groupe de données  
  
1.  Sélectionnez **NorthwindDataSet** dans la barre d'état des composants.  
  
2.  Dans la fenêtre **Propriétés**, remplacez la valeur de la propriété **Modifiers** par **Public**.  
  
     Les groupes de données doivent être publics pour que la mise en cache soit activée.  
  
3.  Remplacez la valeur de la propriété **CacheInDocument** par **True**.  
  
 L'étape suivante consiste à ajouter du texte aux boutons, et en C\#, à ajouter du code pour raccorder les gestionnaires d'événements.  
  
## Initialisation des contrôles  
 Définissez le texte du bouton et ajoutez des gestionnaires d'événements pendant l'événement <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>.  
  
#### Pour initialiser les données et les contrôles  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Sheet1.vb** ou **Sheet1.cs**, puis cliquez sur **Afficher le code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant à la méthode `Sheet1_Startup` afin de définir le texte des boutons.  
  
     [!code-csharp[Trin_VstcoreDataExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#15)]
     [!code-vb[Trin_VstcoreDataExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#15)]  
  
3.  Pour C\# uniquement, ajoutez des gestionnaires d'événements pour les événements Click de bouton à la méthode `Sheet1_Startup`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#16)]  
  
## Ajout de code pour pouvoir faire défiler les enregistrements  
 Ajoutez du code au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> de chaque bouton pour parcourir les enregistrements.  
  
#### Pour faire défiler les enregistrements  
  
1.  Ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> de `Button1` et ajoutez le code suivant afin de faire défiler les enregistrements vers l'arrière :  
  
     [!code-csharp[Trin_VstcoreDataExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#17)]
     [!code-vb[Trin_VstcoreDataExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#17)]  
  
2.  Ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> de `Button2` et ajoutez le code suivant afin de faire défiler les enregistrements vers l'avant :  
  
     [!code-csharp[Trin_VstcoreDataExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#18)]
     [!code-vb[Trin_VstcoreDataExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#18)]  
  
## Test de l'application  
 Maintenant, vous pouvez tester votre classeur afin de vérifier que les données apparaissent correctement et que vous pouvez utiliser la solution hors connexion.  
  
#### Pour tester la mise en cache des données  
  
1.  Appuyez sur **F5**.  
  
2.  Vérifiez que la plage nommée et l'objet de liste contiennent des données de la source de données.  
  
3.  Faites défiler quelques\-uns des enregistrements en cliquant sur les boutons.  
  
4.  Enregistrez le classeur, puis fermez le classeur et Visual Studio.  
  
5.  Désactivez la connexion à la base de données.  Débranchez le câble réseau de votre ordinateur si la base de données est située sur un serveur ou arrêtez le service SQL Server si la base de données se trouve sur votre ordinateur de développement.  
  
6.  Ouvrez Excel, puis **Mon Master\-Detail.xlsx** ouvert de répertoire\\bin\\\(de mes maître\/détail\\bin dans Visual Basic ou mes maître\/détail\\\\ bin\\debug dans c\).  
  
7.  Faites défiler quelques\-uns des enregistrements pour vérifier que, hors connexion, la feuille de calcul fonctionne normalement.  
  
8.  Reconnectez\-vous à la base de données.  Connectez de nouveau votre ordinateur au réseau si la base de données est située sur un serveur ou démarrez le service SQL Server si la base de données se trouve sur votre ordinateur de développement.  
  
## Étapes suivantes  
 Cette procédure pas à pas présente les notions de base de la création d'une relation de données maître\/détail dans une feuille de calcul et de la mise en cache d'un groupe de données.  Vous devrez peut\-être ensuite exécuter les opérations suivantes :  
  
-   Déployer la solution.  Pour plus d'informations, consultez [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)  
  
## Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Données dans les solutions Office](../vsto/data-in-office-solutions.md)   
 [Mise en cache des données](../vsto/caching-data.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  