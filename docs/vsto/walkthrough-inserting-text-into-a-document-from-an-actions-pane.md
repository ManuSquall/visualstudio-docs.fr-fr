---
title: 'Procédure pas à pas : insertion de texte dans un document à partir d’un volet Actions'
description: Créez un volet actions dans un document Microsoft Word. Découvrez que le volet Actions contient deux contrôles qui collectent les entrées, puis envoient le texte au document.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1ac42954e32b30a293abbe031218213948fb103a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824976"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Procédure pas à pas : insertion de texte dans un document à partir d’un volet Actions
  Cette procédure pas à pas montre comment créer un volet actions dans un document Word Microsoft Office. Le volet Actions contient deux contrôles qui collectent l’entrée, puis envoient le texte au document.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Concevoir une interface à l’aide de Windows Forms contrôles sur un contrôle de volet Actions.

- Affichez le volet actions lorsque l’application s’ouvre.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Créer le projet
 La première étape consiste à créer un projet de document Word.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de document Word avec le nom **My Basic Actions Pane**. Dans l’Assistant, sélectionnez **créer un nouveau document**. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le projet **mon volet actions de base** à **Explorateur de solutions**.

## <a name="add-text-and-bookmarks-to-the-document"></a>Ajouter du texte et des signets au document
 Le volet Actions enverra du texte à des signets dans le document. Pour concevoir le document, tapez du texte pour créer un formulaire de base.

### <a name="to-add-text-to-your-document"></a>Pour ajouter du texte à votre document

1. Tapez le texte suivant dans votre document Word :

    **Le 21 mars, 2008**

    **Nom**

    **Adresse**

    **Il s’agit d’un exemple de volet actions de base dans Word.**

   Vous pouvez ajouter un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle à votre document en le faisant glisser à partir de la boîte **à outils** dans Visual Studio ou en utilisant la boîte de dialogue **signet** dans Word.

### <a name="to-add-a-bookmark-control-to-your-document"></a>Pour ajouter un contrôle Bookmark à votre document

1. À partir de l’onglet **contrôles Word** de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle vers votre document.

     La boîte de dialogue **Ajouter un contrôle de signet** s’affiche.

2. Sélectionnez le mot **nom**, sans sélectionner la marque de paragraphe, puis cliquez sur **OK**.

    > [!NOTE]
    > La marque de paragraphe doit être en dehors du signet. Si les marques de paragraphe ne sont pas visibles dans le document, cliquez sur le menu **Outils** , pointez sur **Microsoft Office outils Word** , puis cliquez sur **options**. Cliquez sur l’onglet **affichage** , puis activez la case à cocher **marques de paragraphe** dans la section **marques de mise en forme** de la boîte de dialogue **options** .

3. Dans la fenêtre **Propriétés** , remplacez la propriété **Name** de **bookmark1** par **ShowName**.

4. Sélectionnez l' **adresse** du mot, sans sélectionner la marque de paragraphe.

5. Sous l’onglet **Insérer** du ruban, dans le groupe **liens** , cliquez sur **signet**.

6. Dans la boîte de dialogue **signet** , tapez **showAddress** dans la zone **nom du signet** , puis cliquez sur **Ajouter**.

## <a name="add-controls-to-the-actions-pane"></a>Ajouter des contrôles au volet Actions
 Pour concevoir l’interface du volet Actions, ajoutez un contrôle de volet actions au projet, puis ajoutez des contrôles de Windows Forms au contrôle de volet Actions.

### <a name="to-add-an-actions-pane-control"></a>Pour ajouter un contrôle de volet Actions

1. Sélectionnez le projet **mon volet actions de base** dans **Explorateur de solutions**.

2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** , cliquez sur **contrôle du volet Actions**, nommez le contrôle **InsertTextControl,** puis cliquez sur **Ajouter**.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Pour ajouter des contrôles Windows Forms au contrôle de volet Actions

1. Si le contrôle de volet Actions n’est pas visible dans le concepteur, double-cliquez sur **InsertTextControl**.

2. Dans l’onglet **contrôles communs** de la **boîte à outils**, faites glisser un contrôle **label** vers le contrôle de volet Actions.

3. Remplacez la propriété **Text** du contrôle Label par **Name**.

4. Ajoutez un contrôle **TextBox** au contrôle de volet Actions, puis modifiez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**getName**|
    |**Taille**|**130, 20**|

5. Ajoutez un deuxième contrôle **label** au contrôle de volet Actions, puis remplacez la propriété **Text** par **Address**.

6. Ajoutez un deuxième contrôle **TextBox** au contrôle de volet Actions, puis modifiez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**getAddress**|
    |**Accepte les retours**|**True**|
    |**Lambda**|**True**|
    |**Taille**|**130, 40**|

7. Ajoutez un contrôle **bouton** au contrôle de volet Actions, puis modifiez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**addText**|
    |**Text**|**Insérer**|

## <a name="add-code-to-insert-text-into-the-document"></a>Ajouter du code pour insérer du texte dans le document
 Dans le volet Actions, écrivez le code qui insère le texte des zones de texte dans les <xref:Microsoft.Office.Tools.Word.Bookmark> contrôles appropriés dans le document. Vous pouvez utiliser la `Globals` classe pour accéder aux contrôles du document à partir des contrôles du volet Actions. Pour plus d’informations, consultez [accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Pour insérer du texte à partir du volet actions dans un signet dans le document

1. Ajoutez le code suivant au <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements du bouton **AddText** .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb" id="Snippet8":::

2. En C#, vous devez ajouter un gestionnaire d’événements pour le clic sur le bouton. Vous pouvez placer ce code dans le `InsertTextControl` constructeur après l’appel à `InitializeComponent` . Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet9":::

## <a name="add-code-to-show-the-actions-pane"></a>Ajouter du code pour afficher le volet Actions
 Pour afficher le volet Actions, ajoutez le contrôle que vous avez créé à la collection de contrôles.

### <a name="to-show-the-actions-pane"></a>Pour afficher le volet Actions

1. Créez une nouvelle instance du contrôle de volet actions dans la `ThisDocument` classe.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet10":::

2. Ajoutez le code suivant au <xref:Microsoft.Office.Tools.Word.Document.Startup> Gestionnaire d’événements de `ThisDocument` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet11":::

## <a name="test-the-application"></a>Tester l’application
 Testez votre document pour vérifier que le volet actions s’ouvre lorsque le document est ouvert et que le texte tapé dans les zones de texte est inséré dans les signets lorsque l’utilisateur clique sur le bouton.

### <a name="to-test-your-document"></a>Pour tester votre document

1. Appuyez sur **F5** pour exécuter votre projet.

2. Vérifiez que le volet actions est visible.

3. Tapez votre nom et votre adresse dans les zones de texte du volet Actions, puis cliquez sur **Insérer**.

## <a name="next-steps"></a>Étapes suivantes
 Voici quelques tâches susceptibles de venir après :

- Créez un volet actions dans Excel. Pour plus d’informations, consultez [Comment : ajouter un volet actions à des classeurs Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).

- Lier des données à des contrôles dans un volet Actions. Pour plus d’informations, consultez [procédure pas à pas : liaison de données à des contrôles dans un volet Actions Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)
- [Comment : ajouter un volet actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Comment : ajouter un volet actions à des classeurs Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Comment : gérer la disposition des contrôles dans les volets actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Bookmark, contrôle](../vsto/bookmark-control.md)
