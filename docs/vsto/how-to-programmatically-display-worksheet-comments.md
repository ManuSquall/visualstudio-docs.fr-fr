---
title: 'Comment : afficher des commentaires de feuille de calcul par programmation'
description: Découvrez comment vous pouvez afficher et masquer des commentaires dans une feuille de calcul Microsoft Excel au niveau du document ou de l’application par programmation.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af327a6756189c73f80f624205451274abf19264
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828668"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Comment : afficher des commentaires de feuille de calcul par programmation
  Vous pouvez afficher et masquer des commentaires dans des feuilles de calcul Microsoft Office Excel par programmation.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Pour afficher tous les commentaires dans une feuille de calcul dans une personnalisation au niveau du document

1. Affectez à la propriété <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> la valeur **true** si vous souhaitez afficher les commentaires ; sinon, affectez-lui la valeur **false**. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet31":::

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Pour afficher tous les commentaires dans une feuille de calcul dans un complément VSTO de niveau application

1. Affectez à la propriété <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> la valeur **true** si vous souhaitez afficher les commentaires ; sinon, affectez-lui la valeur **false**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet21":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Comment : ajouter et supprimer des commentaires de feuille de calcul par programmation](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
