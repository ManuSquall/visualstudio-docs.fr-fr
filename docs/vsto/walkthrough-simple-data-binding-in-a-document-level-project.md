---
title: "Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es simple dans un projet au niveau du document"
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
  - "données (développement Office dans Visual Studio), lier des données"
  - "liaison de données (développement Office dans Visual Studio), cellule de feuille de calcul à un champ de base de données"
  - "champ de base de données (développement Office dans Visual Studio)"
  - "liaison de données simple (développement Office dans Visual Studio)"
  - "feuilles de calcul (développement Office dans Visual Studio), lier une cellule de feuille de calcul à un champ de base de données"
ms.assetid: 6b8fd638-af13-4ea1-b1c0-2763e2d8ae23
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es simple dans un projet au niveau du document
  Cette procédure pas à pas présente les notions de base relatives à la liaison de données dans un projet au niveau du document.  Un champ de données unique d'une base de données SQL Server est lié à une plage nommée de Microsoft Office Excel.  La procédure pas à pas indique également comment ajouter des contrôles permettant de faire défiler tous les enregistrements de la table.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'une source de données pour un projet Excel  
  
-   Ajout de contrôles à une feuille de calcul  
  
-   Défilement des enregistrements d'une base de données  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accès à un serveur sur lequel est installé l'exemple de base de données SQL Server Northwind.  
  
-   Autorisations d'accès en lecture et écriture à la base de données SQL Server  
  
## Création d'un projet  
 Dans cette étape, vous allez créer un projet de classeur Excel.  
  
#### Pour créer un projet  
  
1.  Créez un projet de classeur Excel portant le nom **My Simple Data Binding** à l'aide de Visual Basic ou de C\#.  Assurez\-vous d'avoir sélectionné **Créer un nouveau document**.  Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet My Simple Data Binding à l'**Explorateur de solutions**.  
  
## Création de la source de données  
 Utilisez la fenêtre **Sources de données** pour ajouter un groupe de données typé à votre projet.  
  
#### Pour créer la source de données  
  
1.  Si la fenêtre **Sources de données** n'est pas visible, affichez\- la par, dans la barre de menus, choisissant **Afficher**, **Autres fenêtres**, **Sources de données**.  
  
2.  Choisissez **Ajouter une nouvelle source de données** pour démarrer **Assistant Configuration de source de données**.  
  
3.  Sélectionnez **Base de données**, puis cliquez sur **Suivant**.  
  
4.  Sélectionnez une connexion de données à l'exemple de base de données SQL Server Northwind ou ajoutez une nouvelle connexion à l'aide du bouton **Nouvelle connexion**.  
  
5.  Après avoir sélectionné ou créé une connexion, cliquez sur **Suivant**.  
  
6.  Désélectionnez l'option pour enregistrer la connexion si elle est sélectionnée, puis cliquez sur **Suivant**.  
  
7.  Développez le nœud **Tables** dans la fenêtre **Objets de base de données**.  
  
8.  Activez la case à cocher située à côté de la table **Customers**.  
  
9. Cliquez sur **Terminer**.  
  
 L'Assistant ajoute la table **Customers** à la fenêtre **Sources de données**.  Un groupe de données typé est également ajouté à votre projet, visible dans l'**Explorateur de solutions**.  
  
## Ajout de contrôles à la feuille de calcul  
 Pour cette procédure pas à pas, vous avez besoin de deux plages nommées et de quatre boutons sur la première feuille de calcul.  Commencez par ajouter les deux plages nommées de la fenêtre **Sources de données** afin qu'elles soient automatiquement liées à la source de données.  Ensuite, ajoutez les boutons de la **Boîte à outils**.  
  
#### Pour ajouter deux plages nommées  
  
1.  Vérifiez que le classeur **Mes données simples Binding.xlsx** est ouvert dans le concepteur Visual Studio, avec **Feuille1** a affiché.  
  
2.  Ouvrez la fenêtre **Sources de données** et développez le nœud **Customers**.  
  
3.  Sélectionnez la colonne **CompanyName**, puis cliquez sur la flèche de déroulement qui apparaît.  
  
4.  Sélectionnez **NamedRange** dans la liste déroulante, puis faites glisser la colonne **CompanyName** jusqu'à la cellule **A1**.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> nommé `companyNameNamedRange` est créé dans la cellule **A1**.  En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `customersBindingSource`, un adaptateur de table et une instance de <xref:System.Data.DataSet> sont ajoutés au projet.  Le contrôle est lié à <xref:System.Windows.Forms.BindingSource>, qui est lié à son tour à l'instance de <xref:System.Data.DataSet>.  
  
5.  Sélectionnez la colonne **CustomerID** dans la fenêtre **Sources de données**, puis cliquez sur la flèche de déroulement qui apparaît.  
  
6.  Cliquez sur **NamedRange** dans la liste déroulante, puis faites glisser la colonne **CustomerID** jusqu'à la cellule **B1**.  
  
7.  Un autre contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> nommé `customerIDNamedRange` est créé dans la cellule **B1** et lié à la <xref:System.Windows.Forms.BindingSource>.  
  
#### Pour ajouter quatre boutons  
  
1.  À partir de l'onglet **Contrôles communs** de la **Boîte à outils**, ajoutez un contrôle <xref:System.Windows.Forms.Button> à la cellule **A3** de la feuille de calcul.  
  
     Ce bouton est nommé `Button1`.  
  
2.  Ajoutez, dans cet ordre, trois boutons supplémentaires aux cellules suivantes afin que les noms soient comme indiqué :  
  
    |Cellule|\(Name\)|  
    |-------------|--------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 L'étape suivante consiste à ajouter du texte aux boutons et à ajouter des gestionnaires d'événements en C\#.  
  
## Initialisation des contrôles  
 Définissez le texte du bouton et ajoutez des gestionnaires d'événements pendant l'événement <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>.  
  
#### Pour initialiser les contrôles  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Sheet1.vb** ou **Sheet1.cs**, puis cliquez sur **Afficher le code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant à la méthode `Sheet1_Startup` afin de définir le texte pour chaque bouton.  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#2)]  
  
3.  Pour C\# uniquement, ajoutez des gestionnaires d'événements pour les événements Click de bouton à la méthode `Sheet1_Startup`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#3)]  
  
 Maintenant, ajoutez du code pour gérer les événements <xref:System.Windows.Forms.Control.Click> des boutons afin que l'utilisateur puisse parcourir les enregistrements.  
  
## Ajout de code pour pouvoir faire défiler les enregistrements  
 Ajoutez du code au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> de chaque bouton pour parcourir les enregistrements.  
  
#### Pour vous déplacer jusqu'au premier enregistrement  
  
1.  Ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> du bouton `Button1` et ajoutez le code suivant afin de vous déplacer jusqu'au premier enregistrement :  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#4)]  
  
#### Pour revenir à l'enregistrement précédent  
  
1.  Ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> du bouton `Button2` et ajoutez le code suivant afin de revenir à la position précédente :  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#5)]  
  
#### Pour vous déplacer jusqu'à l'enregistrement suivant  
  
1.  Ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> du bouton `Button3` et ajoutez le code suivant afin de passer à la position suivante :  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#6)]  
  
#### Pour vous déplacer jusqu'au dernier enregistrement  
  
1.  Ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> du bouton `Button4` et ajoutez le code suivant afin de vous déplacer jusqu'au dernier enregistrement :  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#7)]  
  
## Test de l'application  
 Vous pouvez maintenant tester votre classeur afin de vous assurer que vous pouvez parcourir les enregistrements de la base de données.  
  
#### Pour tester votre classeur  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Vérifiez que le premier enregistrement apparaît dans les cellules **A1** et **B1**.  
  
3.  Cliquez sur le bouton **\>** \(`Button3`\) et vérifiez que l'enregistrement suivant apparaît dans les cellules **A1** et **B1**.  
  
4.  Cliquez sur les autres boutons de défilement pour confirmer que l'enregistrement est modifié comme vous l'attendiez.  
  
## Étapes suivantes  
 Cette procédure pas à pas présente les notions de base permettant de lier une plage nommée à un champ dans une base de données.  Vous devrez peut\-être ensuite exécuter les opérations suivantes :  
  
-   Mettre en cache les données afin qu'elles puissent être utilisées hors connexion.  Pour plus d'informations, consultez [Comment : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Lier des cellules à plusieurs colonnes dans une table au lieu de les lier à un champ.  Pour plus d'informations, consultez [Procédure pas à pas : liaison de données complexe dans un projet au niveau du document](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Utiliser un contrôle <xref:System.Windows.Forms.BindingNavigator> pour faire défiler les enregistrements.  Pour plus d'informations, consultez [Comment : naviguer parmi les données avec le contrôle BindingNavigator Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb).  
  
## Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Données dans les solutions Office](../vsto/data-in-office-solutions.md)   
 [Procédure pas à pas : liaison de données complexe dans un projet au niveau du document](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  