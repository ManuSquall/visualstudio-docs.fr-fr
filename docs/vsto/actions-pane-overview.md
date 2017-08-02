---
title: "Vue d&#39;ensemble du volet Actions"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "volets Actions (développement Office dans Visual Studio)"
  - "volets Actions (développement Office dans Visual Studio), à propos des volets Actions"
  - "documents dynamiques (développement Office dans Visual Studio)"
  - "contrôles utilisateur (développement Office dans Visual Studio), volets Actions"
ms.assetid: 1b9b7db5-b19f-44ea-a774-f0962ca03bd2
caps.latest.revision: 101
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 100
---
# Vue d&#39;ensemble du volet Actions
  Un volet Actions est un volet de tâches **Actions de document** qui est attaché à un document Microsoft Office Word ou un classeur Microsoft Office Excel spécifique.  Il est hébergé dans le volet de tâches Office en compagnie d'autres volets de tâches intégrés, tels que le volet de tâches **Source XML** dans Excel ou le volet de tâches **Styles et mise en forme** dans Word.  Vous pouvez utiliser des contrôles Windows Forms ou WPF pour concevoir l'interface utilisateur du volet Actions.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Vous pouvez créer un volet Actions uniquement dans une personnalisation au niveau du document pour Word ou Excel.  Vous ne pouvez pas créer un volet Actions dans un complément VSTO.  Pour plus d'informations, consultez [Fonctionnalités disponibles par type d'application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Le volet Actions diffère des volets de tâches personnalisés.  Les volets de tâches personnalisés sont associés à l'application, pas à un document spécifique.  Vous pouvez créer des volets de tâches personnalisés dans les compléments VSTO pour certaines applications Microsoft Office.  Pour plus d'informations, consultez [Volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
 ![lien vers la vidéo](~/data-tools/media/playvideo.gif "lien vers la vidéo") Pour visionner la démonstration vidéo associée, consultez [Comment : utiliser les contrôles WPF dans un volet Actions Excel](http://go.microsoft.com/fwlink/?LinkID=132763).  
  
## Affichage du volet Actions  
 Le volet Actions est représenté par la classe <xref:Microsoft.Office.Tools.ActionsPane>.  Lorsque vous créez un projet au niveau du document, une instance de cette classe est disponible pour votre code à l'aide du champ `ActionsPane` de la classe `ThisWorkbook` \(pour Excel\) ou `ThisDocument` \(pour Word\) de votre projet.  Pour afficher le volet Actions, ajoutez un contrôle Windows Forms à la propriété <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> du champ `ActionsPane`.  L'exemple de code suivant ajoute un contrôle nommé `actions` au volet Actions.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#7)]  
  
 Le volet Actions devient visible au moment de l'exécution, dès que vous lui ajoutez explicitement un contrôle.  Une fois que le volet Actions est affiché, vous pouvez dynamiquement ajouter ou supprimer des contrôles en réponse aux actions de l'utilisateur.  En général, vous ajoutez le code pour afficher le volet Actions du gestionnaire d'événements `Startup` de `ThisDocument` ou `ThisWorkbook` afin que le volet Actions soit visible lorsque l'utilisateur ouvre le document pour la première fois.  Toutefois, vous souhaiterez peut\-être afficher le volet Actions uniquement en réponse à l'action d'un utilisateur dans le document.  Par exemple, vous pouvez ajouter le code à l'événement `Click` d'un contrôle sur le document.  
  
### Ajout de plusieurs contrôles au volet Actions  
 Si vous ajoutez plusieurs contrôles au volet Actions, dans la plupart des cas vous devez regrouper les contrôles dans un contrôle utilisateur, puis ajouter le contrôle utilisateur à la propriété <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>.  Ce processus comprend les étapes suivantes :  
  
1.  Créer l'interface utilisateur \(IU\) du volet Actions en ajoutant un élément **Contrôle de volet Actions** ou **Contrôle utilisateur** à votre projet.  Ces deux éléments incluent une classe <xref:System.Windows.Forms.UserControl> Windows Forms personnalisée.  Les éléments **Contrôle de volet Actions** et **Contrôle utilisateur** sont équivalents, la seule différence est leur nom.  
  
2.  Ajouter des contrôles Windows Forms au <xref:System.Windows.Forms.UserControl> à l'aide du concepteur ou en écrivant du code.  
  
    > [!NOTE]  
    >  Vous pouvez aussi ajouter des contrôles WPF au volet Actions en ajoutant un <xref:System.Windows.Controls.UserControl> WPF au <xref:System.Windows.Forms.UserControl> Windows Forms.  Pour plus d'informations, consultez [Utilisation de contrôles WPF dans les solutions Office](../vsto/using-wpf-controls-in-office-solutions.md).  
  
3.  Ajouter une instance du contrôle utilisateur personnalisé aux contrôles contenus dans le champ `ActionsPane` de la classe `ThisWorkbook` \(pour Excel\) ou `ThisDocument` \(pour Word\) de votre projet.  
  
 Pour obtenir des exemples qui illustrent ce processus plus en détail, consultez [Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
## Masquage du volet Actions  
 Bien que la classe <xref:Microsoft.Office.Tools.ActionsPane> ait une méthode <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> et une propriété <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>, vous ne pouvez pas supprimer le volet Actions à partir de l'interface utilisateur à l'aide des membres de la classe <xref:Microsoft.Office.Tools.ActionsPane> elle\-même.  L'appel de la méthode <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> ou la définition de la propriété <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> avec la valeur **false** masque uniquement les contrôles du volet Actions ; il ne masque pas le volet de tâches.  
  
 Pour masquer le volet de tâches dans votre solution, vous disposez de plusieurs options :  
  
-   Pour Word, définissez la propriété <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> de l'objet <xref:Microsoft.Office.Interop.Word.TaskPane> qui représente le volet de tâches Actions de document avec la valeur **false**.  L'exemple de code suivant est destiné à être exécuté à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#34)]  
  
-   Pour Excel, définissez la propriété <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> de l'objet <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> avec la valeur **false**.  L'exemple de code suivant est destiné à être exécuté à partir de la classe `ThisWorkbook` de votre projet.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#11)]  
  
-   Pour Word ou Excel, vous pouvez également définir la propriété <xref:Microsoft.Office.Core.CommandBar.Visible%2A> de la barre de commandes qui représente le volet de tâches avec la valeur **false**.  L'exemple de code suivant est destiné à être exécuté à partir de la classe `ThisDocument` ou `ThisWorkbook` de votre projet.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#9)]  
  
### Effacement du volet Actions lorsque le document est ouvert  
 Si l'utilisateur enregistre le document alors que le volet Actions est visible, celui\-ci apparaît chaque fois que le document est ouvert, que le volet Actions contienne des contrôles ou non.  Si vous souhaitez contrôler à quel moment il apparaît, appelez la méthode <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> du champ `ActionsPane` du gestionnaire d'événements `Startup` `ThisDocument` ou `ThisWorkbook` pour vous assurer que le volet Actions n'est pas visible lorsque le document est ouvert.  
  
### Détermination du moment où le volet Actions est fermé  
 Il n'y a aucun événement déclenché lorsque le volet Actions est fermé.  Bien que la <xref:Microsoft.Office.Tools.ActionsPane> classe ait un événement <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>, celui\-ci n'est pas déclenché lorsque l'utilisateur final ferme le volet Actions.  Au lieu de cela, cet événement est déclenché lorsque les contrôles du volet Actions sont masqués par l'appel de la méthode <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> ou par la définition de la propriété <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> avec la valeur **false**.  
  
 Si l'utilisateur final ferme le volet Actions, il peut l'afficher à nouveau en exécutant l'une des procédures suivantes dans l'interface utilisateur de l'application.  
  
##### Pour afficher le volet Actions à l'aide de l'interface utilisateur de Word ou Excel  
  
1.  Dans le ruban, cliquez sur l'onglet **Affichage**.  
  
2.  Dans le groupe **Afficher\/masquer**, cliquez sur le bouton bascule **Actions de document**.  
  
## Programmation des événements du volet Actions  
 Vous pouvez ajouter plusieurs contrôles utilisateur au volet Actions, puis écrire le code pour répondre aux événements sur le document en affichant et en masquant les contrôles utilisateur.  Si vous mappez des éléments du schéma XML à votre document, vous pouvez afficher certains contrôles utilisateur dans le volet Actions chaque fois que le point d'insertion se trouve dans l'un des éléments XML.  Pour plus d'informations, consultez [Comment : mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) et [Comment : mapper des schémas à des feuilles de calcul dans Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  
  
 Vous pouvez également écrire le code pour répondre aux événements de n'importe quel objet, y compris les événements de contrôle hôte, d'application ou de document.  Pour plus d'informations, consultez [Procédure pas à pas : programmation d'événements d'un contrôle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
## Liaison de données aux contrôles dans le volet Actions  
 Les contrôles du volet Actions ont les mêmes fonctionnalités de liaison de données que les contrôles Windows Forms.  Vous pouvez lier les contrôles aux sources de données telles que les jeux de données, les groupes de données typées et XML.  Pour plus d'informations, consultez [Liaison de données et Windows Forms](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27).  
  
 Vous pouvez lier des contrôles du volet Actions et des contrôles du document au même jeu de données.  Par exemple, vous pouvez créer une relation maître\/détail entre les contrôles du volet Actions et les contrôles de la feuille de calcul.  Pour plus d'informations, consultez [Procédure pas à pas : liaison de données aux contrôles dans un volet Actions Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
## Validation des données dans les contrôles du volet Actions  
 Si vous affichez un message dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.Validating> d'un contrôle du volet Actions, l'événement peut être déclenché une deuxième fois lorsque le focus se déplace du contrôle au message.  Pour éviter ce problème, utilisez un contrôle <xref:System.Windows.Forms.ErrorProvider> pour afficher les messages d'erreur de validation.  
  
## Ordre d'empilement des contrôles utilisateur  
 Si vous utilisez plusieurs contrôles utilisateur, vous pouvez écrire le code pour empiler correctement les contrôles utilisateur du volet Actions, qu'il soit ancré verticalement ou horizontalement.  Vous pouvez définir l'ordre d'empilement des contrôles utilisateur du volet Actions à l'aide de l'énumération <xref:Microsoft.Office.Tools.StackStyle> de la propriété <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>.  Pour plus d'informations, consultez [Comment : gérer la disposition des contrôles dans les volets Actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)  
  
 La propriété <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> peut accepter les valeurs d'énumération <xref:Microsoft.Office.Tools.StackStyle> suivantes.  
  
|Style d'empilement|Définition|  
|------------------------|----------------|  
|FromBottom|Empilez à partir du bas du volet Actions.|  
|FromLeft|Empilez à partir de la gauche du volet Actions.|  
|FromRight|Empilez à partir de la droite du volet Actions.|  
|FromTop|Empilez à partir du haut du volet Actions.|  
|None|Aucun ordre d'empilement défini ; l'ordre est contrôlé par le développeur.|  
  
 Le code suivant définit la propriété <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> de façon à empiler les contrôles utilisateur à partir du haut du volet Actions.  
  
 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#10)]  
  
## Ancrage des contrôles  
 Si l'utilisateur redimensionne le volet Actions au moment de l'exécution, les contrôles peuvent être redimensionnés avec le volet Actions.  Vous pouvez utiliser la propriété <xref:System.Windows.Forms.Control.Anchor%2A> d'un contrôle Windows Forms pour ancrer des contrôles au volet Actions.  Vous pouvez également ancrer les contrôles Windows Forms au contrôle utilisateur de la même manière.  Pour plus d'informations, consultez [Comment : ancrer des contrôles aux Windows Forms](http://msdn.microsoft.com/library/59ea914f-fbd3-427a-80fe-decd02f7ae6d).  
  
## Redimensionnement du volet Actions  
 Vous ne pouvez pas modifier directement la taille d'un <xref:Microsoft.Office.Tools.ActionsPane>, car le <xref:Microsoft.Office.Tools.ActionsPane> est incorporé au volet des tâches.  Toutefois, vous pouvez modifier par programmation la largeur du volet des tâches en définissant la propriété <xref:Microsoft.Office.Core.CommandBar.Width%2A> du <xref:Microsoft.Office.Core.CommandBar> qui représente le volet des tâches.  Vous pouvez modifier la hauteur du volet des tâches s'il est ancré horizontalement ou est flottant.  
  
 Le redimensionnement par programmation du volet des tâches n'est généralement pas recommandé, car l'utilisateur doit pouvoir choisir la taille du volet des tâches qui correspond le mieux à ses besoins.  Toutefois, si vous devez redimensionner la largeur du volet Office, vous pouvez utiliser le code suivant pour effectuer cette tâche.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#102)]  
  
## Repositionnement du volet Actions  
 Vous ne pouvez pas repositionner directement le <xref:Microsoft.Office.Tools.ActionsPane>, car il est incorporé au volet des tâches.  Toutefois, vous pouvez déplacer par programmation le volet des tâches en définissant la propriété <xref:Microsoft.Office.Core.CommandBar.Position%2A> du <xref:Microsoft.Office.Core.CommandBar> qui représente le volet des tâches.  
  
 Le repositionnement par programmation du volet des tâches n'est généralement pas recommandé, car l'utilisateur doit pouvoir choisir la position du volet des tâches qui correspond le mieux à ses besoins.  Cependant, si vous devez déplacer le volet des tâches vers un emplacement particulier, vous pouvez utiliser le code suivant pour effectuer cette tâche.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#100)]  
  
> [!NOTE]  
>  Les utilisateurs finaux peuvent repositionner manuellement le volet de tâches à tout moment.  Il n'existe aucun moyen de garantir que le volet des tâches demeure ancré à la position indiquée par programmation.  Toutefois, vous pouvez vérifier les modifications de l'orientation et vous assurer que les contrôles du volet Actions sont empilés dans le bon sens.  Pour plus d'informations, consultez [Comment : gérer la disposition des contrôles dans les volets Actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)  
  
 La définition des propriétés <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> et <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> de l'objet <xref:Microsoft.Office.Tools.ActionsPane> ne modifie pas sa position, car l'objet <xref:Microsoft.Office.Tools.ActionsPane> est incorporé au volet des tâches.  
  
 Si le volet des tâches n'est pas ancré, vous pouvez définir les propriétés <xref:Microsoft.Office.Core.CommandBar.Top%2A> et <xref:Microsoft.Office.Core.CommandBar.Left%2A> de l'objet <xref:Microsoft.Office.Core.CommandBar> qui représente le volet des tâches.  Le code suivant déplace un volet des tâches non ancré vers l'angle supérieur gauche du document.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#101)]  
  
## Voir aussi  
 [Utilisation de contrôles WPF dans les solutions Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procédure pas à pas : Insertion de texte dans un document à partir d'un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Procédure pas à pas : liaison de données aux contrôles dans un volet Actions Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [Procédure pas à pas : liaison de données aux contrôles dans un volet Actions Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [Comment : gérer la disposition des contrôles dans les volets Actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Procédure pas à pas : Insertion de texte dans un document à partir d'un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  