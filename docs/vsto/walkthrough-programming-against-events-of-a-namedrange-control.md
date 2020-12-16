---
title: 'Procédure pas à pas : programmer sur les événements d’un contrôle NamedRange'
description: Découvrez comment vous pouvez ajouter un contrôle NamedRange à une feuille de calcul Microsoft Excel et programmer par rapport à ses événements à l’aide des outils de développement Office dans Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e311a567d32ee083bcc13f417c248f5f3d3ee5a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526129"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Procédure pas à pas : programmer sur les événements d’un contrôle NamedRange
  Cette procédure pas à pas montre comment ajouter un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à une feuille de calcul Microsoft Office Excel et programmer par rapport à ses événements à l’aide des outils de développement Office dans Visual Studio.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Pendant cette procédure pas à pas, vous allez apprendre à :

- Ajoutez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à une feuille de calcul.

- Programmer des <xref:Microsoft.Office.Tools.Excel.NamedRange> événements de contrôle.

- Testez votre projet.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Créer le projet
 Dans cette étape, vous allez créer un projet de classeur Excel à l’aide de Visual Studio.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de classeur Excel avec le nom **mes événements de la plage nommée**. Assurez-vous que l’option **créer un nouveau document** est sélectionnée. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet **mes événements de la plage nommée** à **Explorateur de solutions**.

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Ajouter du texte et des plages nommées à la feuille de calcul
 Étant donné que les contrôles hôtes sont des objets Office étendus, vous pouvez les ajouter à votre document de la même manière que vous ajouteriez l’objet natif. Par exemple, vous pouvez ajouter un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle Excel à une feuille de calcul en ouvrant le menu **Insérer** , en pointant sur **nom**, puis en choisissant **définir**. Vous pouvez également ajouter un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle en le faisant glisser de la **boîte à outils** vers la feuille de calcul.

 Dans cette étape, vous allez ajouter deux contrôles de plage nommée à la feuille de calcul à l’aide de la **boîte à outils**, puis ajouter du texte à la feuille de calcul.

### <a name="to-add-a-range-to-your-worksheet"></a>Pour ajouter une plage à votre feuille de calcul

1. Vérifiez que le classeur *ma plage nommée Events.xlsx* est ouvert dans le concepteur Visual Studio, avec l' `Sheet1` affichage affiché.

2. À partir de l’onglet **contrôles Excel** de la boîte à outils, faites glisser un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle vers la cellule **a1** dans `Sheet1` .

     La boîte de dialogue **Ajouter un contrôle NamedRange** s’affiche.

3. Vérifiez que **$A $1** apparaît dans la zone de texte modifiable et que la cellule **a1** est sélectionnée. Si ce n’est pas le cas, cliquez sur la cellule **a1** pour la sélectionner.

4. Cliquez sur **OK**.

     La cellule **a1** devient une plage nommée `namedRange1` . Il n’existe aucune indication visible sur la feuille de calcul, mais elle `namedRange1` apparaît dans la zone **nom** (située juste au-dessus de la feuille de calcul sur le côté gauche) lorsque la cellule **a1** est sélectionnée.

5. Ajoutez un autre <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à la cellule **B3**.

6. Vérifiez que **$B $3** apparaît dans la zone de texte modifiable et que la cellule **B3** est sélectionnée. Si ce n’est pas le cas, cliquez sur la cellule **B3** pour la sélectionner.

7. Cliquez sur **OK**.

     La cellule **B3** devient une plage nommée `namedRange2` .

### <a name="to-add-text-to-your-worksheet"></a>Pour ajouter du texte à une feuille de calcul

1. Dans la cellule **a1**, tapez le texte suivant :

    **Il s’agit d’un exemple de contrôle NamedRange.**

2. Dans la cellule **a3** (à gauche de `namedRange2` ), tapez le texte suivant :

    **Événements**

   Dans les sections suivantes, vous allez écrire du code qui insère du texte dans `namedRange2` et modifie les propriétés du `namedRange2` contrôle en réponse aux <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> événements, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> et <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> de `namedRange1` .

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Ajouter du code pour répondre à l’événement BeforeDoubleClick

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Pour insérer du texte dans NamedRange2 en fonction de l’événement BeforeDoubleClick

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Feuil1. vb** ou **Sheet1.cs** , puis sélectionnez **afficher le code**.

2. Ajoutez du code pour que le `namedRange1_BeforeDoubleClick` Gestionnaire d’événements ressemble à ce qui suit :

     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]

3. En C#, vous devez ajouter des gestionnaires d’événements pour la plage nommée, comme indiqué dans l' <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> événement ci-dessous. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]

## <a name="add-code-to-respond-to-the-change-event"></a>Ajouter du code pour répondre à l’événement de modification

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Pour insérer du texte dans namedRange2 en fonction de l’événement de modification

1. Ajoutez du code pour que le `NamedRange1_Change` Gestionnaire d’événements ressemble à ce qui suit :

     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]

    > [!NOTE]
    > Étant donné que le fait de double-cliquer sur une cellule dans une plage Excel passe en mode édition, un <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> événement se produit lorsque la sélection est déplacée en dehors de la plage, même si aucune modification de texte n’a eu lieu.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Ajouter du code pour répondre à l’événement SelectionChange

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Pour insérer du texte dans namedRange2 en fonction de l’événement SelectionChange

1. Ajoutez du code pour que le gestionnaire d’événements **NamedRange1_SelectionChange** ressemble à ce qui suit :

     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]

    > [!NOTE]
    > Étant donné que le fait de double-cliquer sur une cellule dans une plage Excel provoque le déplacement de la sélection dans la plage, un <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> événement se produit avant que l' <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> événement se produise.

## <a name="test-the-application"></a>Test de l’application
 Vous pouvez maintenant tester votre classeur pour vérifier que le texte décrivant les événements d’un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle est inséré dans une autre plage nommée lorsque les événements sont déclenchés.

### <a name="to-test-your-document"></a>Pour tester votre document

1. Appuyez sur **F5** pour exécuter votre projet.

2. Placez votre curseur dans `namedRange1` et vérifiez que le texte relatif à l' <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> événement est inséré et qu’un commentaire est inséré dans la feuille de calcul.

3. Double-cliquez dans `namedRange1` et vérifiez que le texte relatif aux <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> événements est inséré avec du texte en italique rouge dans `namedRange2` .

4. Cliquez en dehors de `namedRange1` et notez que l’événement de modification se produit lorsque vous quittez le mode édition, même si aucune modification n’a été apportée au texte.

5. Modifiez le texte dans `namedRange1` .

6. Cliquez en dehors de `namedRange1` , puis vérifiez que le texte relatif <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> à l’événement est inséré avec du texte en bleu dans `namedRange2` .

## <a name="next-steps"></a>Étapes suivantes
 Cette procédure pas à pas montre les concepts de base de la programmation par rapport aux événements d’un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle. Voici une tâche qui peut s’avérer suivante :

- Déploiement du projet. Pour plus d’informations, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Comment : redimensionner des contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
