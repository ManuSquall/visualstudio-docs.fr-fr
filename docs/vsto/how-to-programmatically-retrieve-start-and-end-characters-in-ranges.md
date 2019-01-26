---
title: 'Procédure : Récupérer par programme des caractères de début et de fin dans les plages'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 88876641d0c6e72385d6f9e514ff8135de9518fa
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863199"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Procédure : Récupérer par programme des caractères de début et de fin dans les plages
  Cet exemple montre comment vous pouvez récupérer les positions de début et de fin des caractères d’une plage.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Pour récupérer les caractères de début et de fin d’une plage dans une personnalisation au niveau du document  
  
1.  Obtenez les valeurs des propriétés <xref:Microsoft.Office.Interop.Word.Range.Start%2A> et <xref:Microsoft.Office.Interop.Word.Range.End%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range> . L’exemple de code suivant obtient la position de début et de fin de la deuxième phrase du document. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Pour récupérer les caractères de début et de fin d’une plage en utilisant un complément, VSTO  
  
1.  Obtenez les valeurs des propriétés <xref:Microsoft.Office.Interop.Word.Range.Start%2A> et <xref:Microsoft.Office.Interop.Word.Range.End%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range> . L’exemple de code suivant obtient la position de début et de fin de la deuxième phrase du document actif. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Guide pratique pour Étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Guide pratique pour Réinitialisation par programmation des plages dans des documents Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Guide pratique pour Réduire des plages ou des sélections dans des documents par programmation](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Guide pratique pour Par programmation exclure les marques de paragraphe lors de la création de plages](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Guide pratique pour Compter les caractères dans les documents par programmation](../vsto/how-to-programmatically-count-characters-in-documents.md)  
