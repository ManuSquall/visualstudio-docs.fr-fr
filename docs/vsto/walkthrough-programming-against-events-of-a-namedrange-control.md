---
title: "Procédure pas à pas : Programmation d’événements d’un contrôle NamedRange | Documents Microsoft"
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
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: "57"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 40076f607e66ec76aaa42ae297d22b38a6234ab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-programming-against-events-of-a-namedrange-control"></a>Procédure pas à pas : programmation d'événements d'un contrôle NamedRange
  Cette procédure pas à pas montre comment ajouter un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à une feuille de calcul Microsoft Office Excel et de programmer ses événements à l’aide des outils de développement Office dans Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Pendant cette procédure pas à pas, vous allez apprendre à :  
  
-   Ajouter un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à une feuille de calcul.  
  
-   Programmer <xref:Microsoft.Office.Tools.Excel.NamedRange> événements de contrôle.  
  
-   Votre projet de test.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
 Dans cette étape, vous allez créer un projet de classeur Excel à l’aide de Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de classeur Excel portant le nom **My Named Range Events**. Assurez-vous que **créer un nouveau document** est sélectionnée. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le **My Named Range Events** projet **l’Explorateur de solutions**.  
  
## <a name="adding-text-and-named-ranges-to-the-worksheet"></a>Ajout de texte et plages nommées à la feuille de calcul  
 Étant donné que les contrôles hôtes sont des objets Office étendus, vous pouvez les ajouter à votre document de la même manière, vous devez ajouter l’objet natif. Par exemple, vous pouvez ajouter d’Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à une feuille de calcul en ouvrant le **insérer** menu, pointez sur **nom**et en choisissant **définir**. Vous pouvez également ajouter un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle en le faisant glisser à partir de la **boîte à outils** sur la feuille de calcul.  
  
 Dans cette étape, vous allez ajouter deux contrôles de plage nommée à la feuille de calcul à l’aide de la **boîte à outils**, puis ajoutez le texte à la feuille de calcul.  
  
#### <a name="to-add-a-range-to-your-worksheet"></a>Pour ajouter une plage à votre feuille de calcul  
  
1.  Vérifiez que le **mes Events.xlsx de plage nommée** classeur est ouvert dans le concepteur Visual Studio, avec `Sheet1` affiché.  
  
2.  À partir de la **contrôles Excel** onglet de la boîte à outils, faites glisser un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle cellule **A1** dans `Sheet1`.  
  
     Le **ajouter un contrôle NamedRange** boîte de dialogue s’affiche.  
  
3.  Vérifiez que **$A$ 1** s’affiche dans la zone de texte modifiable et que la cellule **A1** est sélectionnée. Si elle n’est pas le cas, cliquez sur cellule **A1** pour le sélectionner.  
  
4.  Cliquez sur **OK**.  
  
     Cellule **A1** devient une plage nommée `namedRange1`. Il n’existe aucune indication visible sur la feuille de calcul, mais `namedRange1` s’affiche dans le **nom** zone (située juste au-dessus de la feuille de calcul sur le côté gauche) lorsque la cellule **A1** est sélectionnée.  
  
5.  Ajoutez un autre <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle cellule **B3**.  
  
6.  Vérifiez que **$B$ 3** s’affiche dans la zone de texte modifiable et que la cellule **B3** est sélectionnée. Si elle n’est pas le cas, cliquez sur cellule **B3** pour le sélectionner.  
  
7.  Cliquez sur **OK**.  
  
     Cellule **B3** devient une plage nommée `namedRange2`.  
  
#### <a name="to-add-text-to-your-worksheet"></a>Pour ajouter du texte à votre feuille de calcul  
  
1.  Dans la cellule **A1**, tapez le texte suivant :  
  
     **Il s’agit d’un exemple d’un contrôle NamedRange.**  
  
2.  Dans la cellule **A3** (à gauche de `namedRange2`), tapez le texte suivant :  
  
     **Événements :**  
  
 Dans les sections suivantes, vous allez écrire du code qui insère du texte dans `namedRange2` et modifie les propriétés de la `namedRange2` contrôle en réponse à la <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, et <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> événements de `namedRange1`.  
  
## <a name="adding-code-to-respond-to-the-beforedoubleclick-event"></a>Ajout d’un Code pour répondre à l’événement BeforeDoubleClick  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Pour insérer du texte dans NamedRange2 en fonction de l’événement BeforeDoubleClick  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **Sheet1.vb** ou **Sheet1.cs** et sélectionnez **afficher le Code**.  
  
2.  Ajoutez du code afin que la `namedRange1_BeforeDoubleClick` Gestionnaire d’événements ressemble à ce qui suit :  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  En c#, vous devez ajouter des gestionnaires d’événements pour la plage nommée comme indiqué dans le <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> événement ci-dessous. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="adding-code-to-respond-to-the-change-event"></a>Ajout d’un Code pour répondre à l’événement de modification  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Pour insérer du texte dans namedRange2 en fonction de l’événement de modification  
  
1.  Ajoutez du code afin que la `NamedRange1_Change` Gestionnaire d’événements ressemble à ce qui suit :  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Étant donné que le double-clic sur une cellule dans une plage Excel en mode édition, un <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> événement se produit lorsque la sélection est déplacée en dehors de la plage, même si aucune modification de texte s’est produite.  
  
## <a name="adding-code-to-respond-to-the-selectionchange-event"></a>Ajout de Code pour répondre à l’événement SelectionChange  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Pour insérer du texte dans namedRange2 selon l’événement SelectionChange  
  
1.  Ajoutez du code afin que la **NamedRange1_SelectionChange** Gestionnaire d’événements ressemble à ce qui suit :  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Étant donné que le double-clic sur une cellule dans une plage Excel entraîne la sélection se déplace dans la plage, un <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> événement se produit avant le <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> événement se produit.  
  
## <a name="testing-the-application"></a>Test de l'application  
 Maintenant vous pouvez tester votre classeur pour vérifier que le texte qui décrit les événements d’un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle est inséré dans une autre plage nommée lorsque les événements sont déclenchés.  
  
#### <a name="to-test-your-document"></a>Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Placez votre curseur dans `namedRange1`et vérifiez que le texte concernant la <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> événement est inséré et qu’un commentaire est inséré dans la feuille de calcul.  
  
3.  Double-cliquez sur à l’intérieur de `namedRange1`et vérifiez que le texte concernant <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> événements est inséré avec du texte en italique rouge dans `namedRange2`.  
  
4.  Cliquez en dehors de `namedRange1` et notez que l’événement de modification se produit lors de la sortie en mode édition, même si aucune modification au texte.  
  
5.  Modifiez le texte dans `namedRange1`.  
  
6.  Cliquez en dehors de `namedRange1`et vérifiez que le texte concernant <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> événement est inséré avec du texte bleu dans `namedRange2`.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas illustre les principes fondamentaux de la programmation des événements d’un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle. Voici une tâche susceptibles de venir :  
  
-   Déploiement du projet. Pour plus d’informations, consultez [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Comment : redimensionner les contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Guide pratique pour créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  