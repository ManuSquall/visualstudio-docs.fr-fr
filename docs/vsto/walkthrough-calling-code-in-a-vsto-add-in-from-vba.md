---
title: "Procédure pas à pas : Appel de Code dans un complément VSTO à partir de VBA | Documents Microsoft"
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
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 677ddfef196c79d1dd696889fd16dcfa0300ccff
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-calling-code-in-a-vsto-add-in-from-vba"></a>Procédure pas à pas : appel de code dans un complément VSTO à partir de VBA
  Cette procédure pas à pas montre comment exposer un objet dans un complément VSTO à d’autres solutions Microsoft Office, notamment des compléments VSTO VBA (Visual Basic pour Applications) et COM.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Bien que cette procédure pas à pas utilise spécifiquement Excel, les concepts présentés ici s'appliquent à tous les modèles de projet de complément VSTO fournis par Visual Studio.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Définition d'une classe pouvant être exposée à d'autres solutions Office  
  
-   Exposition de la classe à d'autres solutions Office  
  
-   Appel d'une méthode de la classe à partir du code VBA  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="creating-the-vsto-add-in-project"></a>Création du projet de complément VSTO  
 La première étape consiste à créer un projet de complément VSTO pour Excel.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créez un projet de complément VSTO Excel nommé **ExcelImportData**à l’aide du modèle de projet de complément VSTO Excel. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le fichier de code **ThisAddIn.cs** ou **ThisAddIn.vb** et ajoute le projet **ExcelImportData** à l' **Explorateur de solutions**.  
  
## <a name="defining-a-class-that-you-can-expose-to-other-office-solutions"></a>Définition d'une classe pouvant être exposée à d'autres solutions Office  
 L'objectif de cette procédure pas à pas est d'appeler la méthode `ImportData` d'une classe nommée `AddInUtilities` dans votre complément VSTO à partir du code VBA. Cette méthode écrit une chaîne dans la cellule A1 de la feuille de calcul active.  
  
 Pour exposer la classe `AddInUtilities` à d'autres solutions Office, vous devez faire rendre la classe publique et visible par COM. Vous devez également exposer l'interface [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) dans la classe. Le code de la procédure suivante vous montre une façon de respecter ces exigences. Pour plus d'informations, consultez [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
#### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Pour définir une classe pouvant être exposée à d'autres solutions Office  
  
1.  Dans le menu **Projet** , cliquez sur **Ajouter une classe**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , remplacez le nom de la nouvelle classe par **AddInUtilities**, puis cliquez sur **Ajouter**.  
  
     Le fichier **AddInUtilities.cs** ou **AddInUtilities.vb** s'ouvre dans l'éditeur de code.  
  
3.  Ajoutez les instructions suivantes au début du fichier.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#2)]  
  
4.  Remplacez la classe `AddInUtilities` par le code suivant :  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
     Ce code rend la classe `AddInUtilities` visible par COM et ajoute la méthode `ImportData` à la classe. Pour exposer l'interface [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) , la classe `AddInUtilities` possède également l'attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> et implémente une interface visible par COM.  
  
## <a name="exposing-the-class-to-other-office-solutions"></a>Exposition de la classe à d'autres solutions Office  
 Pour exposer la classe `AddInUtilities` à d'autres solutions Office, substituez la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> dans la classe `ThisAddIn` . Dans la substitution, retournez une instance de la classe `AddInUtilities` .  
  
#### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>Pour exposer la classe AddInUtilities à d'autres Solutions Office  
  
1.  Dans l' **Explorateur de solutions**, développez **Excel**.  
  
2.  Cliquez avec le bouton droit sur **ThisAddIn.cs** ou **ThisAddIn.vb**, puis cliquez sur **Afficher le code**.  
  
3.  Ajoutez le code suivant à la classe `ThisAddIn` .  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
4.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
     Vérifiez que la solution se génère sans erreur.  
  
## <a name="testing-the-vsto-add-in"></a>Test du complément VSTO  
 Vous pouvez exécuter un appel dans la classe `AddInUtilities` à partir de différents types de solutions Office. Dans cette procédure pas à pas, vous allez utiliser du code VBA dans un classeur Excel. Pour plus d’informations sur les autres types de solutions Office utilisables, consultez [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
#### <a name="to-test-your-vsto-add-in"></a>Pour tester votre complément VSTO  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Dans Excel, enregistrez le classeur actif en tant que classeur Excel prenant en charge les macros (*.xlsm) dans un emplacement pratique, tel que le Bureau.  
  
3.  Dans le ruban, cliquez sur l'onglet **Développeur** .  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, consultez [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Dans le groupe **Code** , cliquez sur **Visual Basic**.  
  
     Visual Basic Editor s'ouvre.  
  
5.  Dans la fenêtre **Projet** , double-cliquez sur **ThisWorkbook**.  
  
     Le fichier de code de l'objet `ThisWorkbook` s'ouvre.  
  
6.  Ajoutez le code VBA suivant au fichier de code. Ce code obtient d’abord un objet COMAddIn qui représente le **ExcelImportData** complément VSTO. Ensuite, le code utilise la propriété de l’objet de l’objet COMAddIn pour appeler le `ImportData` (méthode).  
  
    ```  
    Sub CallVSTOMethod()  
        Dim addIn As COMAddIn  
        Dim automationObject As Object  
        Set addIn = Application.COMAddIns("ExcelImportData")  
        Set automationObject = addIn.Object  
        automationObject.ImportData  
    End Sub  
    ```  
  
7.  Appuyez sur F5.  
  
8.  Assurez-vous qu'une nouvelle feuille de calcul **Imported Data** a été ajoutée au classeur. Vérifiez également que la cellule A1 contient la chaîne **This is my data**.  
  
9. Quittez Excel.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour en savoir plus sur la programmation de compléments VSTO, consultez les rubriques suivantes :  
  
-   Utiliser la classe `ThisAddIn` pour automatiser l'application hôte et effectuer d'autres tâches dans les projets de complément VSTO. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Créer un volet des tâches personnalisé dans un complément VSTO. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md) et [Comment : ajouter un volet de tâches personnalisé à une Application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
-   Personnaliser le ruban dans un complément VSTO. Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md) et [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Appel de Code dans des Compléments VSTO à partir d’autres Solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Développement de Solutions Office](../vsto/developing-office-solutions.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architecture des Compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Personnalisation des fonctionnalités de l’interface utilisateur à l’aide d’interfaces d’extensibilité](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  