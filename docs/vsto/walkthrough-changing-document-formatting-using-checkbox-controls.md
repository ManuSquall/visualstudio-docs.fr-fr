---
title: Modifier la mise en forme d’un document à l’aide de contrôles CheckBox
description: Apprenez à utiliser les contrôles Windows Forms dans une personnalisation au niveau du document pour Microsoft Word afin de modifier la mise en forme du texte.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 931e9554a10e0e1525d9ee4a10505633b211610b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527248"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Procédure pas à pas : modifier la mise en forme d’un document à l’aide de contrôles CheckBox
  Cette procédure pas à pas montre comment utiliser des contrôles Windows Forms dans une personnalisation au niveau du document pour Microsoft Office Word afin de modifier la mise en forme du texte.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Ajout de texte et d’un contrôle au document dans un projet au niveau du document au moment du Design.

- Mise en forme du texte lorsqu’une option est sélectionnée.

  Pour voir le résultat sous forme d’exemple terminé, consultez l’exemple de contrôles Word dans les [exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Créer le projet
 La première étape consiste à créer un projet de document Word.

### <a name="create-a-new-project"></a>Créer un projet

1. Créez un projet de document Word portant le nom **My Word Formatting**. Dans l’Assistant, sélectionnez **créer un nouveau document**.

     Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le projet de **mise en forme My Word** à **Explorateur de solutions**.

## <a name="add-text-and-controls-to-the-word-document"></a>Ajouter du texte et des contrôles au document Word
 Pour cette procédure pas à pas, ajoutez trois cases à cocher et du texte dans un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle au document Word. Les cases à cocher présentent des options permettant à l’utilisateur de mettre en forme le texte.

### <a name="add-three-check-boxes"></a>Ajouter trois cases à cocher

1. Vérifiez que le document est ouvert dans le concepteur Visual Studio.

2. Dans l’onglet **contrôles communs** de la **boîte à outils**, faites glisser le premier <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> contrôle vers le document.

3. Dans la fenêtre **Propriétés** , changez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**applyBoldFont**|
    |**Text**|**Gras**|

4. Appuyez sur **entrée** pour déplacer le point d’insertion sous la première case à cocher.

5. Ajoutez une deuxième case à cocher au document sous la case `ApplyBoldFont` à cocher, puis modifiez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**applyItalicFont**|
    |**Text**|**Italique**|

6. Appuyez sur **entrée** pour déplacer le point d’insertion sous la deuxième case à cocher.

7. Ajoutez une troisième case à cocher au document sous la case `ApplyItalicFont` à cocher, puis modifiez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**applyUnderlineFont**|
    |**Text**|**Souligner**|

### <a name="add-text-and-a-bookmark-control"></a>Ajouter du texte et un contrôle Bookmark

1. Déplacez le point d’insertion sous les contrôles de case à cocher et tapez le texte suivant :

    **Cliquez sur une case à cocher pour modifier la mise en forme de ce texte.**

2. À partir de l’onglet **contrôles Word** de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle vers le document.

    La boîte de dialogue **Ajouter un contrôle de signet** s’affiche.

3. Sélectionnez le texte que vous avez ajouté au document, puis cliquez sur **OK**.

    Un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle nommé **bookmark1** est ajouté au texte sélectionné dans le document.

4. Dans la fenêtre **Propriétés** , remplacez la valeur de la propriété **(Name)** par **fontText.**

   Ensuite, écrivez le code pour mettre en forme le texte lorsqu’une case à cocher est activée ou désactivée.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Mettre en forme le texte lorsqu’une case à cocher est activée ou désactivée
 Lorsque l’utilisateur sélectionne une option de mise en forme, modifiez le format du texte dans le document.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Modifier la mise en forme lorsqu’une case à cocher est activée

1. Cliquez avec le bouton droit `ThisDocument` dans **Explorateur de solutions**, puis cliquez sur **afficher le code** dans le menu contextuel.

2. Pour C# uniquement, ajoutez les constantes suivantes à la classe **ThisDocument** .

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]

3. Ajoutez le code suivant au <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la case `applyBoldFont` à cocher.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]

4. Ajoutez le code suivant au <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la case `applyItalicFont` à cocher.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]

5. Ajoutez le code suivant au <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la case `applyUnderlineFont` à cocher.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]

6. En C#, vous devez ajouter des gestionnaires d’événements pour les zones de texte à l' <xref:Microsoft.Office.Tools.Word.Document.Startup> événement. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]

## <a name="test-the-application"></a>Test de l’application
 Vous pouvez maintenant tester votre document pour vérifier que le texte est mis en forme correctement lorsque vous activez ou désactivez une case à cocher.

### <a name="test-your-document"></a>Tester votre document

1. Appuyez sur **F5** pour exécuter votre projet.

2. Activer ou désactiver une case à cocher.

3. Confirmez que le texte est correctement mis en forme.

## <a name="next-steps"></a>Étapes suivantes
 Cette procédure pas à pas montre les concepts de base de l’utilisation de cases à cocher et la modification par programme de la mise en forme du texte dans les documents Word. Voici quelques tâches susceptibles de venir après :

- Utilisez un bouton pour remplir une zone de texte. Pour plus d’informations, consultez [procédure pas à pas : affichage de texte dans une zone de texte dans un document à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Utilisation de cases d'option pour sélectionner des styles de graphique. Pour plus d’informations, consultez [procédure pas à pas : mise à jour d’un graphique dans un document à l’aide de cases d’option](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Voir aussi
- [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)
- [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Limitations des contrôles de Windows Forms sur les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
