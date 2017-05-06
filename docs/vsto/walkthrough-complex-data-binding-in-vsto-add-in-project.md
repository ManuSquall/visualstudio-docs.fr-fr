---
title: "Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es complexe dans un projet de compl&#233;ment VSTO"
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
  - "liaison de données (développement Office dans Visual Studio), Excel"
  - "données (développement Office dans Visual Studio), lier des données"
  - "données complexes (développement Office dans Visual Studio)"
ms.assetid: ff52fb56-1f67-4ae2-a3d1-93038619d4e6
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es complexe dans un projet de compl&#233;ment VSTO
  Vous pouvez lier des données à des contrôles hôtes et des contrôles Windows Forms dans des projets de complément VSTO. Cette procédure pas à pas montre comment ajouter des contrôles à une feuille de calcul Microsoft Office Excel et les lier à des données au moment de l’exécution.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout d’un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul au moment de l’exécution.  
  
-   Création d’un <xref:System.Windows.Forms.BindingSource> qui connecte le contrôle à une instance d’un dataset.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accès à une instance en cours d’exécution de SQL Server 2005 ou SQL Server 2005 Express à laquelle l’exemple de base de données `AdventureWorksLT` est attaché. Vous pouvez télécharger la base de données `AdventureWorksLT` à partir du [site web CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Pour plus d’informations sur l’attachement d’une base de données, consultez les rubriques suivantes :  
  
    -   Pour attacher une base de données à l’aide de SQL Server Management Studio ou de SQL Server Management Studio Express, consultez [Comment : attacher une base de données \(SQL Server Management Studio\)](http://msdn.microsoft.com/fr-fr/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Pour attacher une base de données à l’aide de la ligne de commande, consultez [Comment : attacher un fichier de base de données à SQL Server Express](http://msdn.microsoft.com/fr-fr/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Création d'un projet  
 La première étape consiste à créer un projet de complément VSTO Excel.  
  
#### Pour créer un projet  
  
1.  Créez un projet de complément VSTO Excel nommé **Remplissage de feuilles de calcul à partir d’une base de données**, à l’aide de Visual Basic ou C\#.  
  
     Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le fichier `ThisAddIn.vb` or `ThisAddIn.cs`, et ajoute le projet **Remplissage de feuilles de calcul à partir d’une base de données** dans l’**Explorateur de solutions**.  
  
## Création d’une source de données  
 Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.  
  
#### Pour ajouter un dataset typé au projet  
  
1.  Si la fenêtre **Sources de données** n'est pas visible, affichez\-la en choisissant, dans la barre de menus, **Affichage**, **Autres fenêtres**, **Sources de données**.  
  
2.  Choisissez **Ajouter une nouvelle source de données** pour démarrer l'**Assistant Configuration de source de données**.  
  
3.  Cliquez sur **Base de données**, puis sur **Suivant**.  
  
4.  Si vous disposez d’une connexion à la base de données `AdventureWorksLT`, choisissez cette connexion et cliquez sur **Suivant**.  
  
     Sinon, cliquez sur **Nouvelle connexion** et utilisez la boîte de dialogue **Ajouter une connexion** pour créer la connexion. Pour plus d'informations, consultez [Comment : établir une connexion à des données d'une base de données](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
5.  Dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l’application**, cliquez sur **Suivant**.  
  
6.  Dans la page **Choisir vos objets de base de données**, développez **Tables** et sélectionnez **Address \(SalesLT\)**.  
  
7.  Cliquez sur **Terminer**.  
  
     Le fichier AdventureWorksLTDataSet.xsd est ajouté dans l’**Explorateur de solutions**. Ce fichier définit les éléments suivants :  
  
    -   Un dataset typé nommé `AdventureWorksLTDataSet`. Ce dataset représente le contenu de la table **Address \(SalesLT\)** dans la base de données AdventureWorksLT.  
  
    -   un TableAdapter nommé `AddressTableAdapter`. Vous pouvez utiliser ce TableAdapter pour lire et écrire des données dans le `AdventureWorksLTDataSet`. Pour plus d'informations, consultez [Vue d'ensemble de TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
     Vous utiliserez ces deux objets ultérieurement dans cette procédure pas à pas.  
  
## Création et liaison de contrôles à des données  
 Pour cette procédure pas à pas, le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> affiche toutes les données dans la table que vous avez sélectionnée dès que l’utilisateur ouvre le classeur. L’objet de liste utilise un <xref:System.Windows.Forms.BindingSource> pour connecter le contrôle à la base de données.  
  
 Pour plus d’informations sur la liaison des contrôles aux données, consultez [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### Pour ajouter l’objet de liste, le dataset et l’adaptateur de table  
  
1.  Dans la classe `ThisAddIn`, déclarez les contrôles suivants pour afficher la table `Address` du dataset `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  Dans la méthode `ThisAddIn_Startup`, ajoutez le code suivant pour initialiser le dataset et le remplir avec des informations issues du dataset `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  Ajoutez le code suivant à la méthode `ThisAddIn_Startup`. Cela génère un élément hôte qui étend la feuille de calcul. Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_ExcelAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  Créez une plage et ajoutez le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  Liez l’objet de liste à `AdventureWorksLTDataSet` en utilisant <xref:System.Windows.Forms.BindingSource>. Passez les noms des colonnes que vous souhaitez lier à l’objet de liste.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#5)]  
  
## Test du complément  
 Quand vous ouvrez Excel, le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> affiche les données de la table `Address` du dataset `AdventureWorksLTDataSet`.  
  
#### Pour tester le complément VSTO  
  
-   Appuyez sur **F5**.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `addressListObject` est créé dans la feuille de calcul. Au même moment, un objet dataset nommé `adventureWorksLTDataSet` et un <xref:System.Windows.Forms.BindingSource> nommé `addressBindingSource` sont ajoutés au projet.<xref:Microsoft.Office.Tools.Excel.ListObject> est lié à <xref:System.Windows.Forms.BindingSource>, qui est lui\-même lié à l’objet dataset.  
  
## Voir aussi  
 [Données dans les solutions Office](../vsto/data-in-office-solutions.md)   
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Comment : remplir des feuilles de calcul avec des données provenant d'une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Comment : remplir des documents avec les données d'une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Comment : remplir des documents avec les données de services](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Comment : remplir des documents avec les données d'objets](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Comment : parcourir les enregistrements de base de données dans une feuille de calcul](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Comment : mettre à jour une source de données avec les données d'un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Procédure pas à pas : liaison de données simple dans un projet au niveau du document](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [Procédure pas à pas : liaison de données complexe dans un projet au niveau du document](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [Vue d'ensemble de l'utilisation de fichiers de base de données locaux dans les solutions Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Vue d'ensemble de l'utilisation de fichiers de base de données locaux dans les solutions Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Connexion à des données dans des applications Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Vue d'ensemble du composant BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  