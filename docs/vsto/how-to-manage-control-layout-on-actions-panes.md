---
title: 'Procédure : Gérer la disposition des contrôles dans les volets actions'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 38f9e534fe213b766ea74c83604ddf1cafa1ac65
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647047"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Procédure : Gérer la disposition des contrôles dans les volets actions
  Un volet actions est ancré à droite d’un document ou une feuille de calcul par défaut ; Toutefois, il peut être ancré à gauche, haut ou bas. Si vous utilisez plusieurs contrôles utilisateur, vous pouvez écrire du code pour empiler correctement les contrôles utilisateur dans le volet actions. Pour plus d’informations, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 L’ordre de la pile des contrôles varie selon que le volet actions est ancré verticalement ou horizontalement.  
  
> [!NOTE]  
>  Si l’utilisateur redimensionne le volet actions lors de l’exécution, vous pouvez définir les contrôles à redimensionner avec le volet actions. Vous pouvez utiliser la propriété <xref:System.Windows.Forms.Control.Anchor%2A> d'un contrôle Windows Forms pour ancrer des contrôles au volet Actions. Pour plus d'informations, voir [Procédure : Ancrer des contrôles aux Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Pour définir l’ordre de la pile des contrôles de volet actions  
  
1.  Ouvrez un projet au niveau du document pour Microsoft Office Word qui inclut un volet actions avec plusieurs contrôles utilisateur ou contrôles de volet actions imbriqués. Pour plus d'informations, voir [Procédure : Ajouter un volet actions à des documents Word ou de classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  Avec le bouton droit **ThisDocument.cs** ou **ThisDocument.vb** dans **l’Explorateur de solutions** puis cliquez sur **afficher le Code**.  
  
3.  Dans le <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> Gestionnaire d’événements du volet actions, vérifiez si l’orientation du volet actions est horizontale.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  Si l’orientation est horizontale, empiler les contrôles de volet Actions à partir de la gauche ; Sinon, les empiler à partir du haut.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  En c#, vous devez ajouter un gestionnaire d’événements pour le `ActionsPane` à la <xref:Microsoft.Office.Tools.Word.Document.Startup> Gestionnaire d’événements. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : Créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  Exécutez le projet et vérifiez que les contrôles de volet actions sont empilés de gauche à droite lorsque le volet actions est ancré en haut du document, et les contrôles sont empilés de haut en bas lorsque le volet actions est ancré à droite du document.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple nécessite :  
  
-   Contrôle d’un projet au niveau du document de Word avec un volet actions qui contient plusieurs contrôles utilisateur ou le volet actions imbriqués.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Guide pratique pour Ajouter un volet actions à des documents Word ou des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Guide pratique pour Ajouter un volet actions aux classeurs des Documents Word ou Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procédure pas à pas : Insérer du texte dans un document à partir d’un volet actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Procédure pas à pas : Insérer du texte dans un document à partir d’un volet actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  