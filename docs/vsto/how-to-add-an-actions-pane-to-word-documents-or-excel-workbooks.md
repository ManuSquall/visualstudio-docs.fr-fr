---
title: Ajouter un volet actions à des documents Word ou à des classeurs Excel
description: En savoir plus sur l’ajout d’un volet actions à un document Word Microsoft Office ou un classeur Microsoft Excel, vous devez d’abord créer un contrôle utilisateur Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 69d675209f2a3ac47e8681da8fca73c5cd86e95d
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848064"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel
  Pour ajouter un volet actions à un document Word Microsoft Office ou à un classeur Microsoft Excel, commencez par créer un contrôle utilisateur Windows Forms. Ensuite, ajoutez le contrôle utilisateur à la <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propriété du `ThisDocument.ActionsPane` champ (Word) ou du `ThisWorkbook.ActionsPane` champ (Excel) dans votre projet.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="creating-the-user-control"></a>Création du contrôle utilisateur
 La procédure suivante montre comment créer un contrôle utilisateur dans un projet Word ou Excel. Elle ajoute également un bouton au contrôle utilisateur qui écrit du texte dans le document ou le classeur lorsque l’utilisateur clique dessus.

#### <a name="to-create-the-user-control"></a>Pour créer le contrôle utilisateur

1. Ouvrez votre projet au niveau du document Word ou Excel dans Visual Studio.

2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **contrôle du volet Actions**, nommez-le **HelloControl**, puis cliquez sur **Ajouter**.

    > [!NOTE]
    > Vous pouvez également ajouter un élément de **contrôle utilisateur** à votre projet. Les classes générées par les éléments de contrôle de **volet Actions** et de **contrôle utilisateur** sont équivalentes de façon fonctionnelle.

4. À partir de l’onglet **Windows Forms** de la **boîte à outils,** faites glisser un contrôle **bouton** sur le contrôle.

    > [!NOTE]
    > Si le contrôle n’est pas visible dans le concepteur, double-cliquez sur **HelloControl** dans **Explorateur de solutions**.

5. Ajoutez le code au <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements du bouton. L’exemple suivant montre le code d’un document Word Microsoft Office.

     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]

6. En C#, vous devez ajouter un gestionnaire d’événements pour le clic sur le bouton. Vous pouvez placer ce code dans le `HelloControl` constructeur après l’appel à `InitializeComponent` .

     Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]

## <a name="add-the-user-control-to-the-actions-pane"></a>Ajouter le contrôle utilisateur au volet Actions
 Pour afficher le volet Actions, ajoutez le contrôle utilisateur à la <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propriété du `ThisDocument.ActionsPane` champ (Word) ou du `ThisWorkbook.ActionsPane` champ (Excel).

### <a name="to-add-the-user-control-to-the-actions-pane"></a>Pour ajouter le contrôle utilisateur au volet Actions

1. Ajoutez le code suivant à la `ThisDocument` `ThisWorkbook` classe ou sous la forme d’une déclaration au niveau de la classe (n’ajoutez pas ce code à une méthode).

     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]

2. Ajoutez le code suivant au `ThisDocument_Startup` Gestionnaire d’événements de la `ThisDocument` classe ou du `ThisWorkbook_Startup` Gestionnaire d’événements de la `ThisWorkbook` classe.

     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)
- [Procédure pas à pas : insertion de texte dans un document à partir d’un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Comment : gérer la disposition des contrôles dans les volets actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Procédure pas à pas : insertion de texte dans un document à partir d’un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
