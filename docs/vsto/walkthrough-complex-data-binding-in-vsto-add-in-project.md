---
title: "Procédure pas à pas : Liaison de données complexe dans VSTO complément projet | Documents Microsoft"
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
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
ms.assetid: ff52fb56-1f67-4ae2-a3d1-93038619d4e6
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 02db64a64cdf6e8cdbaf7a0d99044e2b8e9071c4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Procédure pas à pas : liaison de données complexe dans un projet de complément VSTO
  Vous pouvez lier des données à des contrôles hôtes et des contrôles Windows Forms dans des projets de complément VSTO. Cette procédure pas à pas montre comment ajouter des contrôles à une feuille de calcul Microsoft Office Excel et les lier à des données au moment de l’exécution.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout d’un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul au moment de l’exécution.  
  
-   Création d’un <xref:System.Windows.Forms.BindingSource> qui connecte le contrôle à une instance d’un dataset.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accès à une instance en cours d’exécution de SQL Server 2005 ou SQL Server 2005 Express à laquelle l’exemple de base de données `AdventureWorksLT` est attaché. Vous pouvez télécharger la base de données `AdventureWorksLT` à partir du [site web CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Pour plus d’informations sur l’attachement d’une base de données, consultez les rubriques suivantes :  
  
    -   Pour attacher une base de données à l’aide de SQL Server Management Studio ou de SQL Server Management Studio Express, consultez [Comment : attacher une base de données (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Pour attacher une base de données à l’aide de la ligne de commande, consultez [Comment : attacher un fichier de base de données à SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="creating-a-new-project"></a>Création d'un projet  
 La première étape consiste à créer un projet de complément VSTO Excel.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créez un projet de complément VSTO Excel nommé **Remplissage de feuilles de calcul à partir d’une base de données**, à l’aide de Visual Basic ou C#.  
  
     Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le fichier `ThisAddIn.vb` or `ThisAddIn.cs` , et ajoute le projet **Remplissage de feuilles de calcul à partir d’une base de données** dans l’ **Explorateur de solutions**.  
  
## <a name="creating-a-data-source"></a>Création d’une source de données  
 Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.  
  
#### <a name="to-add-a-typed-dataset-to-the-project"></a>Pour ajouter un dataset typé au projet  
  
1.  Si la fenêtre **Sources de données** n'est pas visible, affichez-la en choisissant, dans la barre de menus, **Affichage**, **Autres fenêtres**, **Sources de données**.  
  
2.  Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.  
  
3.  Cliquez sur **Base de données**, puis sur **Suivant**.  
  
4.  Si vous disposez d’une connexion à la base de données `AdventureWorksLT` , choisissez cette connexion et cliquez sur **Suivant**.  
  
     Sinon, cliquez sur **Nouvelle connexion**et utilisez la boîte de dialogue **Ajouter une connexion** pour créer la connexion. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).  
  
5.  Dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , cliquez sur **Suivant**.  
  
6.  Dans la page **Choisir vos objets de base de données** , développez **Tables** et sélectionnez **Address (SalesLT)**.  
  
7.  Cliquez sur **Terminer**.  
  
     Le fichier AdventureWorksLTDataSet.xsd est ajouté dans l’ **Explorateur de solutions**. Ce fichier définit les éléments suivants :  
  
    -   Un dataset typé nommé `AdventureWorksLTDataSet`. Ce dataset représente le contenu de la table **Address (SalesLT)** dans la base de données AdventureWorksLT.  
  
    -   Un TableAdapter nommé `AddressTableAdapter`. Ce TableAdapter peut être utilisé pour lire et écrire des données le `AdventureWorksLTDataSet`. Pour plus d'informations, consultez [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Vous utiliserez ces deux objets ultérieurement dans cette procédure pas à pas.  
  
## <a name="creating-controls-and-binding-controls-to-data"></a>Création et liaison de contrôles à des données  
 Pour cette procédure pas à pas, le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> affiche toutes les données dans la table que vous avez sélectionnée dès que l’utilisateur ouvre le classeur. L’objet de liste utilise un <xref:System.Windows.Forms.BindingSource> pour connecter le contrôle à la base de données.  
  
 Pour plus d’informations sur la liaison des contrôles aux données, consultez [Binding Data to Controls in Office Solutions](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Pour ajouter l’objet de liste, le dataset et l’adaptateur de table  
  
1.  Dans la classe `ThisAddIn` , déclarez les contrôles suivants pour afficher la table `Address` du dataset `AdventureWorksLTDataSet` .  
  
     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]  
  
2.  Dans la méthode `ThisAddIn_Startup` , ajoutez le code suivant pour initialiser le dataset et le remplir avec des informations issues du dataset `AdventureWorksLTDataSet` .  
  
     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]  
  
3.  Ajoutez le code suivant à la méthode `ThisAddIn_Startup` . Cela génère un élément hôte qui étend la feuille de calcul. Pour plus d'informations, consultez [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]  
  
4.  Créez une plage et ajoutez le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> .  
  
     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]  
  
5.  Liez l’objet de liste à `AdventureWorksLTDataSet` en utilisant <xref:System.Windows.Forms.BindingSource>. Passez les noms des colonnes que vous souhaitez lier à l’objet de liste.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]  
  
## <a name="testing-the-add-in"></a>Test du complément  
 Quand vous ouvrez Excel, le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> affiche les données de la table `Address` du dataset `AdventureWorksLTDataSet` .  
  
#### <a name="to-test-the-vsto-add-in"></a>Pour tester le complément VSTO  
  
-   Appuyez sur **F5**.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `addressListObject` est créé dans la feuille de calcul. Au même moment, un objet dataset nommé `adventureWorksLTDataSet` et un <xref:System.Windows.Forms.BindingSource> nommé `addressBindingSource` sont ajoutés au projet. <xref:Microsoft.Office.Tools.Excel.ListObject> est lié à <xref:System.Windows.Forms.BindingSource>, qui est lui-même lié à l’objet dataset.  
  
## <a name="see-also"></a>Voir aussi  
 [Données dans les Solutions Office](../vsto/data-in-office-solutions.md)   
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Comment : remplir des feuilles de calcul avec des données à partir d’une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Comment : remplir des Documents avec les données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Comment : remplir des Documents avec des données à partir des Services](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Comment : remplir des Documents avec les données d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Comment : faire défiler des enregistrements de base de données dans une feuille de calcul](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Comment : mettre à jour une Source de données avec des données à partir d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Procédure pas à pas : Liaison de données Simple dans un projet au niveau du Document](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [Procédure pas à pas : Liaison de données complexe dans un projet au niveau du Document](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [L’utilisation de fichiers de base de données locale dans la vue d’ensemble des Solutions Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [L’utilisation de fichiers de base de données locale dans la vue d’ensemble des Solutions Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Connexion aux données dans les Applications Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Vue d'ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  