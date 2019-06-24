---
title: Texte affiché dans la zone de texte dans le document à l’aide du bouton
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f3c467abcee8fb4faafd2da06ba261e7f3039fe
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328750"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Procédure pas à pas : Texte affiché dans une zone de texte dans un document à l’aide d’un bouton
  Cette procédure pas à pas montre comment utiliser les boutons et les zones de texte dans une personnalisation au niveau du document pour Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Ajout de contrôles au document Word d'un projet de niveau document au moment du design.

- Remplissage d'une zone de texte lorsqu'un clic est effectué.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Créer le projet
 La première étape consiste à créer un projet de document Word.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créer un projet de Document Word portant le nom **mon bouton Word**. Dans l’Assistant, sélectionnez **créer un nouveau document**.

     Pour plus d'informations, voir [Procédure : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le **mon bouton Word** projet **l’Explorateur de solutions**.

## <a name="add-controls-to-the-word-document"></a>Ajouter des contrôles au document Word
 Les contrôles d'interface utilisateur se composent d'un bouton et une zone de texte dans le document Word.

### <a name="to-add-a-button-and-a-text-box"></a>Pour ajouter un bouton et une zone de texte

1. Vérifiez que le document est ouvert dans le concepteur Visual Studio.

2. À partir de la **contrôles communs** onglet de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Word.Controls.TextBox> contrôle au document.

   > [!NOTE]
   > Dans Word, les contrôles sont déposés en ligne avec le texte par défaut. Vous pouvez modifier les façon dont les contrôles et objets de forme sont insérés en modifiant la valeur par défaut sur le **modifier** onglet de la **Options** boîte de dialogue dans Word.

3. Dans le menu **Affichage** , cliquez sur **Fenêtre Propriétés**.

4. Rechercher **TextBox1** dans le **propriétés** zone de liste déroulante de fenêtre et de modifier le **nom** propriété de la zone de texte **displayText**.

5. Faites glisser un **bouton** contrôler au document et modifiez les propriétés suivantes.

   |Propriété|Value|
   |--------------|-----------|
   |**Name**|**insertText**|
   |**Text**|**Insérer du texte**|

   Vous pouvez maintenant écrire le code qui s'exécute lors d'un clic sur le bouton.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Remplir la zone de texte lorsque le bouton est activé.
 Chaque fois que l’utilisateur clique sur le bouton, **Hello World !** est ajouté à la zone de texte.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Pour écrire dans la zone de texte lorsqu'un clic est effectué

1. Dans **l’Explorateur de solutions**, avec le bouton droit **ThisDocument**, puis cliquez sur **afficher le Code** dans le menu contextuel.

2. Ajoutez le code suivant au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du bouton :

     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]

3. En C#, vous devez ajouter un gestionnaire d'événements du bouton à l'événement <xref:Microsoft.Office.Tools.Word.Document.Startup>. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : Créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]

## <a name="test-the-application"></a>Tester l’application
 Vous pouvez maintenant tester votre document pour vous assurer que le message **Hello World !** s’affiche dans la zone de texte lorsque vous cliquez sur le bouton.

### <a name="to-test-your-document"></a>Pour tester votre document

1. Appuyez sur **F5** pour exécuter votre projet.

2. Cliquez sur le bouton.

3. Vérifiez que **Hello World !** s’affiche dans la zone de texte.

## <a name="next-steps"></a>Étapes suivantes
 Cette procédure pas à pas présente les notions de base de l'utilisation des boutons et des zones de texte dans les documents Word. Voici quelques tâches susceptibles de venir après :

- Utilisation d'une zone de liste déroulante pour modifier la mise en forme. Pour plus d’informations, consultez [Procédure pas à pas : Modifier le format de document à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

- Utilisation de cases d'option pour sélectionner des styles de graphique. Pour plus d’informations, consultez [Procédure pas à pas : Mettre à jour d’un graphique dans un document à l’aide de cases d’option](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Voir aussi
- [Contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)
- [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)
- [Guide pratique pour Ajouter des contrôles Windows Forms aux documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
