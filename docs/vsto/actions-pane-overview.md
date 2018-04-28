---
title: Vue d’ensemble du volet Actions | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 50f39b6fc292bba2081d8eb5c3bc87d6f9041b49
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
---
# <a name="actions-pane-overview"></a>Vue d'ensemble du volet Actions
  Un volet actions est un **Actions de Document** volet qui est attaché à un document spécifique de Microsoft Office Word ou un classeur Microsoft Office Excel. Le volet actions est hébergé dans le volet de tâches, ainsi que d’autres volets de tâches intégrés, tels que les **Source XML** volet dans Excel ou le **Styles et mise en forme** volet de tâches dans Word. Vous pouvez utiliser des contrôles Windows Forms ou WPF pour concevoir l'interface utilisateur du volet Actions.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

 Vous pouvez créer un volet Actions uniquement dans une personnalisation au niveau du document pour Word ou Excel. Vous ne pouvez pas créer un volet Actions dans un complément VSTO. Pour plus d'informations, consultez [Fonctionnalités disponibles par type d'application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  

> [!NOTE]  
>  Le volet Actions diffère des volets de tâches personnalisés. Les volets de tâches personnalisés sont associés à l'application, pas à un document spécifique. Vous pouvez créer des volets de tâches personnalisés dans les compléments VSTO pour certaines applications Microsoft Office. Pour plus d’informations, consultez [Vue d’ensemble des volets de tâches personnalisés](../vsto/custom-task-panes.md).  

 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire faire : utiliser WPF contrôles à l’intérieur d’un volet Actions Excel ?](http://go.microsoft.com/fwlink/?LinkId=132763).

## <a name="displaying-the-actions-pane"></a>Affichage du volet Actions  
 Le volet Actions est représenté par la classe <xref:Microsoft.Office.Tools.ActionsPane>. Lorsque vous créez un projet au niveau du document, une instance de cette classe est disponible pour votre code à l'aide du champ `ActionsPane` de la classe `ThisWorkbook` (pour Excel) ou `ThisDocument` (pour Word) de votre projet. Pour afficher le volet Actions, ajoutez un contrôle Windows Forms à la propriété <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> du champ `ActionsPane`. L'exemple de code suivant ajoute un contrôle nommé `actions` au volet Actions.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  

 Le volet Actions devient visible au moment de l'exécution, dès que vous lui ajoutez explicitement un contrôle. Une fois que le volet Actions est affiché, vous pouvez dynamiquement ajouter ou supprimer des contrôles en réponse aux actions de l'utilisateur. En général, vous ajoutez le code pour afficher le volet Actions du gestionnaire d'événements `Startup` de `ThisDocument` ou `ThisWorkbook` afin que le volet Actions soit visible lorsque l'utilisateur ouvre le document pour la première fois. Toutefois, vous souhaiterez peut-être afficher le volet Actions uniquement en réponse à l'action d'un utilisateur dans le document. Par exemple, vous pouvez ajouter le code à l'événement `Click` d'un contrôle sur le document.  

### <a name="adding-multiple-controls-to-the-actions-pane"></a>Ajout de plusieurs contrôles au volet Actions  
 Lorsque vous ajoutez plusieurs contrôles au volet actions, vous devez regrouper les contrôles dans un contrôle utilisateur et puis ajoutez le contrôle utilisateur à la <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propriété. Ce processus comprend les étapes suivantes :  

1.  Créer l’interface utilisateur (IU) du volet actions en ajoutant un **contrôle de volet Actions** ou **contrôle utilisateur** élément à votre projet. Ces deux éléments incluent une classe <xref:System.Windows.Forms.UserControl> Windows Forms personnalisée. Le **contrôle de volet Actions** et **contrôle utilisateur** éléments sont équivalents ; la seule différence est leur nom.  

2.  Ajouter des contrôles Windows Forms au <xref:System.Windows.Forms.UserControl> à l'aide du concepteur ou en écrivant du code.  

    > [!NOTE]  
    >  Vous pouvez aussi ajouter des contrôles WPF au volet Actions en ajoutant un <xref:System.Windows.Controls.UserControl> WPF au <xref:System.Windows.Forms.UserControl> Windows Forms. Pour plus d’informations, consultez [à l’aide de contrôles WPF dans les Solutions Office](../vsto/using-wpf-controls-in-office-solutions.md).  

3.  Ajouter une instance du contrôle utilisateur personnalisé aux contrôles contenus dans le champ `ActionsPane` de la classe `ThisWorkbook` (pour Excel) ou `ThisDocument` (pour Word) de votre projet.  

 Pour obtenir des exemples qui illustrent ce processus plus en détail, consultez [Comment : ajouter un volet Actions à des Documents Word ou des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  

## <a name="hiding-the-actions-pane"></a>Masquage du volet Actions  
 Bien que la classe <xref:Microsoft.Office.Tools.ActionsPane> ait une méthode <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> et une propriété <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>, vous ne pouvez pas supprimer le volet Actions à partir de l'interface utilisateur à l'aide des membres de la classe <xref:Microsoft.Office.Tools.ActionsPane> elle-même. Appel de la <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> méthode ou un paramètre le <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> propriété **false** masque uniquement les contrôles du volet actions ; il ne masque pas le volet de tâches.  

 Pour masquer le volet de tâches dans votre solution, vous disposez de plusieurs options :  

-   Pour Word, définissez la <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> propriété de la <xref:Microsoft.Office.Interop.Word.TaskPane> objet qui représente le volet de tâches Actions de Document **false**. L'exemple de code suivant est destiné à être exécuté à partir de la classe `ThisDocument` de votre projet.  

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]  

-   Pour Excel, définissez la <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> propriété de la <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> objet **false**. L'exemple de code suivant est destiné à être exécuté à partir de la classe `ThisWorkbook` de votre projet.  

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]  

-   Pour Word ou Excel, vous pouvez également définir le <xref:Microsoft.Office.Core.CommandBar.Visible%2A> propriété de la barre de commandes qui représente le volet de tâches **false**. L'exemple de code suivant est destiné à être exécuté à partir de la classe `ThisDocument` ou `ThisWorkbook` de votre projet.  

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]  

### <a name="clearing-the-actions-pane-when-the-document-is-opened"></a>Effacement du volet Actions lorsque le document est ouvert  
 Lorsqu’un utilisateur enregistre le document alors que le volet actions est visible, le volet actions est visible chaque fois que le document est ouvert, le volet actions contienne des contrôles ou non. Si vous souhaitez contrôler à quel moment il apparaît, appelez la méthode <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> du champ `ActionsPane` du gestionnaire d'événements `Startup` `ThisDocument` ou `ThisWorkbook` pour vous assurer que le volet Actions n'est pas visible lorsque le document est ouvert.  

### <a name="determining-when-the-actions-pane-is-closed"></a>Détermination du moment où le volet Actions est fermé  
 Il n'y a aucun événement déclenché lorsque le volet Actions est fermé. Bien que la <xref:Microsoft.Office.Tools.ActionsPane> classe ait un événement <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>, celui-ci n'est pas déclenché lorsque l'utilisateur final ferme le volet Actions. Au lieu de cela, cet événement est déclenché lorsque les contrôles du volet actions sont masqués par l’appel le <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> méthode ou en définissant le <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> propriété **false**.  

 Lorsque l’utilisateur ferme le volet actions, l’utilisateur puisse l’afficher à nouveau en effectuant l’une des procédures suivantes dans l’interface utilisateur (IU) de l’application.  

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Pour afficher le volet Actions à l'aide de l'interface utilisateur de Word ou Excel  

1.  Dans le ruban, cliquez sur le **vue** onglet.  

2.  Dans le **afficher/masquer** , cliquez sur le **Actions de Document** bouton bascule.  

## <a name="programming-actions-pane-events"></a>Programmation des événements du volet Actions  
 Vous pouvez ajouter plusieurs contrôles utilisateur au volet Actions, puis écrire le code pour répondre aux événements sur le document en affichant et en masquant les contrôles utilisateur. Si vous mappez des éléments du schéma XML à votre document, vous pouvez afficher certains contrôles utilisateur dans le volet Actions chaque fois que le point d'insertion se trouve dans l'un des éléments XML. Pour plus d’informations, consultez [Comment : schémas de mappage à des Documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) et [Comment : schémas de mappage à des feuilles de calcul à l’intérieur de Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  

 Vous pouvez également écrire le code pour répondre aux événements de n'importe quel objet, y compris les événements de contrôle hôte, d'application ou de document. Pour plus d'informations, consultez [Procédure pas à pas : programmation d'événements d'un contrôle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  

## <a name="binding-data-to-controls-on-the-actions-pane"></a>Liaison de données aux contrôles dans le volet Actions  
 Les contrôles du volet Actions ont les mêmes fonctionnalités de liaison de données que les contrôles Windows Forms. Vous pouvez lier les contrôles aux sources de données telles que les jeux de données, les groupes de données typées et XML. Pour plus d'informations, consultez [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  

 Vous pouvez lier des contrôles du volet Actions et des contrôles du document au même jeu de données. Par exemple, vous pouvez créer une relation maître/détail entre les contrôles du volet Actions et les contrôles de la feuille de calcul. Pour plus d’informations, consultez [procédure pas à pas : liaison de données aux contrôles dans un volet Actions Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  

## <a name="validating-data-in-actions-pane-controls"></a>Validation des données dans les contrôles du volet Actions  
 Si vous affichez un message dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.Validating> d'un contrôle du volet Actions, l'événement peut être déclenché une deuxième fois lorsque le focus se déplace du contrôle au message. Pour éviter ce problème, utilisez un contrôle <xref:System.Windows.Forms.ErrorProvider> pour afficher les messages d'erreur de validation.  

## <a name="user-control-stacking-order"></a>Ordre d'empilement des contrôles utilisateur  
 Si vous utilisez plusieurs contrôles utilisateur, vous pouvez écrire le code pour empiler correctement les contrôles utilisateur du volet Actions, qu'il soit ancré verticalement ou horizontalement. Vous pouvez définir l'ordre d'empilement des contrôles utilisateur du volet Actions à l'aide de l'énumération <xref:Microsoft.Office.Tools.StackStyle> de la propriété <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>. Pour plus d’informations, consultez [Comment : gérer la disposition des contrôles dans les volets Actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)  

 La propriété <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> peut accepter les valeurs d'énumération <xref:Microsoft.Office.Tools.StackStyle> suivantes.  

|Style d'empilement|Définition|  
|--------------------|----------------|  
|FromBottom|Empilez à partir du bas du volet Actions.|  
|FromLeft|Empilez à partir de la gauche du volet Actions.|  
|FromRight|Empilez à partir de la droite du volet Actions.|  
|FromTop|Empilez à partir du haut du volet Actions.|  
|Aucun|Aucun ordre d'empilement défini ; l'ordre est contrôlé par le développeur.|  

 Le code suivant définit la propriété <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> de façon à empiler les contrôles utilisateur à partir du haut du volet Actions.  

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]  

## <a name="anchoring-controls"></a>Ancrage des contrôles  
 Si l'utilisateur redimensionne le volet Actions au moment de l'exécution, les contrôles peuvent être redimensionnés avec le volet Actions. Vous pouvez utiliser la propriété <xref:System.Windows.Forms.Control.Anchor%2A> d'un contrôle Windows Forms pour ancrer des contrôles au volet Actions. Vous pouvez également ancrer les contrôles Windows Forms au contrôle utilisateur de la même manière. Pour plus d’informations, consultez [Comment : ancrer des contrôles dans les Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  

## <a name="resizing-the-actions-pane"></a>Redimensionnement du volet Actions  
 Vous ne pouvez pas modifier directement la taille d'un <xref:Microsoft.Office.Tools.ActionsPane>, car le <xref:Microsoft.Office.Tools.ActionsPane> est incorporé au volet des tâches. Toutefois, vous pouvez modifier par programmation la largeur du volet des tâches en définissant la propriété <xref:Microsoft.Office.Core.CommandBar.Width%2A> du <xref:Microsoft.Office.Core.CommandBar> qui représente le volet des tâches. Vous pouvez modifier la hauteur du volet des tâches s’il est ancré horizontalement ou est flottant.  

 Le redimensionnement par programmation le volet de tâches n’est pas recommandé, car l’utilisateur doit être en mesure de choisir la taille du volet de tâches qui convient le mieux à leurs besoins. Toutefois, si vous devez redimensionner la largeur du volet Office, vous pouvez utiliser le code suivant pour effectuer cette tâche.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]  

## <a name="repositioning-the-actions-pane"></a>Repositionnement du volet Actions  
 Vous ne pouvez pas repositionner directement le <xref:Microsoft.Office.Tools.ActionsPane>, car il est incorporé au volet des tâches. Toutefois, vous pouvez déplacer par programmation le volet des tâches en définissant la propriété <xref:Microsoft.Office.Core.CommandBar.Position%2A> du <xref:Microsoft.Office.Core.CommandBar> qui représente le volet des tâches.  

 Le repositionnement par programmation du volet des tâches n'est généralement pas recommandé, car l'utilisateur doit pouvoir choisir la position du volet des tâches qui correspond le mieux à ses besoins. Cependant, si vous devez déplacer le volet des tâches vers un emplacement particulier, vous pouvez utiliser le code suivant pour effectuer cette tâche.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]  

> [!NOTE]  
>  Les utilisateurs finaux peuvent repositionner manuellement le volet de tâches à tout moment. Il n'existe aucun moyen de garantir que le volet des tâches demeure ancré à la position indiquée par programmation. Toutefois, vous pouvez vérifier les modifications de l'orientation et vous assurer que les contrôles du volet Actions sont empilés dans le bon sens. Pour plus d’informations, consultez [Comment : gérer la disposition des contrôles dans les volets Actions](../vsto/how-to-manage-control-layout-on-actions-panes.md).  

 Définition de la <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> et <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> propriétés de la <xref:Microsoft.Office.Tools.ActionsPane> ne change pas sa position, car le <xref:Microsoft.Office.Tools.ActionsPane> objet est incorporé dans le volet des tâches.  

 Si le volet des tâches n'est pas ancré, vous pouvez définir les propriétés <xref:Microsoft.Office.Core.CommandBar.Top%2A> et <xref:Microsoft.Office.Core.CommandBar.Left%2A> de l'objet <xref:Microsoft.Office.Core.CommandBar> qui représente le volet des tâches. Le code suivant déplace un volet des tâches non ancré vers l’angle supérieur gauche du document.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]  

## <a name="see-also"></a>Voir aussi  
 [Utilisation de contrôles WPF dans les Solutions Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Comment : ajouter un volet Actions à des Documents Word ou des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procédure pas à pas : Insertion de texte dans un Document à partir d’un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Procédure pas à pas : Liaison de données aux contrôles dans un volet Actions Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [Procédure pas à pas : Liaison de données aux contrôles dans un volet Actions Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [Comment : gérer la disposition des contrôles dans les volets Actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Procédure pas à pas : insertion de texte dans un document à partir d’un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
