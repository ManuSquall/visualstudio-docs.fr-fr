---
title: Obtenez les caractères de début & de fin dans les plages par programmation
description: Cet exemple montre comment vous pouvez récupérer les positions de début et de fin des caractères d’une plage.
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4739043362a0f183574959f32a6e324d03522f65
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824027"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Comment : récupérer des caractères de début et de fin dans les plages par programmation
  Cet exemple montre comment vous pouvez récupérer les positions de début et de fin des caractères d’une plage.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Pour récupérer les caractères de début et de fin d’une plage dans une personnalisation au niveau du document

1. Obtenez les valeurs des propriétés <xref:Microsoft.Office.Interop.Word.Range.Start%2A> et <xref:Microsoft.Office.Interop.Word.Range.End%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range> . L’exemple de code suivant obtient la position de début et de fin de la deuxième phrase du document. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` de votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet25":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet25":::

## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Pour récupérer les caractères de début et de fin d’une plage à l’aide d’un complément VSTO

1. Obtenez les valeurs des propriétés <xref:Microsoft.Office.Interop.Word.Range.Start%2A> et <xref:Microsoft.Office.Interop.Word.Range.End%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range> . L’exemple de code suivant obtient la position de début et de fin de la deuxième phrase du document actif. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet25":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet25":::

## <a name="see-also"></a>Voir aussi
- [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Comment : réinitialiser des plages dans les documents Word par programmation](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Comment : réduire des plages ou des sélections dans des documents par programmation](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Comment : exclure des marques de paragraphe lors de la création de plages par programmation](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Comment : compter des caractères dans les documents par programmation](../vsto/how-to-programmatically-count-characters-in-documents.md)
