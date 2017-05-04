---
title: "Proc&#233;dure pas &#224; pas&#160;: appel de code dans un compl&#233;ment VSTO &#224; partir de VBA | Microsoft Docs"
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
  - "VBA (développement Office dans Visual Studio), appel de code dans les compléments au niveau de l’application"
  - "compléments au niveau de l’application (développement Office dans Visual Studio), appel de code à partir d’autres solutions"
  - "vidéos pratiques, développement Office dans Visual Studio"
  - "appeler du code de complément"
  - "compléments (développement Office dans Visual Studio), appel de code à partir d’autres solutions"
  - "interopérabilité (développement Office dans Visual Studio)"
  - "appeler du code à partir de VBA"
ms.assetid: 9c04d1df-0d93-473c-85fd-02dc2e956c9e
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Proc&#233;dure pas &#224; pas&#160;: appel de code dans un compl&#233;ment VSTO &#224; partir de VBA
  Cette procédure pas à pas montre comment exposer un objet dans un complément VSTO à d’autres solutions Microsoft Office, notamment des compléments VSTO VBA \(Visual Basic pour Applications\) et COM.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Bien que cette procédure pas à pas utilise spécifiquement Excel, les concepts présentés ici s'appliquent à tous les modèles de projet de complément VSTO fournis par Visual Studio.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Définition d'une classe pouvant être exposée à d'autres solutions Office  
  
-   Exposition de la classe à d'autres solutions Office  
  
-   Appel d'une méthode de la classe à partir du code VBA  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## Création du projet de complément VSTO  
 La première étape consiste à créer un projet de complément VSTO pour Excel.  
  
#### Pour créer un projet  
  
1.  Créez un projet de complément VSTO Excel nommé **ExcelImportData** à l’aide du modèle de projet de complément VSTO Excel. Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le fichier de code **ThisAddIn.cs** ou **ThisAddIn.vb** et ajoute le projet **ExcelImportData** à l'**Explorateur de solutions**.  
  
## Définition d'une classe pouvant être exposée à d'autres solutions Office  
 L'objectif de cette procédure pas à pas est d'appeler la méthode `ImportData` d'une classe nommée `AddInUtilities` dans votre complément VSTO à partir du code VBA. Cette méthode écrit une chaîne dans la cellule A1 de la feuille de calcul active.  
  
 Pour exposer la classe `AddInUtilities` à d'autres solutions Office, vous devez faire rendre la classe publique et visible par COM. Vous devez également exposer l'interface [IDispatch](http://msdn.microsoft.com/fr-fr/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) dans la classe. Le code de la procédure suivante vous montre une façon de respecter ces exigences. Pour plus d'informations, consultez [Appel de code dans des compléments VSTO à partir d'autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
#### Pour définir une classe pouvant être exposée à d'autres solutions Office  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter une classe**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, remplacez le nom de la nouvelle classe par **AddInUtilities**, puis cliquez sur **Ajouter**.  
  
     Le fichier **AddInUtilities.cs** ou **AddInUtilities.vb** s'ouvre dans l'éditeur de code.  
  
3.  Ajoutez les instructions suivantes au début du fichier.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/AddInUtilities.vb#2)]  
  
4.  Remplacez la classe `AddInUtilities` par le code suivant :  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/AddInUtilities.vb#3)]  
  
     Ce code rend la classe `AddInUtilities` visible par COM et ajoute la méthode `ImportData` à la classe. Pour exposer l'interface [IDispatch](http://msdn.microsoft.com/fr-fr/ebbff4bc-36b2-4861-9efa-ffa45e013eb5), la classe `AddInUtilities` possède également l'attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> et implémente une interface visible par COM.  
  
## Exposition de la classe à d'autres solutions Office  
 Pour exposer la classe `AddInUtilities` à d'autres solutions Office, substituez la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> dans la classe `ThisAddIn`. Dans la substitution, retournez une instance de la classe `AddInUtilities`.  
  
#### Pour exposer la classe AddInUtilities à d'autres Solutions Office  
  
1.  Dans l'**Explorateur de solutions**, développez **Excel**.  
  
2.  Cliquez avec le bouton droit sur **ThisAddIn.cs** ou **ThisAddIn.vb**, puis cliquez sur **Afficher le code**.  
  
3.  Ajoutez le code suivant à la classe `ThisAddIn`.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/ThisAddIn.vb#1)]  
  
4.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
     Vérifiez que la solution se génère sans erreur.  
  
## Test du complément VSTO  
 Vous pouvez exécuter un appel dans la classe `AddInUtilities` à partir de différents types de solutions Office. Dans cette procédure pas à pas, vous allez utiliser du code VBA dans un classeur Excel. Pour plus d’informations sur les autres types de solutions Office utilisables, consultez [Appel de code dans des compléments VSTO à partir d'autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
#### Pour tester votre complément VSTO  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Dans Excel, enregistrez le classeur actif en tant que classeur Excel prenant en charge les macros \(\*.xlsm\) dans un emplacement pratique, tel que le Bureau.  
  
3.  Dans le ruban, cliquez sur l'onglet **Développeur**.  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Dans le groupe **Code**, cliquez sur **Visual Basic**.  
  
     Visual Basic Editor s'ouvre.  
  
5.  Dans la fenêtre **Projet**, double\-cliquez sur **ThisWorkbook**.  
  
     Le fichier de code de l'objet `ThisWorkbook` s'ouvre.  
  
6.  Ajoutez le code VBA suivant au fichier de code. Dans un premier temps, le code obtient un objet COMAddIn qui représente le complément VSTO **ExcelImportData**. Il utilise ensuite la propriété Object de l'objet COMAddIn pour appeler la méthode `ImportData`.  
  
    ```  
    Sub CallVSTOMethod() Dim addIn As COMAddIn Dim automationObject As Object Set addIn = Application.COMAddIns("ExcelImportData") Set automationObject = addIn.Object automationObject.ImportData End Sub  
    ```  
  
7.  Appuyez sur F5.  
  
8.  Assurez\-vous qu'une nouvelle feuille de calcul **Imported Data** a été ajoutée au classeur. Vérifiez également que la cellule A1 contient la chaîne **This is my data**.  
  
9. Quittez Excel.  
  
## Étapes suivantes  
 Pour en savoir plus sur la programmation de compléments VSTO, consultez les rubriques suivantes :  
  
-   Utiliser la classe `ThisAddIn` pour automatiser l'application hôte et effectuer d'autres tâches dans les projets de complément VSTO. Pour plus d'informations, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Créer un volet des tâches personnalisé dans un complément VSTO. Pour plus d’informations, consultez [Volets de tâches personnalisés](../vsto/custom-task-panes.md) et [Comment : ajouter un volet de tâches personnalisé à une application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
-   Personnaliser le ruban dans un complément VSTO. Pour plus d’informations, consultez [Vue d'ensemble du ruban](../vsto/ribbon-overview.md) et [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
## Voir aussi  
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Appel de code dans des compléments VSTO à partir d'autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Développement de solutions Office](../vsto/developing-office-solutions.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Personnalisation des fonctionnalités de l'interface utilisateur à l'aide d'interfaces d'extensibilité](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  