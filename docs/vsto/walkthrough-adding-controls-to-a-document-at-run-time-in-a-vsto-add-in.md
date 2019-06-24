---
title: Ajouter des contrôles au document lors de l’exécution dans le complément VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6ac01f32a14589837d0cb7707cb3d2f8946bd0a
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328398"
---
# <a name="walkthrough-add-controls-to-a-document-at-runtime-in-a-vsto-add-in"></a>Procédure pas à pas : Ajouter des contrôles à un document lors de l’exécution dans un complément, VSTO
  Vous pouvez ajouter des contrôles à un document Microsoft Office Word ouvert en utilisant un complément, VSTO. Cette procédure pas à pas montre comment utiliser le ruban pour permettre aux utilisateurs d’ajouter un <xref:Microsoft.Office.Tools.Word.Controls.Button> ou un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> à un document.

 **S’applique à :** Les informations contenues dans cette rubrique s’appliquent aux projets de complément VSTO pour Word 2010. Pour plus d’informations, consultez [Fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un projet de complément VSTO Word.

- Mise à disposition d’une interface utilisateur permettant d’ajouter des contrôles au document.

- Ajout de contrôles au document lors de l’exécution.

- Suppression de contrôles dans le document.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-word-add-in-project"></a>Créer un nouveau projet de complément Word
 Commencez par créer un projet de complément VSTO Word.

### <a name="to-create-a-new-word-vsto-add-in-project"></a>Pour créer un projet de complément VSTO Word

1. Créer un projet de complément VSTO pour Word portant le nom **WordDynamicControls**. Pour plus d'informations, voir [Procédure : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Ajoutez une référence à l’assembly **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** . Cette référence est obligatoire pour ajouter par programmation un contrôle Windows Forms au document, plus loin dans cette procédure pas à pas.

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>Fournir une interface utilisateur pour ajouter des contrôles à un document
 Ajoutez un onglet personnalisé au ruban dans Word. Les utilisateurs peuvent cocher des cases sous l’onglet pour ajouter des contrôles à un document.

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Pour fournir une interface utilisateur permettant d’ajouter des contrôles à un document

1. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Ruban (Concepteur visuel)** .

3. Remplacez le nom du nouveau ruban par **MyRibbon**, puis cliquez sur **Ajouter**.

    Le fichier **MyRibbon.cs** ou **MyRibbon.vb** s'ouvre dans le Concepteur de ruban et affiche un onglet et un groupe par défaut.

4. Dans le Concepteur de ruban, cliquez sur le groupe **group1** .

5. Dans la fenêtre **Propriétés** , affectez **Ajouter des contrôles** comme propriété **Étiquette** de **group1**.

6. Sous l’onglet **Contrôles de ruban Office** de la **Boîte à outils**, faites glisser un contrôle **CheckBox** sur **group1**.

7. Cliquez sur **CheckBox1** pour le sélectionner.

8. Dans la fenêtre **Propriétés** , changez les propriétés suivantes.

   | Propriété | Value |
   |-----------|-----------------------|
   | **Name** | **addButtonCheckBox** |
   | **Ajouter des contrôles** | **Bouton Ajouter** |

9. Ajoutez une deuxième case à cocher pour **group1**, puis modifiez les propriétés suivantes.

   | Propriété | Value |
   |-----------|---------------------------|
   | **Name** | **addRichTextCheckBox** |
   | **Label** | **Ajouter un contrôle de texte enrichi** |

10. Dans le Concepteur de ruban, double-cliquez sur **Bouton Ajouter**.

     Le gestionnaire d’événements <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> de la case à cocher **Bouton Ajouter** s’ouvre dans l’éditeur de code.

11. Revenez au Concepteur de ruban et double-cliquez sur **Ajouter un contrôle de texte enrichi**.

     Le gestionnaire d’événements <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> de la case à cocher **Ajouter un contrôle de texte enrichi** s’ouvre dans l’éditeur de code.

    Plus loin dans cette procédure pas à pas, vous ajouterez du code à ces gestionnaires d’événements pour ajouter et supprimer des contrôles dans le document actif.

## <a name="add-and-remove-controls-on-the-active-document"></a>Ajouter et supprimer des contrôles dans le document actif
 Dans le code de complément VSTO, vous devez convertir le document actif en <xref:Microsoft.Office.Tools.Word.Document>*T:Microsoft.Office.Tools.Word.Document* avant de pouvoir ajouter un contrôle. Dans les solutions Office, vous ne pouvez ajouter des contrôles managés qu’à des éléments hôtes, qui agissent comme des conteneurs pour les contrôles. Dans les projets de complément VSTO, éléments hôtes peuvent être créés au moment de l’exécution à l’aide de la `GetVstoObject` (méthode).

 Ajoutez des méthodes à la classe `ThisAddIn` qui peut être appelée pour ajouter ou supprimer un <xref:Microsoft.Office.Tools.Word.Controls.Button> ou <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dans le document actif. Plus loin dans cette procédure, vous appellerez ces méthodes à partir des gestionnaires d’événements <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> des cases à cocher dans le ruban.

### <a name="to-add-and-remove-controls-on-the-active-document"></a>Pour ajouter et supprimer des contrôles dans le document actif

1. Dans **l’Explorateur de solutions**, double-cliquez sur *ThisAddIn.cs* ou *ThisAddIn.vb* pour ouvrir le fichier dans l’éditeur de Code.

2. Ajoutez le code suivant à la classe `ThisAddIn` . Ce code déclare des objets <xref:Microsoft.Office.Tools.Word.Controls.Button> et <xref:Microsoft.Office.Tools.Word.RichTextContentControl> qui représentent les contrôles qui seront ajoutés au document.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]

3. Ajoutez la méthode suivante à la classe `ThisAddIn` . Quand l’utilisateur clique sur la case à cocher **Bouton Ajouter** dans le ruban, cette méthode ajoute un <xref:Microsoft.Office.Tools.Word.Controls.Button> à la sélection actuelle dans le document si la case est cochée, ou supprime le <xref:Microsoft.Office.Tools.Word.Controls.Button> si la case est décochée.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]

4. Ajoutez la méthode suivante à la classe `ThisAddIn` . Quand l’utilisateur clique sur la case à cocher **Ajouter un contrôle de texte enrichi** dans le ruban, cette méthode ajoute un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> à la sélection actuelle dans le document si la case est cochée, ou supprime le <xref:Microsoft.Office.Tools.Word.RichTextContentControl> si la case est décochée.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]

## <a name="remove-the-button-control-when-the-document-is-saved"></a>Supprimer le contrôle Button lorsque le document est enregistré.
 Les contrôles Windows Forms ne sont pas conservés lorsque le document est enregistré puis fermé. Toutefois, un wrapper ActiveX pour chaque contrôle reste dans le document, et la bordure de ce wrapper est visible par les utilisateurs finaux quand le document est rouvert. Il existe plusieurs façons de nettoyer des contrôles Windows Forms créés de manière dynamique dans des compléments VSTO. Lors de cette procédure pas à pas, vous allez supprimer par programmation le contrôle <xref:Microsoft.Office.Tools.Word.Controls.Button> quand le document est enregistré.

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Pour supprimer le contrôle Button quand le document est enregistré

1. Dans le *ThisAddIn.cs* ou *ThisAddIn.vb* fichier de code, ajoutez la méthode suivante à la `ThisAddIn` classe. Cette méthode est un gestionnaire d’événements pour l’événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> . Si le document enregistré a un élément hôte <xref:Microsoft.Office.Tools.Word.Document> qui lui est associé, le gestionnaire d’événements obtient l’élément hôte et supprime le contrôle <xref:Microsoft.Office.Tools.Word.Controls.Button> , s’il existe.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]

2. En C#, ajoutez le code suivant au gestionnaire d’événements `ThisAddIn_Startup` . Ce code est nécessaire en C# pour connecter le gestionnaire d’événements `Application_DocumentBeforeSave` à l’événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> .

     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Ajouter et supprimer des contrôles lorsque l’utilisateur clique sur les cases à cocher du ruban
 Enfin, modifiez le <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> gestionnaires d’événements des cases à cocher que vous avez ajouté au ruban pour ajouter ou supprimer des contrôles dans le document.

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Pour ajouter ou supprimer des contrôles lorsque l’utilisateur clique sur les cases à cocher du ruban

1. Dans le *MyRibbon.cs* ou *MyRibbon.vb* fichier de code, remplacez le texte généré `addButtonCheckBox_Click` et `addRichTextCheckBox_Click` gestionnaires d’événements par le code suivant. Ce code redéfinit ces gestionnaires d’événements pour appeler les méthodes `ToggleButtonOnDocument` et `ToggleRichTextControlOnDocument` que vous avez ajoutées à la classe `ThisAddIn` plus tôt lors de cette procédure pas à pas.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]

## <a name="test-the-solution"></a>Tester la solution
 Ajoutez des contrôles à un document en les sélectionnant à partir de l’onglet personnalisé dans le ruban. Quand vous enregistrez le document, le contrôle <xref:Microsoft.Office.Tools.Word.Controls.Button> est supprimé.

### <a name="to-test-the-solution"></a>Pour tester la solution.

1. Appuyez sur **F5** pour exécuter votre projet.

2. Dans le document actif, appuyez sur **entrée** plusieurs fois pour ajouter de nouveaux vide paragraphes au document.

3. Sélectionnez le premier paragraphe.

4. Cliquez sur l'onglet **Compléments** .

5. Dans le groupe **Ajouter des contrôles** , cliquez sur **Bouton Ajouter**.

     Un bouton apparaît dans le premier paragraphe.

6. Sélectionnez le dernier paragraphe.

7. Dans le groupe **Ajouter des contrôles** , cliquez sur **Ajouter un contrôle de texte enrichi**.

     Un contrôle de contenu de texte enrichi est ajouté au dernier paragraphe.

8. Enregistrez le document.

     Le bouton est supprimé du document.

## <a name="next-steps"></a>Étapes suivantes
 Pour en savoir plus sur les contrôles dans les compléments VSTO, consultez les rubriques suivantes :

- Pour obtenir un exemple qui montre comment ajouter de nombreux autres types de contrôles à un document lors de l’exécution et recréer les contrôles lorsque le document est rouvert, consultez l’exemple de contrôles dynamiques de complément Word à [exemples de développement Office et des procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).

- Pour une procédure pas à pas qui montre comment ajouter des contrôles à une feuille de calcul en utilisant un complément, VSTO pour Excel, consultez [procédure pas à pas : Ajouter des contrôles à une feuille de calcul lors de l’exécution dans un projet de complément VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).

## <a name="see-also"></a>Voir aussi
- [Solutions Word](../vsto/word-solutions.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Conserver les contrôles dynamiques dans les documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Guide pratique pour Ajouter des contrôles Windows Forms aux documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Guide pratique pour Ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Étendre des documents Word et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
