---
title: 'Procédure : Masquer du texte dans des documents par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0c39a82a6b381296c47dcbf059b22e351dba3afc
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646081"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Procédure : Masquer du texte dans des documents par programmation
  Vous pouvez masquer du texte dans un document en définissant la propriété <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> de <xref:Microsoft.Office.Interop.Word.Range.Font%2A> pour une plage de texte particulière.

 Par exemple, vous pouvez masquer temporairement le texte dans un <xref:Microsoft.Office.Tools.Word.Bookmark> (dans une personnalisation au niveau du document) ou un <xref:Microsoft.Office.Interop.Word.Bookmark> (dans un complément VSTO) avant d’envoyer un document à une imprimante.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Pour masquer du texte dans un contrôle Bookmark pendant l’impression du document

1.  Créez une procédure qui masque tout le texte figurant dans une plage spécifiée.

     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]

2.  Créez une procédure qui affiche tout le texte figurant dans une plage spécifiée.

     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]

3.  Passez la plage d’un signet à la méthode `HideText` , imprimez le document, puis passez la même plage à la méthode `UnhideText` .

     Vous pouvez utiliser l’exemple de code suivant dans une personnalisation au niveau du document. Pour utiliser cet exemple, exécutez-le à partir de la classe `ThisDocument` dans votre projet.

     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]

     L'exemple de code suivant peut être utilisé dans un complément VSTO. Cet exemple utilise le document actif. Pour utiliser l'exemple, exécutez-le à partir de la classe `ThisAddIn` dans votre projet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple de code suppose que le document contient un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle (dans une personnalisation au niveau du document) ou <xref:Microsoft.Office.Interop.Word.Bookmark> contrôle (dans un complément VSTO) nommé `bookmark1`.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Imprimer des documents par programmation](../vsto/how-to-programmatically-print-documents.md)
- [Guide pratique pour Définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Guide pratique pour Réinitialisation par programmation des plages dans des documents Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Guide pratique pour Mettre à jour par programme de texte d’un signet](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
