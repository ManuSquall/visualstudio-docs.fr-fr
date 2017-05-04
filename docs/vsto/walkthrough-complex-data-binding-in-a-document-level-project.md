---
title: "Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es complexe dans un projet au niveau du document | Microsoft Docs"
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
  - "données complexes (développement Office dans Visual Studio)"
  - "données (développement Office dans Visual Studio), lier des données"
  - "liaison de données (développement Office dans Visual Studio), plusieurs colonnes"
  - "liaison de données sur plusieurs colonnes (développement Office dans Visual Studio)"
ms.assetid: 32ffad3d-fba4-476a-99b8-ef440434f4e1
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es complexe dans un projet au niveau du document
  Cette procédure pas à pas présente les notions de base relatives à la liaison de données complexe dans un projet au niveau du document.  Vous pouvez lier plusieurs cellules dans une feuille de calcul Microsoft Office Excel aux champs de la base de données SQL Server Northwind.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout d'une source de données à votre projet de classeur.  
  
-   Ajout de contrôles liés aux données à une feuille de calcul.  
  
-   Enregistrement des modifications de données dans la base de données.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accès à un serveur sur lequel est installé l'exemple de base de données SQL Server Northwind.  
  
-   Autorisations d'accès en lecture et écriture à la base de données SQL Server  
  
## Création d'un projet  
 La première étape consiste à créer un projet de classeur Excel.  
  
#### Pour créer un projet  
  
1.  Créez un projet de classeur Excel et attribuez\-lui le nom **My Complex Data Binding**.  Dans l'Assistant, sélectionnez **Créer un nouveau document**.  
  
     Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet My Complex Data Binding à l'**Explorateur de solutions**.  
  
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
  
8.  Activez la case à cocher située à côté de la table **Employees**.  
  
9. Cliquez sur **Terminer**.  
  
 L'Assistant ajoute la table **Employees** à la fenêtre **Sources de données**.  Un groupe de données typé est également ajouté à votre projet, visible dans l'**Explorateur de solutions**.  
  
## Ajout de contrôles à la feuille de calcul  
 Une feuille de calcul affichera la table **Employees** lorsque le classeur sera ouvert.  Les utilisateurs pourront apporter des modifications aux données et les enregistrer dans la base de données en cliquant sur un bouton.  
  
 Pour lier automatiquement la feuille de calcul à la table, vous pouvez ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> à la feuille de calcul à partir de la fenêtre **Sources de données**.  Pour permettre à l'utilisateur d'enregistrer des modifications, ajoutez un contrôle <xref:System.Windows.Forms.Button> à partir de la **Boîte à outils**.  
  
#### Pour ajouter un objet de liste  
  
1.  Vérifiez que le classeur **Mes données complexes Binding.xlsx** est ouvert dans le concepteur Visual Studio, avec **Feuille1** a affiché.  
  
2.  Ouvrez la fenêtre **Sources de données** et sélectionnez le nœud **Employees**.  
  
3.  Cliquez sur la flèche de déroulement qui apparaît.  
  
4.  Sélectionnez **ListObject** dans la liste déroulante.  
  
5.  Faites glisser la table **Employees** vers la cellule **A6**.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `EmployeesListObject` est créé dans cellule **A6**.  En même temps, un <xref:System.Windows.Forms.BindingSource> nommé `EmployeesBindingSource`, un adaptateur de table et une instance de <xref:System.Data.DataSet> sont ajoutés au projet.  Le contrôle est lié à <xref:System.Windows.Forms.BindingSource>, qui est lié à son tour à l'instance de <xref:System.Data.DataSet>.  
  
#### Pour ajouter un bouton  
  
1.  À partir de l'onglet **Contrôles communs** de la **Boîte à outils**, ajoutez un contrôle <xref:System.Windows.Forms.Button> à la cellule **A4** de la feuille de calcul.  
  
 L'étape suivante consiste à ajouter du texte au bouton lorsque la feuille de calcul s'affiche.  
  
## Initialisation du contrôle  
 Ajoutez du texte au bouton dans le gestionnaire d'événements <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>.  
  
#### Pour initialiser le contrôle  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Sheet1.vb** ou **Sheet1.cs**, puis cliquez sur **Afficher le code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant à la méthode `Sheet1_Startup` pour définir le texte du `button`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#8)]  
  
3.  Pour C\# uniquement, ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> à la méthode `Sheet1_Startup`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#9)]  
  
 Ajoutez maintenant le code pour gérer l'événement <xref:System.Windows.Forms.Control.Click> du bouton.  
  
## Enregistrement des modifications apportées à la base de données  
 Toutes les modifications apportées aux données existent uniquement dans le groupe de données local jusqu'à ce qu'elles soient de nouveau enregistrées explicitement dans la base de données.  
  
#### Pour enregistrer les modifications apportées à la base de données  
  
1.  Ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> du b`utton`, puis ajoutez le code suivant pour valider dans la base de données toutes les modifications qui ont été apportées au groupe de données :  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#10)]  
  
## Test de l'application  
 Vous pouvez maintenant tester votre classeur pour vérifier que les données s'affichent correctement et que vous pouvez les manipuler dans l'objet de liste.  
  
#### Pour tester la liaison de données  
  
-   Appuyez sur F5.  
  
     Vérifiez que lorsque le classeur s'ouvre, l'objet de liste contient les données de la table **Employees**.  
  
#### Pour modifier des données  
  
1.  Cliquez sur la cellule **B7** qui doit contenir le nom **Davolio**.  
  
2.  Tapez le nom Anderson, puis appuyez sur ENTRÉE.  
  
#### Pour modifier un en\-tête de colonne  
  
1.  Cliquez sur la cellule qui contient l'en\-tête de colonne **LastName**.  
  
2.  Tapez Last Name, sans oublier l'espace entre les deux mots, puis appuyez sur ENTRÉE.  
  
#### Pour enregistrer des données  
  
1.  Cliquez sur **Enregistrer** dans la feuille de calcul.  
  
2.  Quittez Excel.  Cliquez sur **Non** à l'invite proposant d'enregistrer les modifications effectuées.  
  
3.  Appuyez sur F5 pour exécuter de nouveau le projet.  
  
     L'objet de liste contient les données de la table **Employees**.  
  
4.  Notez que le nom dans la cellule **B7** est encore Anderson ; il correspond à la modification de données que vous avez effectuée et enregistrée dans la base de données.  L'en\-tête de colonne **LastName** est revenu à sa forme d'origine sans espace, parce que l'en\-tête de colonne n'est pas lié à la base de données et que vous n'avez pas enregistré les modifications apportées à la feuille de calcul.  
  
#### Pour ajouter de nouvelles lignes  
  
1.  Sélectionnez une cellule à l'intérieur de l'objet de liste.  
  
     Une nouvelle ligne apparaît au bas de la liste, avec un astérisque \(**\***\) dans la première cellule de la nouvelle ligne.  
  
2.  Ajoutez les informations suivantes dans la ligne vide.  
  
    |ID Employé|LastName|FirstName|Titre|  
    |----------------|--------------|---------------|-----------|  
    |10|Ito|Shu|Directeur commercial|  
  
#### Pour supprimer des lignes  
  
-   Cliquez avec le bouton droit sur le nombre 16 \(ligne 16\) sur l'extrême gauche de la feuille de calcul, puis cliquez sur **Supprimer**.  
  
#### Pour trier les lignes dans la liste  
  
1.  Sélectionnez une cellule à l'intérieur de la liste.  
  
     Les boutons fléchés apparaissent dans chaque en\-tête de colonne.  
  
2.  Cliquez sur le bouton fléché dans l'en\-tête de colonne **Last Name**.  
  
3.  Cliquez sur **Tri croissant**.  
  
     Les lignes sont triées par ordre alphabétique des noms.  
  
#### Pour filtrer des informations  
  
1.  Sélectionnez une cellule à l'intérieur de la liste.  
  
2.  Cliquez sur le bouton fléché dans l'en\-tête de colonne **Title**.  
  
3.  Cliquez sur **Sales Representative**.  
  
     La liste affiche uniquement les lignes contenant **Sales Representative** dans la colonne **Title**.  
  
4.  Cliquez de nouveau sur le bouton fléché dans l'en\-tête de colonne **Title**.  
  
5.  Cliquez sur **\(Tous\)**.  
  
     Le filtrage est désactivé et toutes les lignes apparaissent.  
  
## Étapes suivantes  
 Cette procédure pas à pas présente les notions de base de la liaison d'une table dans une base de données à un objet de liste.  Vous devrez peut\-être ensuite exécuter les opérations suivantes :  
  
-   Mettre en cache les données afin qu'elles puissent être utilisées hors connexion.  Pour plus d'informations, consultez [Comment : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Déployer la solution.  Pour plus d'informations, consultez [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md).  
  
-   Créer une relation maître\/détails entre un champ et une table.  Pour plus d'informations, consultez [Procédure pas à pas : création d'une relation maître&#47;détail à l'aide d'un groupe de données mis en cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).  
  
## Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Données dans les solutions Office](../vsto/data-in-office-solutions.md)   
 [Procédure pas à pas : liaison de données simple dans un projet au niveau du document](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  