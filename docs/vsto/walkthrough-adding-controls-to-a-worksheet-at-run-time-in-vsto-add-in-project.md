---
title: Ajouter des contrôles à la feuille de calcul au moment de l’exécution dans un projet de complément VSTO
description: Découvrez comment utiliser le ruban pour permettre aux utilisateurs d’ajouter un bouton, un NamedRange et un ListObject à une feuille de calcul.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bc6c608d406cabe6962a47dae4c86fa7503a05a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921789"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>Procédure pas à pas : ajout de contrôles à une feuille de calcul au moment de l’exécution dans un projet de complément VSTO
  Vous pouvez ajouter des contrôles à une feuille de calcul ouverte en utilisant un complément Excel VSTO. Cette procédure pas à pas montre comment utiliser le ruban pour permettre aux utilisateurs d'ajouter <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> et <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

 **S’applique à :** Les informations contenues dans cette rubrique s’appliquent aux projets de compléments VSTO pour Excel. Pour plus d'informations, consultez [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).

 Cette procédure pas à pas décrit les tâches suivantes :

- Fournit une interface utilisateur permettant d'ajouter des contrôles à la feuille de calcul.

- Ajout de contrôles à la feuille de calcul.

- Suppression de contrôles dans la feuille de calcul.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Excel

## <a name="create-a-new-excel-vsto-add-in-project"></a>Créer un projet de complément Excel VSTO
 Commencez par créer un projet de complément Excel VSTO.

### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Pour créer un projet de complément Excel VSTO

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , créez un projet de complément VSTO Excel nommé **ExcelDynamicControls**. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Ajoutez une référence à l’assembly de **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** . Cette référence est obligatoire pour ajouter par programmation un contrôle Windows Forms à une feuille de calcul, plus loin dans cette procédure pas à pas.

## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Fournir une interface utilisateur pour ajouter des contrôles à une feuille de calcul
 Ajoutez un onglet personnalisé au ruban Excel. Les utilisateurs peuvent cocher des cases sous l'onglet pour ajouter des contrôles à une feuille de calcul.

#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Pour fournir une interface utilisateur permettant d'ajouter des contrôles à une feuille de calcul

1. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Ruban (concepteur visuel)**, puis cliquez sur **Ajouter**.

     Un fichier nommé **Ribbon1.cs** ou **Ribbon1. vb** s’ouvre dans le concepteur de ruban et affiche un onglet et un groupe par défaut.

3. Sous l’onglet **Contrôles de ruban Office** de la **Boîte à outils**, faites glisser un contrôle CheckBox sur **group1**.

4. Cliquez sur **CheckBox1** pour le sélectionner.

5. Dans la fenêtre **Propriétés** , changez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**Button**|
    |**Étiquette**|**Button**|

6. Ajoutez une deuxième case à cocher pour **group1**, puis modifiez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**NamedRange**|
    |**Étiquette**|**NamedRange**|

7. Ajoutez une troisième case à cocher à **Group1**, puis modifiez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**ListObject**|
    |**Étiquette**|**ListObject**|

## <a name="add-controls-to-the-worksheet"></a>Ajouter des contrôles à la feuille de calcul
 Les contrôles managés ne peuvent être ajoutés qu'aux éléments hôtes, lesquels servent de conteneurs. Dans la mesure où les projets de complément VSTO fonctionnent avec n'importe quel classeur ouvert, le complément VSTO convertit la feuille de calcul en élément hôte, ou récupère un élément hôte existant, avant d'ajouter le contrôle. Ajoutez du code aux gestionnaires d'événements click de chaque contrôle pour générer un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> basé sur la feuille de calcul ouverte. Ajoutez ensuite <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> et <xref:Microsoft.Office.Tools.Excel.ListObject> à la sélection actuelle dans la feuille de calcul.

### <a name="to-add-controls-to-a-worksheet"></a>Pour ajouter des contrôles à une feuille de calcul

1. Dans le concepteur de ruban, double-cliquez sur **Button**.

     Le <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Gestionnaire d’événements de la case à cocher du **bouton** s’ouvre dans l’éditeur de code.

2. Remplacez le gestionnaire d'événements `Button_Click` par le code suivant.

     Ce code utilise la méthode `GetVstoObject` pour obtenir un élément hôte qui représente la première feuille de calcul du classeur, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.Controls.Button> à la cellule sélectionnée.

     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]

3. Dans **Explorateur de solutions**, sélectionnez *Ribbon1.cs* ou *Ribbon1. vb*.

4. Dans le menu **affichage** , cliquez sur **Concepteur**.

5. Dans le concepteur de ruban, double-cliquez sur **NamedRange**.

6. Remplacez le gestionnaire d'événements `NamedRange_Click` par le code suivant.

     Ce code utilise la méthode `GetVstoObject` pour obtenir un élément hôte qui représente la première feuille de calcul du classeur, puis définit un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> pour la ou les cellules sélectionnées.

     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]

7. Dans le concepteur de ruban, double-cliquez sur **ListObject**.

8. Remplacez le gestionnaire d'événements `ListObject_Click` par le code suivant.

     Ce code utilise la méthode `GetVstoObject` pour obtenir un élément hôte qui représente la première feuille de calcul du classeur, puis définit un <xref:Microsoft.Office.Tools.Excel.ListObject> pour la ou les cellules sélectionnées.

     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]

9. Ajoutez les instructions suivantes au début du fichier de code du ruban.

     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]

## <a name="remove-controls-from-the-worksheet"></a>Supprimer des contrôles de la feuille de calcul
 Les contrôles ne sont pas conservés quand la feuille de calcul est enregistrée et fermée. Supprimez par programmation tous les contrôles Windows Forms générés avant que la feuille de calcul ne soit enregistrée. Sinon, seul le contour du contrôle apparaît quand vous rouvrez le classeur. Ajoutez du code à l'événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> qui supprime les contrôles Windows Forms dans la collection de contrôles de l'élément hôte généré. Pour plus d’informations, consultez [persistance des contrôles dynamiques dans les documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

### <a name="to-remove-controls-from-the-worksheet"></a>Pour supprimer des contrôles dans la feuille de calcul

1. Dans **Explorateur de solutions**, sélectionnez *ThisAddIn.cs* ou *ThisAddIn. vb*.

2. Dans le menu **Affichage** , cliquez sur **Code**.

3. Ajoutez la méthode suivante à la classe `ThisAddIn`. Ce code récupère la première feuille de calcul du classeur, puis utilise la méthode `HasVstoObject` pour vérifier si la feuille de calcul possède un objet de feuille de calcul généré. Si l'objet de feuille de calcul généré possède des contrôles, le code récupère cet objet de feuille de calcul, puis effectue une itération dans la collection de contrôles, en supprimant ces derniers.

     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]

4. En C#, vous devez créer un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>. Vous pouvez placer ce code dans la méthode `ThisAddIn_Startup`. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md). Remplacez la méthode `ThisAddIn_Startup` par le code suivant.

     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]

## <a name="test-the-solution"></a>Test de la solution
 Ajoutez des contrôles à une feuille de calcul en les sélectionnant à partir d’un onglet personnalisé sur le ruban. Quand vous enregistrez la feuille de calcul, ces contrôles sont supprimés.

### <a name="to-test-the-solution"></a>Pour tester la solution.

1. Appuyez sur **F5** pour exécuter votre projet.

2. Sélectionnez n'importe quelle cellule dans Feuil1.

3. Cliquez sur l'onglet **Compléments** .

4. Dans le groupe **Group1** , cliquez sur **bouton**.

     Un bouton s'affiche dans la cellule sélectionnée.

5. Sélectionnez une autre cellule dans Feuil1.

6. Dans le groupe **Group1** , cliquez sur **NamedRange**.

     Une plage nommée est définie pour la cellule sélectionnée.

7. Sélectionnez une série de cellules dans Feuil1.

8. Dans le groupe **Group1** , cliquez sur **ListObject**.

     Un objet de liste est ajouté pour les cellules sélectionnées.

9. Enregistrez la feuille de calcul.

     Les contrôles que vous avez ajoutés à Feuil1 ne s'affichent plus.

## <a name="next-steps"></a>Étapes suivantes
 Pour plus d’informations sur les contrôles dans les projets de complément Excel VSTO, consultez cette rubrique :

- Pour en savoir plus sur l’enregistrement de contrôles dans une feuille de calcul, consultez l’exemple de contrôles dynamiques de compléments VSTO Excel dans [exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="see-also"></a>Voir aussi
- [Solutions Excel](../vsto/excel-solutions.md)
- [Vue d’ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [ListObject (contrôle)](../vsto/listobject-control.md)
