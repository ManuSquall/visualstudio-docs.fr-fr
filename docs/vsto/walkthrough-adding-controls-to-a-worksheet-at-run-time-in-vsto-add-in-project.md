---
title: "Procédure pas à pas : Ajout de contrôles à une feuille de calcul au moment de l’exécution dans VSTO complément projet | Documents Microsoft"
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
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
ms.assetid: 4f68677a-4789-4564-b229-02e2d4031a5f
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bae6ff23763300a4baa748479c609217123c765c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>Procédure pas à pas : ajout de contrôles à une feuille de calcul au moment de l’exécution dans un projet de complément VSTO
  Vous pouvez ajouter des contrôles à une feuille de calcul ouverte en utilisant un complément Excel VSTO. Cette procédure pas à pas montre comment utiliser le ruban pour permettre aux utilisateurs d'ajouter <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> et <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul. Pour plus d’informations, consultez [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **S’applique à :** les informations contenues dans cette rubrique s’appliquent aux projets de complément VSTO pour Excel. Pour plus d'informations, consultez [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Fournit une interface utilisateur permettant d'ajouter des contrôles à la feuille de calcul.  
  
-   Ajout de contrôles à la feuille de calcul.  
  
-   Suppression de contrôles dans la feuille de calcul.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## <a name="creating-a-new-excel-vsto-add-in-project"></a>Création d'un projet de complément Excel VSTO  
 Commencez par créer un projet de complément Excel VSTO.  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Pour créer un projet de complément Excel VSTO  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez un projet de complément Excel VSTO nommé **ExcelDynamicControls**. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Ajoutez une référence à la **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** assembly. Cette référence est obligatoire pour ajouter par programmation un contrôle Windows Forms à une feuille de calcul, plus loin dans cette procédure pas à pas.  
  
## <a name="providing-a-ui-to-add-controls-to-a-worksheet"></a>Mise à disposition d'une interface utilisateur permettant d'ajouter des contrôles à une feuille de calcul  
 Ajoutez un onglet personnalisé au ruban Excel. Les utilisateurs peuvent cocher des cases sous l'onglet pour ajouter des contrôles à une feuille de calcul.  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Pour fournir une interface utilisateur permettant d'ajouter des contrôles à une feuille de calcul  
  
1.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **ruban (Concepteur visuel)**, puis cliquez sur **ajouter**.  
  
     Un fichier nommé **Ribbon1.cs** ou **Ribbon1.vb** s’ouvre dans le Concepteur de ruban et affiche un onglet par défaut et un groupe.  
  
3.  À partir de la **contrôles de ruban Office** onglet de la **boîte à outils**, faites glisser un contrôle de case à cocher dans **group1**.  
  
4.  Cliquez sur **CheckBox1** pour le sélectionner.  
  
5.  Dans la fenêtre **Propriétés** , changez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**Button**|  
    |**Label**|**Button**|  
  
6.  Ajoutez une deuxième case à cocher pour **group1**, puis modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**NamedRange**|  
    |**Label**|**NamedRange**|  
  
7.  Ajoutez une troisième case à cocher pour **group1**, puis modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**ListObject**|  
    |**Label**|**ListObject**|  
  
## <a name="adding-controls-to-the-worksheet"></a>Ajout de contrôles à la feuille de calcul  
 Les contrôles managés ne peuvent être ajoutés qu'aux éléments hôtes, lesquels servent de conteneurs. Dans la mesure où les projets de complément VSTO fonctionnent avec n'importe quel classeur ouvert, le complément VSTO convertit la feuille de calcul en élément hôte, ou récupère un élément hôte existant, avant d'ajouter le contrôle. Ajoutez du code aux gestionnaires d'événements click de chaque contrôle pour générer un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> basé sur la feuille de calcul ouverte. Ajoutez ensuite <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> et <xref:Microsoft.Office.Tools.Excel.ListObject> à la sélection actuelle dans la feuille de calcul.  
  
#### <a name="to-add-controls-to-a-worksheet"></a>Pour ajouter des contrôles à une feuille de calcul  
  
1.  Dans le Concepteur de ruban, double-cliquez sur **bouton**.  
  
     Le <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Gestionnaire d’événements de la **bouton** case à cocher s’ouvre dans l’éditeur de Code.  
  
2.  Remplacez le gestionnaire d'événements `Button_Click` par le code suivant.  
  
     Ce code utilise la méthode `GetVstoObject` pour obtenir un élément hôte qui représente la première feuille de calcul du classeur, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.Controls.Button> à la cellule sélectionnée.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]  
  
3.  Dans **l’Explorateur de solutions**, sélectionnez Ribbon1.cs ou Ribbon1.vb.  
  
4.  Sur le **vue** menu, cliquez sur **concepteur**.  
  
5.  Dans le Concepteur de ruban, double-cliquez sur **NamedRange**.  
  
6.  Remplacez le gestionnaire d'événements `NamedRange_Click` par le code suivant.  
  
     Ce code utilise la méthode `GetVstoObject` pour obtenir un élément hôte qui représente la première feuille de calcul du classeur, puis définit un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> pour la ou les cellules sélectionnées.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]  
  
7.  Dans le Concepteur de ruban, double-cliquez sur **ListObject**.  
  
8.  Remplacez le gestionnaire d'événements `ListObject_Click` par le code suivant.  
  
     Ce code utilise la méthode `GetVstoObject` pour obtenir un élément hôte qui représente la première feuille de calcul du classeur, puis définit un <xref:Microsoft.Office.Tools.Excel.ListObject> pour la ou les cellules sélectionnées.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]  
  
9. Ajoutez les instructions suivantes au début du fichier de code du ruban.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]  
  
## <a name="removing-controls-from-the-worksheet"></a>Suppression de contrôles dans la feuille de calcul  
 Les contrôles ne sont pas conservés quand la feuille de calcul est enregistrée et fermée. Supprimez par programmation tous les contrôles Windows Forms générés avant que la feuille de calcul ne soit enregistrée. Sinon, seul le contour du contrôle apparaît quand vous rouvrez le classeur. Ajoutez du code à l'événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> qui supprime les contrôles Windows Forms dans la collection de contrôles de l'élément hôte généré. Pour plus d'informations, consultez [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
#### <a name="to-remove-controls-from-the-worksheet"></a>Pour supprimer des contrôles dans la feuille de calcul  
  
1.  Dans **l’Explorateur de solutions**, sélectionnez ThisAddIn.cs ou ThisAddIn.vb.  
  
2.  Sur le **vue** menu, cliquez sur **Code**.  
  
3.  Ajoutez la méthode suivante à la classe ThisAddIn. Ce code récupère la première feuille de calcul du classeur, puis utilise la méthode `HasVstoObject` pour vérifier si la feuille de calcul possède un objet de feuille de calcul généré. Si l’objet de feuille de calcul généré possède des contrôles, le code récupère cet objet de feuille de calcul, puis effectue une itération dans la collection de contrôles, en supprimant ces derniers.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]  
  
4.  En C#, vous devez créer un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>. Vous pouvez placer ce code dans la méthode `ThisAddIn_Startup`. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md). Remplacez la méthode `ThisAddIn_Startup` par le code suivant.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]  
  
## <a name="testing-the-solution"></a>Test de la solution  
 Ajoutez des contrôles à une feuille de calcul en les sélectionnant à partir d'un onglet personnalisé sur le ruban. Quand vous enregistrez la feuille de calcul, ces contrôles sont supprimés.  
  
#### <a name="to-test-the-solution"></a>Pour tester la solution.  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Sélectionnez n'importe quelle cellule dans Feuil1.  
  
3.  Cliquez sur l'onglet **Compléments** .  
  
4.  Dans le **group1** , cliquez sur **bouton**.  
  
     Un bouton s'affiche dans la cellule sélectionnée.  
  
5.  Sélectionnez une autre cellule dans Feuil1.  
  
6.  Dans le **group1** , cliquez sur **NamedRange**.  
  
     Une plage nommée est définie pour la cellule sélectionnée.  
  
7.  Sélectionnez une série de cellules dans Feuil1.  
  
8.  Dans le **group1** , cliquez sur **ListObject**.  
  
     Un objet de liste est ajouté pour les cellules sélectionnées.  
  
9. Enregistrez la feuille de calcul.  
  
     Les contrôles que vous avez ajoutés à Feuil1 ne s'affichent plus.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d’informations sur les contrôles dans les projets de complément Excel VSTO, consultez cette rubrique :  
  
-   Pour savoir comment enregistrer des contrôles dans une feuille de calcul, consultez l’exemple de contrôles dynamiques de complément Excel VSTO dans [exemples de développement Office et des procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Excel](../vsto/excel-solutions.md)   
 [Contrôles Windows Forms dans une vue d’ensemble des Documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [ListObject, contrôle](../vsto/listobject-control.md)  
  
  