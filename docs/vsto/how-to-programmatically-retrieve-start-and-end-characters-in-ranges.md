---
title: 'Comment : récupérer les caractères de début et fin dans les plages par programmation | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a79112e80885dfd64b85a90125ea059277725d33
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Comment : récupérer les caractères de début et de fin dans les plages par programmation
  Cet exemple montre comment vous pouvez récupérer les positions de début et de fin des caractères d’une plage.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Pour récupérer les caractères de début et de fin d’une plage dans une personnalisation au niveau du document  
  
1.  Obtenez les valeurs des propriétés <xref:Microsoft.Office.Interop.Word.Range.Start%2A> et <xref:Microsoft.Office.Interop.Word.Range.End%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range> . L’exemple de code suivant obtient la position de début et de fin de la deuxième phrase du document. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-an-vsto-add-in"></a>Pour récupérer les caractères de début et de fin d’une plage en utilisant un complément VSTO  
  
1.  Obtenez les valeurs des propriétés <xref:Microsoft.Office.Interop.Word.Range.Start%2A> et <xref:Microsoft.Office.Interop.Word.Range.End%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range> . L’exemple de code suivant obtient la position de début et de fin de la deuxième phrase du document actif. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : définir par programme et sélectionner des plages dans des Documents](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Comment : étendre des plages dans des Documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Comment : réinitialiser des plages dans Word Documents par programmation](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Comment : réduire des plages par programmation ou des sélections dans des Documents](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Comment : exclure les marques de paragraphe par programmation lorsque vous créez des plages](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Guide pratique pour compter des caractères dans les documents par programmation](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  