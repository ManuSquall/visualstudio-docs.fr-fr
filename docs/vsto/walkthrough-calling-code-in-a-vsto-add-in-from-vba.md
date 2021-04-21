---
title: 'Procédure pas à pas : appel de code dans un complément VSTO à partir de VBA'
description: Découvrez comment exposer un objet dans un complément VSTO à d’autres solutions Microsoft Office, notamment des compléments Visual Basic pour Applications (VBA) et COM VSTO.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 21e0928396327911ea794c6270340c6efd27a43e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824599"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Procédure pas à pas : appel de code dans un complément VSTO à partir de VBA
  Cette procédure pas à pas montre comment exposer un objet dans un complément VSTO à d’autres solutions Microsoft Office, notamment des compléments VSTO VBA (Visual Basic pour Applications) et COM.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Bien que cette procédure pas à pas utilise spécifiquement Excel, les concepts présentés ici s'appliquent à tous les modèles de projet de complément VSTO fournis par Visual Studio.

 Cette procédure pas à pas décrit les tâches suivantes :

- Définition d'une classe pouvant être exposée à d'autres solutions Office

- Exposition de la classe à d'autres solutions Office

- Appel d'une méthode de la classe à partir du code VBA

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-the-vsto-add-in-project"></a>Créer le projet de complément VSTO
 La première étape consiste à créer un projet de complément VSTO pour Excel.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de complément VSTO Excel nommé **ExcelImportData** à l’aide du modèle de projet de complément VSTO Excel. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le fichier de code **ThisAddIn. cs** ou **ThisAddIn. vb** et ajoute le projet **ExcelImportData** à **Explorateur de solutions**.

## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Définir une classe que vous pouvez exposer à d’autres solutions Office
 L'objectif de cette procédure pas à pas est d'appeler la méthode `ImportData` d'une classe nommée `AddInUtilities` dans votre complément VSTO à partir du code VBA. Cette méthode écrit une chaîne dans la cellule A1 de la feuille de calcul active.

 Pour exposer la classe `AddInUtilities` à d'autres solutions Office, vous devez faire rendre la classe publique et visible par COM. Vous devez également exposer l'interface [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) dans la classe. Le code de la procédure suivante vous montre une façon de respecter ces exigences. Pour plus d'informations, consultez [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Pour définir une classe pouvant être exposée à d'autres solutions Office

1. Dans le menu **Projet** , cliquez sur **Ajouter une classe**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , remplacez le nom de la nouvelle classe par **AddInUtilities**, puis cliquez sur **Ajouter**.

     Le fichier **AddInUtilities.cs** ou **AddInUtilities.vb** s'ouvre dans l'éditeur de code.

3. Ajoutez les directives suivantes au début du fichier.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet2":::

4. Remplacez la classe `AddInUtilities` par le code suivant :

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet3":::

     Ce code rend la classe `AddInUtilities` visible par COM et ajoute la méthode `ImportData` à la classe. Pour exposer l'interface [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) , la classe `AddInUtilities` possède également l'attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> et implémente une interface visible par COM.

## <a name="expose-the-class-to-other-office-solutions"></a>Exposer la classe à d’autres solutions Office
 Pour exposer la classe `AddInUtilities` à d'autres solutions Office, substituez la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> dans la classe `ThisAddIn` . Dans la substitution, retournez une instance de la classe `AddInUtilities` .

### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>Pour exposer la classe AddInUtilities à d'autres Solutions Office

1. Dans l' **Explorateur de solutions**, développez **Excel**.

2. Cliquez avec le bouton droit sur **ThisAddIn.cs** ou **ThisAddIn.vb**, puis cliquez sur **Afficher le code**.

3. Ajoutez le code suivant à la classe `ThisAddIn` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb" id="Snippet1":::

4. Dans le menu **Générer**, cliquez sur **Générer la solution**.

     Vérifiez que la solution se génère sans erreur.

## <a name="test-the-vsto-add-in"></a>Tester le complément VSTO
 Vous pouvez exécuter un appel dans la classe `AddInUtilities` à partir de différents types de solutions Office. Dans cette procédure pas à pas, vous allez utiliser du code VBA dans un classeur Excel. Pour plus d’informations sur les autres types de solutions Office que vous pouvez également utiliser, consultez [appeler du code dans des compléments VSTO à partir d’autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

### <a name="to-test-your-vsto-add-in"></a>Pour tester votre complément VSTO

1. Appuyez sur **F5** pour exécuter votre projet.

2. Dans Excel, enregistrez le classeur actif en tant que classeur Excel prenant en charge les macros (*.xlsm) dans un emplacement pratique, tel que le Bureau.

3. Dans le ruban, cliquez sur l'onglet **Développeur** .

    > [!NOTE]
    > Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d’informations, consultez [Comment : afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Dans le groupe **Code** , cliquez sur **Visual Basic**.

     Visual Basic Editor s'ouvre.

5. Dans la fenêtre **Projet** , double-cliquez sur **ThisWorkbook**.

     Le fichier de code de l'objet `ThisWorkbook` s'ouvre.

6. Ajoutez le code VBA suivant au fichier de code. Ce code obtient d’abord un objet COMAddIn qui représente le complément VSTO **ExcelImportData** . Ensuite, le code utilise la propriété Object de l’objet COMAddIn pour appeler la `ImportData` méthode.

    ```vb
    Sub CallVSTOMethod()
        Dim addIn As COMAddIn
        Dim automationObject As Object
        Set addIn = Application.COMAddIns("ExcelImportData")
        Set automationObject = addIn.Object
        automationObject.ImportData
    End Sub
    ```

7. Appuyez sur **F5**.

8. Assurez-vous qu'une nouvelle feuille de calcul **Imported Data** a été ajoutée au classeur. Vérifiez également que la cellule A1 contient la chaîne **This is my data**.

9. Quittez Excel.

## <a name="next-steps"></a>Étapes suivantes
 Pour en savoir plus sur la programmation de compléments VSTO, consultez les rubriques suivantes :

- Utiliser la classe `ThisAddIn` pour automatiser l'application hôte et effectuer d'autres tâches dans les projets de complément VSTO. Pour plus d’informations, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md).

- Créer un volet des tâches personnalisé dans un complément VSTO. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md) et [Comment : ajouter un volet de tâches personnalisé à une application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

- Personnaliser le ruban dans un complément VSTO. Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md) et [Comment : prendre en main la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).

## <a name="see-also"></a>Voir aussi
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Appeler du code dans des compléments VSTO à partir d’autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Développer des solutions Office](../vsto/developing-office-solutions.md)
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Personnaliser les fonctionnalités de l’interface utilisateur à l’aide des interfaces d’extensibilité](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
