---
title: 'Comment : masquer des contrôles sur des feuilles de calcul lors de l’impression'
description: Découvrez que vous pouvez masquer les contrôles lors de l’impression d’une feuille de calcul Excel Microsoft Office qui contient des contrôles Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: acc90986dd394e69de12893aac01e0a4f662b1a3
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846491"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Comment : masquer des contrôles sur des feuilles de calcul lors de l’impression
  Lorsque vous imprimez un document Excel Microsoft Office qui contient des contrôles Windows Forms, les contrôles sont visibles sur la feuille de calcul imprimée. Vous pouvez masquer les contrôles lors de l’impression d’une feuille de calcul.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Si vous masquez des contrôles qui affichent des données, tels qu’un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> , les données du contrôle ne seront pas visibles sur la feuille de calcul imprimée.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Pour masquer des contrôles lors de l’impression d’une feuille de calcul

1. Créez ou ouvrez un projet Excel dans Visual Studio et vérifiez que **Feuil1** est visible dans le concepteur. Pour plus d’informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. À partir de l’onglet **contrôles communs** de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Excel.Controls.Button> contrôle vers une cellule sur `Sheet1` .

3. Dans la fenêtre **Propriétés** , affectez <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> à la propriété la valeur **false**.

## <a name="see-also"></a>Voir aussi
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [Vue d’ensemble des contrôles de Windows Forms sur les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Comment : redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md)
