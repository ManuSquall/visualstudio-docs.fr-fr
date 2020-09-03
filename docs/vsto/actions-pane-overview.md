---
title: Vue d’ensemble du volet Actions
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 82bf3ac9515effaa1053a011085849f0afea67f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986314"
---
# <a name="actions-pane-overview"></a>Vue d’ensemble du volet Actions
  Un volet actions est un volet de tâches **actions de document** personnalisable qui est associé à un document Word Microsoft Office spécifique ou Microsoft Office classeur Excel. Le volet actions est hébergé dans le volet Office, ainsi que d’autres volets de tâches intégrés, tels que le volet Office **source XML** dans Excel ou le volet de tâches **styles et mise en forme** dans Word. Vous pouvez utiliser des contrôles Windows Forms ou WPF pour concevoir l'interface utilisateur du volet Actions.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Vous pouvez créer un volet Actions uniquement dans une personnalisation au niveau du document pour Word ou Excel. Vous ne pouvez pas créer un volet Actions dans un complément VSTO. Pour plus d’informations, consultez [fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Le volet Actions diffère des volets de tâches personnalisés. Les volets de tâches personnalisés sont associés à l’application, pas à un document spécifique. Vous pouvez créer des volets de tâches personnalisés dans les compléments VSTO pour certaines applications Microsoft Office. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).

## <a name="display-the-actions-pane"></a>Afficher le volet Actions
 Le volet Actions est représenté par la classe <xref:Microsoft.Office.Tools.ActionsPane>. Lorsque vous créez un projet au niveau du document, une instance de cette classe est disponible pour votre code à l'aide du champ `ActionsPane` de la classe `ThisWorkbook` (pour Excel) ou `ThisDocument` (pour Word) de votre projet. Pour afficher le volet Actions, ajoutez un contrôle Windows Forms à la propriété <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> du champ `ActionsPane`. L'exemple de code suivant ajoute un contrôle nommé `actions` au volet Actions.

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

 Le volet Actions devient visible au moment de l'exécution, dès que vous lui ajoutez explicitement un contrôle. Une fois que le volet Actions est affiché, vous pouvez dynamiquement ajouter ou supprimer des contrôles en réponse aux actions de l'utilisateur. En général, vous ajoutez le code pour afficher le volet Actions du gestionnaire d'événements `Startup` de `ThisDocument` ou `ThisWorkbook` afin que le volet Actions soit visible lorsque l'utilisateur ouvre le document pour la première fois. Toutefois, vous souhaiterez peut-être afficher le volet Actions uniquement en réponse à l'action d'un utilisateur dans le document. Par exemple, vous pouvez ajouter le code à l'événement `Click` d'un contrôle sur le document.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Ajouter plusieurs contrôles au volet Actions
 Quand vous ajoutez plusieurs contrôles au volet Actions, vous devez regrouper les contrôles dans un contrôle utilisateur, puis ajouter le contrôle utilisateur à la <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propriété. Ce processus comprend les étapes suivantes :

1. Créez l’interface utilisateur du volet actions en ajoutant un élément de contrôle de **volet Actions** ou un élément de **contrôle utilisateur** à votre projet. Ces deux éléments incluent une classe <xref:System.Windows.Forms.UserControl> Windows Forms personnalisée. Les éléments de contrôle de **volet Actions** et de **contrôle utilisateur** sont équivalents ; la seule différence est son nom.

2. Ajouter des contrôles Windows Forms au <xref:System.Windows.Forms.UserControl> à l'aide du concepteur ou en écrivant du code.

   > [!NOTE]
   > Vous pouvez aussi ajouter des contrôles WPF au volet Actions en ajoutant un <xref:System.Windows.Controls.UserControl> WPF au <xref:System.Windows.Forms.UserControl> Windows Forms. Pour plus d’informations, consultez [utiliser des contrôles WPF dans les solutions Office](../vsto/using-wpf-controls-in-office-solutions.md).

3. Ajouter une instance du contrôle utilisateur personnalisé aux contrôles contenus dans le champ `ActionsPane` de la classe `ThisWorkbook` (pour Excel) ou `ThisDocument` (pour Word) de votre projet.

   Pour obtenir des exemples qui illustrent ce processus plus en détail, consultez [Comment : ajouter un volet actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

## <a name="hide-the-actions-pane"></a>Masquer le volet Actions
 Bien que la classe <xref:Microsoft.Office.Tools.ActionsPane> ait une méthode <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> et une propriété <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>, vous ne pouvez pas supprimer le volet Actions à partir de l'interface utilisateur à l'aide des membres de la classe <xref:Microsoft.Office.Tools.ActionsPane> elle-même. L’appel de la <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> méthode ou la définition <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> de la propriété sur **false** masque uniquement les contrôles du volet Actions ; il ne masque pas le volet de tâches.

 Pour masquer le volet de tâches dans votre solution, vous disposez de plusieurs options :

- Pour Word, affectez la valeur <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> <xref:Microsoft.Office.Interop.Word.TaskPane> **false**à la propriété de l’objet qui représente le volet de tâches actions de document. L'exemple de code suivant est destiné à être exécuté à partir de la classe `ThisDocument` de votre projet.

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]

- Pour Excel, affectez la valeur <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> **false**à la propriété de l’objet. L'exemple de code suivant est destiné à être exécuté à partir de la classe `ThisWorkbook` de votre projet.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]

- Pour Word ou Excel, vous pouvez également définir la <xref:Microsoft.Office.Core.CommandBar.Visible%2A> propriété de la barre de commandes qui représente le volet de tâches sur **false**. L'exemple de code suivant est destiné à être exécuté à partir de la classe `ThisDocument` ou `ThisWorkbook` de votre projet.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Effacer le volet actions lorsque le document est ouvert
 Quand un utilisateur enregistre le document alors que le volet actions est visible, le volet actions est visible à chaque fois que le document est ouvert, que le volet Actions contienne ou non des contrôles. Si vous souhaitez contrôler à quel moment il apparaît, appelez la méthode <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> du champ `ActionsPane` du gestionnaire d'événements `Startup``ThisDocument` ou `ThisWorkbook` pour vous assurer que le volet Actions n'est pas visible lorsque le document est ouvert.

### <a name="determine-when-the-actions-pane-is-closed"></a>Déterminer à quel moment le volet actions est fermé
 Il n'y a aucun événement déclenché lorsque le volet Actions est fermé. Bien que la <xref:Microsoft.Office.Tools.ActionsPane> classe ait un événement <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>, celui-ci n'est pas déclenché lorsque l'utilisateur final ferme le volet Actions. Au lieu de cela, cet événement est déclenché lorsque les contrôles du volet actions sont masqués en appelant la <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> méthode ou en affectant <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> à la propriété la **valeur false**.

 Lorsque l’utilisateur ferme le volet Actions, il peut l’afficher à nouveau en effectuant l’une des procédures suivantes dans l’interface utilisateur (IU) de l’application.

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Pour afficher le volet Actions à l'aide de l'interface utilisateur de Word ou Excel

1. Dans le ruban, cliquez sur l’onglet **affichage** .

2. Dans le groupe **Afficher/masquer** , cliquez sur le bouton bascule **actions de document** .

## <a name="program-actions-pane-events"></a>Événements du volet Actions du programme
 Vous pouvez ajouter plusieurs contrôles utilisateur au volet Actions, puis écrire le code pour répondre aux événements sur le document en affichant et en masquant les contrôles utilisateur. Si vous mappez des éléments du schéma XML à votre document, vous pouvez afficher certains contrôles utilisateur dans le volet Actions chaque fois que le point d'insertion se trouve dans l'un des éléments XML. Pour plus d’informations, consultez [Comment : mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) et [Comment : mapper des schémas à des feuilles de calcul dans Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).

 Vous pouvez également écrire le code pour répondre aux événements de n'importe quel objet, y compris les événements de contrôle hôte, d'application ou de document. Pour plus d’informations, consultez [procédure pas à pas : programmer sur les événements d’un contrôle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Lier des données à des contrôles dans le volet Actions
 Les contrôles du volet Actions ont les mêmes fonctionnalités de liaison de données que les contrôles Windows Forms. Vous pouvez lier les contrôles aux sources de données telles que les jeux de données, les groupes de données typées et XML. Pour plus d’informations, consultez [liaison de données et Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 Vous pouvez lier des contrôles du volet Actions et des contrôles du document au même jeu de données. Par exemple, vous pouvez créer une relation maître/détail entre les contrôles du volet Actions et les contrôles de la feuille de calcul. Pour plus d’informations, consultez [procédure pas à pas : liaison de données à des contrôles dans un volet Actions Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

## <a name="validate-data-in-actions-pane-controls"></a>Valider les données dans les contrôles du volet Actions
 Si vous affichez un message dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.Validating> d'un contrôle du volet Actions, l'événement peut être déclenché une deuxième fois lorsque le focus se déplace du contrôle au message. Pour éviter ce problème, utilisez un contrôle <xref:System.Windows.Forms.ErrorProvider> pour afficher les messages d’erreur de validation.

## <a name="user-control-stacking-order"></a>Ordre d’empilement des contrôles utilisateur
 Si vous utilisez plusieurs contrôles utilisateur, vous pouvez écrire le code pour empiler correctement les contrôles utilisateur du volet Actions, qu'il soit ancré verticalement ou horizontalement. Vous pouvez définir l'ordre d'empilement des contrôles utilisateur du volet Actions à l'aide de l'énumération <xref:Microsoft.Office.Tools.StackStyle> de la propriété <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>. Pour plus d’informations, consultez [Comment : gérer la disposition des contrôles dans les volets actions](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 La propriété <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> peut accepter les valeurs d'énumération <xref:Microsoft.Office.Tools.StackStyle> suivantes.

|Style d'empilement|Définition|
|--------------------|----------------|
|FromBottom|Empilez à partir du bas du volet Actions.|
|FromLeft|Empilez à partir de la gauche du volet Actions.|
|FromRight|Empilez à partir de la droite du volet Actions.|
|FromTop|Empilez à partir du haut du volet Actions.|
|None|Aucun ordre d'empilement défini ; l'ordre est contrôlé par le développeur.|

 Le code suivant définit la propriété <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> de façon à empiler les contrôles utilisateur à partir du haut du volet Actions.

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]

## <a name="anchor-controls"></a>Contrôles d’ancrage
 Si l'utilisateur redimensionne le volet Actions au moment de l'exécution, les contrôles peuvent être redimensionnés avec le volet Actions. Vous pouvez utiliser la propriété <xref:System.Windows.Forms.Control.Anchor%2A> d'un contrôle Windows Forms pour ancrer des contrôles au volet Actions. Vous pouvez également ancrer les contrôles Windows Forms au contrôle utilisateur de la même manière. Pour plus d’informations, consultez [Comment : ancrer des contrôles sur Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

## <a name="resize-the-actions-pane"></a>Redimensionner le volet Actions
 Vous ne pouvez pas modifier directement la taille d’un <xref:Microsoft.Office.Tools.ActionsPane>, car le <xref:Microsoft.Office.Tools.ActionsPane> est incorporé au volet des tâches. Toutefois, vous pouvez modifier par programmation la largeur du volet des tâches en définissant la propriété <xref:Microsoft.Office.Core.CommandBar.Width%2A> du <xref:Microsoft.Office.Core.CommandBar> qui représente le volet des tâches. Vous pouvez modifier la hauteur du volet des tâches s'il est ancré horizontalement ou est flottant.

 Le redimensionnement par programmation du volet des tâches n’est pas recommandé, car l’utilisateur doit pouvoir sélectionner la taille du volet des tâches qui correspond le mieux à ses besoins. Toutefois, si vous devez redimensionner la largeur du volet Office, vous pouvez utiliser le code suivant pour effectuer cette tâche.

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]

## <a name="reposition-the-actions-pane"></a>Repositionner le volet Actions
 Vous ne pouvez pas repositionner directement le <xref:Microsoft.Office.Tools.ActionsPane>, car il est incorporé au volet des tâches. Toutefois, vous pouvez déplacer par programmation le volet des tâches en définissant la propriété <xref:Microsoft.Office.Core.CommandBar.Position%2A> du <xref:Microsoft.Office.Core.CommandBar> qui représente le volet des tâches.

 Le repositionnement par programmation du volet des tâches n’est pas recommandé, car l’utilisateur doit pouvoir choisir la position du volet de tâches sur l’écran qui correspond le mieux à ses besoins. Cependant, si vous devez déplacer le volet des tâches vers un emplacement particulier, vous pouvez utiliser le code suivant pour effectuer cette tâche.

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]

> [!NOTE]
> Les utilisateurs finaux peuvent repositionner manuellement le volet de tâches à tout moment. Il n'existe aucun moyen de garantir que le volet des tâches demeure ancré à la position indiquée par programmation. Toutefois, vous pouvez vérifier les modifications de l'orientation et vous assurer que les contrôles du volet Actions sont empilés dans le bon sens. Pour plus d’informations, consultez [Comment : gérer la disposition des contrôles dans les volets actions](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 La définition <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> des propriétés et de <xref:Microsoft.Office.Tools.ActionsPane> ne modifie pas sa position, car l' <xref:Microsoft.Office.Tools.ActionsPane> objet est incorporé dans le volet des tâches.

 Si le volet des tâches n’est pas ancré, vous pouvez définir les propriétés <xref:Microsoft.Office.Core.CommandBar.Top%2A> et <xref:Microsoft.Office.Core.CommandBar.Left%2A> de l’objet <xref:Microsoft.Office.Core.CommandBar> qui représente le volet des tâches. Le code suivant déplace un volet des tâches non ancré vers l'angle supérieur gauche du document.

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des contrôles WPF dans les solutions Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Comment : ajouter un volet actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Procédure pas à pas : insertion de texte dans un document à partir d’un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Procédure pas à pas : liaison de données à des contrôles dans un volet Actions Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)
- [Procédure pas à pas : liaison de données à des contrôles dans un volet Actions Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)
- [Comment : gérer la disposition des contrôles dans les volets actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Procédure pas à pas : insertion de texte dans un document à partir d’un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
