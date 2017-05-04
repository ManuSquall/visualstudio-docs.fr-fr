---
title: "Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es simple dans un projet de compl&#233;ment VSTO | Microsoft Docs"
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
  - "données (développement Office dans Visual Studio), liaison de données"
  - "liaison de données (développement Office dans Visual Studio), Word"
  - "données (développement Office dans Visual Studio), liaison de données simple"
ms.assetid: b248d194-a8b1-4f87-94c4-24e940eea1fd
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es simple dans un projet de compl&#233;ment VSTO
  Vous pouvez lier des données à des contrôles hôtes et des contrôles Windows Forms dans des projets de complément VSTO. Cette procédure pas à pas montre comment ajouter des contrôles à un document Microsoft Office Word et les lier à des données au moment de l’exécution.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajouter un <xref:Microsoft.Office.Tools.Word.ContentControl> à un document au moment de l’exécution.  
  
-   Créer un <xref:System.Windows.Forms.BindingSource> qui connecte le contrôle à une instance d’un dataset.  
  
-   Permettre à l’utilisateur de parcourir les enregistrements et de les afficher dans le contrôle.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Accès à une instance en cours d’exécution de SQL Server 2005 ou SQL Server 2005 Express à laquelle est attaché l’exemple de base de données `AdventureWorksLT`. Vous pouvez télécharger la base de données `AdventureWorksLT` à partir du [site web CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Pour plus d’informations sur l’attachement d’une base de données, consultez les rubriques suivantes :  
  
    -   Pour attacher une base de données à l’aide de SQL Server Management Studio ou de SQL Server Management Studio Express, consultez [Procédure : attachement d’une base de données \(SQL Server Management Studio\)](http://msdn.microsoft.com/fr-fr/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Pour attacher une base de données à l’aide de la ligne de commande, consultez [Procédure : attachement d’un fichier de base de données à SQL Server Express](http://msdn.microsoft.com/fr-fr/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Création d'un projet  
 La première étape consiste à créer un projet de complément VSTO Word.  
  
#### Pour créer un projet  
  
1.  Créez un projet de complément VSTO Word nommé **Remplissage de documents à partir d’une base de données**, à l’aide de Visual Basic ou C\#.  
  
     Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le fichier ThisAddIn.vb ou ThisAddIn.cs et ajoute le projet **Remplissage de documents à partir d’une base de données** à l’**Explorateur de solutions**.  
  
2.  Si votre projet cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], ajoutez une référence à l’assembly Microsoft.Office.Tools.Word.v4.0.Utilities.dll. Cette référence est obligatoire pour ajouter par programmation un contrôle Windows Forms au document, plus loin dans cette procédure pas à pas.  
  
## Création d’une source de données  
 Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.  
  
#### Pour ajouter un dataset typé au projet  
  
1.  Si la fenêtre **Sources de données** n'est pas visible, affichez\-la en choisissant, dans la barre de menus, **Affichage**, **Autres fenêtres**, **Sources de données**.  
  
2.  Choisissez **Ajouter une nouvelle source de données** pour démarrer l'**Assistant Configuration de source de données**.  
  
3.  Cliquez sur **Base de données**, puis sur **Suivant**.  
  
4.  Si vous avez une connexion existante à la base de données `AdventureWorksLT`, choisissez cette connexion et cliquez sur **Suivant**.  
  
     Sinon, cliquez sur **Nouvelle connexion** et utilisez la boîte de dialogue **Ajouter une connexion** pour créer la connexion. Pour plus d'informations, consultez [Comment : établir une connexion à des données d'une base de données](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
5.  Dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l’application**, cliquez sur **Suivant**.  
  
6.  Dans la page **Choisir vos objets de base de données**, développez **Tables** et sélectionnez **Customer \(SalesLT\)**.  
  
7.  Cliquez sur **Terminer**.  
  
     Le fichier AdventureWorksLTDataSet.xsd est ajouté à l’**Explorateur de solutions**. Ce fichier définit les éléments suivants :  
  
    -   Un dataset typé nommé `AdventureWorksLTDataSet`. Ce dataset représente le contenu de la table **Customer \(SalesLT\)** dans la base de données AdventureWorksLT.  
  
    -   Un TableAdapter nommé `CustomerTableAdapter`. Vous pouvez utiliser ce TableAdapter pour lire et écrire des données dans le `AdventureWorksLTDataSet`. Pour plus d'informations, consultez [Vue d'ensemble de TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
     Vous utiliserez ces deux objets plus loin lors de cette procédure pas à pas.  
  
## Création et liaison de contrôles à des données  
 L’interface d’affichage des enregistrements de base de données dans cette procédure pas à pas est très simple, et elle est créée directement dans le document. Un <xref:Microsoft.Office.Tools.Word.ContentControl> affiche un enregistrement de base de données à la fois et deux contrôles <xref:Microsoft.Office.Tools.Word.Controls.Button> vous permettent de parcourir les enregistrements. Le contrôle de contenu utilise un <xref:System.Windows.Forms.BindingSource> pour se connecter à la base de données.  
  
 Pour plus d’informations sur la liaison des contrôles aux données, consultez [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### Pour créer l’interface dans le document  
  
1.  Dans la classe `ThisAddIn`, déclarez les contrôles suivants pour afficher et parcourir la table `Customer` de la base de données `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_WordAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  Dans la méthode `ThisAddIn_Startup`, ajoutez le code suivant pour initialiser le dataset et le remplir avec des informations de la base de données `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_WordAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  Ajoutez le code suivant à la méthode `ThisAddIn_Startup`. Cela génère un élément hôte qui étend le document. Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_WordAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  Définissez plusieurs plages au début du document. Ces plages identifient où insérer du texte et placer des contrôles.  
  
     [!code-csharp[Trin_WordAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  Ajoutez les contrôles d’interface aux plages précédemment définies.  
  
     [!code-csharp[Trin_WordAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#5)]  
  
6.  Liez le contrôle de contenu à `AdventureWorksLTDataSet` à l’aide de <xref:System.Windows.Forms.BindingSource>. Pour les développeurs C\# : ajoutez deux gestionnaires d’événements pour les contrôles <xref:Microsoft.Office.Tools.Word.Controls.Button>.  
  
     [!code-csharp[Trin_WordAddInDatabase#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddInDatabase#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#6)]  
  
7.  Ajoutez le code suivant pour parcourir les enregistrements de base de données.  
  
     [!code-csharp[Trin_WordAddInDatabase#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDatabase#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#7)]  
  
## Test du complément  
 Lorsque vous ouvrez Word, le contrôle de contenu affiche des données du dataset `AdventureWorksLTDataSet`. Parcourez les enregistrements de base de données en cliquant sur les boutons **Suivant** et **Précédent**.  
  
#### Pour tester le complément VSTO  
  
1.  Appuyez sur **F5**.  
  
     Un contrôle de contenu nommé `customerContentControl` est créé et rempli avec des données. En même temps, un objet dataset nommé `adventureWorksLTDataSet` et un <xref:System.Windows.Forms.BindingSource> nommé `customerBindingSource` sont ajoutés au projet. Le <xref:Microsoft.Office.Tools.Word.ContentControl> est lié au <xref:System.Windows.Forms.BindingSource>, qui est lui\-même lié à l’objet dataset.  
  
2.  Cliquez sur les boutons **Suivant** et **Précédent** pour parcourir les enregistrements de base de données.  
  
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
 [Comment : remplir des documents avec les données d'objets](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Comment : mettre à jour une source de données avec les données d'un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Vue d'ensemble de l'utilisation de fichiers de base de données locaux dans les solutions Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Connexion à des données dans des applications Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Vue d'ensemble du composant BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  