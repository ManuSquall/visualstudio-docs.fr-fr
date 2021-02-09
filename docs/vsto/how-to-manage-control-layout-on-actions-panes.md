---
title: 'Comment : gérer la disposition des contrôles dans les volets actions'
description: Découvrez comment vous pouvez gérer la disposition des contrôles dans les volets actions en écrivant du code pour empiler correctement les contrôles utilisateur.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 49739b6011fcf977db84a3350929a56514040975
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918586"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Comment : gérer la disposition des contrôles dans les volets actions
  Un volet actions est ancré par défaut à droite d’un document ou d’une feuille de calcul ; Toutefois, elle peut être ancrée à gauche, en haut ou en bas. Si vous utilisez plusieurs contrôles utilisateur, vous pouvez écrire du code pour empiler correctement les contrôles utilisateur dans le volet Actions. Pour plus d’informations, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 L’ordre de pile des contrôles varie selon que le volet actions est ancré verticalement ou horizontalement.

> [!NOTE]
> Si l’utilisateur redimensionne le volet actions au moment de l’exécution, vous pouvez définir le redimensionnement des contrôles avec le volet Actions. Vous pouvez utiliser la propriété <xref:System.Windows.Forms.Control.Anchor%2A> d'un contrôle Windows Forms pour ancrer des contrôles au volet Actions. Pour plus d’informations, consultez [Comment : ancrer des contrôles sur Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Pour définir l’ordre de pile des contrôles de volet Actions

1. Ouvrez un projet au niveau du document pour Microsoft Office Word qui comprend un volet actions avec plusieurs contrôles utilisateur ou contrôles de volet Actions imbriqués. Pour plus d’informations, consultez [Comment : ajouter un volet actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

2. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur **ThisDocument.cs** ou sur **ThisDocument. vb** , puis cliquez sur **afficher le code**.

3. Dans le <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> Gestionnaire d’événements du volet Actions, vérifiez si l’orientation du volet actions est horizontale.

     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]

4. Si l’orientation est horizontale, empile les contrôles du volet d’action à partir de la gauche ; dans le cas contraire, empilez-les à partir du haut.

     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]

5. En C#, vous devez ajouter un gestionnaire d’événements pour le `ActionsPane` au <xref:Microsoft.Office.Tools.Word.Document.Startup> Gestionnaire d’événements. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]

6. Exécutez le projet et vérifiez que les contrôles du volet actions sont empilés de gauche à droite lorsque le volet actions est ancré en haut du document, et les contrôles sont empilés de haut en bas lorsque le volet actions est ancré à la partie droite du document.

## <a name="example"></a>Exemple
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite :

- Projet au niveau du document Word avec un volet actions qui contient plusieurs contrôles utilisateur ou contrôles de volet Actions imbriqués.

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)
- [Comment : ajouter un volet actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Comment : ajouter un volet actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Procédure pas à pas : insertion de texte dans un document à partir d’un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Procédure pas à pas : insertion de texte dans un document à partir d’un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
