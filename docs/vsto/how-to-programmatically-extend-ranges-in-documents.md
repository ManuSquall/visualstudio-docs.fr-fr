---
title: 'Comment : étendre des plages dans des documents par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 810f65cbb021845c4fa659cd785e83e8c979376d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888669"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Comment : étendre par programmation les plages en documents
  Une fois que vous avez défini un objet <xref:Microsoft.Office.Interop.Word.Range> dans un document Microsoft Office Word, vous modifiez son point de départ et son point de fin à l’aide des méthodes <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> et <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> . Les méthodes <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> et <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> utilisent les deux mêmes arguments, à savoir *Unit* et *Count*. Les méthodes *Count* correspond au nombre d’unités à déplacer, tandis que l’argument *Unit* peut être l’une des valeurs <xref:Microsoft.Office.Interop.Word.WdUnits> suivantes :  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
  L’exemple suivant définit une plage de sept caractères. Il déplace ensuite la position de début de la plage de sept caractères après la position de début d’origine. Étant donné que la position de fin de la plage était également de sept caractères après la position de début, le résultat est une plage composée de zéro caractère. Le code déplace ensuite la position de fin de sept caractères après la position de fin actuelle.  
  
## <a name="to-extend-a-range"></a>Pour étendre une plage  
  
1.  Définissez une plage de caractères. Pour plus d’informations, consultez [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
     Vous pouvez utiliser l’exemple de code suivant dans une personnalisation au niveau du document.  
  
     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]  
  
     L'exemple de code suivant peut être utilisé dans un complément VSTO. Cet exemple utilise le document actif.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]  
  
2.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range> pour déplacer la position de début de la plage.  
  
     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]  
  
3.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range> pour déplacer la position de fin de la plage.  
  
     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]  
  
## <a name="document-level-customization-code"></a>Code de personnalisation au niveau du document  
  
### <a name="to-extend-a-range-in-a-document-level-customization"></a>Pour étendre une plage dans une personnalisation au niveau du document  
  
1.  L'exemple suivant montre le code complet pour une personnalisation au niveau du document. Pour utiliser ce code, exécutez-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]  
  
## <a name="vsto-add-in-code"></a>Code de complément VSTO  
  
### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Pour étendre une plage dans un complément VSTO de niveau application  
  
1.  L’exemple suivant montre le code complet pour un complément VSTO. Pour utiliser ce code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : réinitialiser par programmation des plages dans des documents Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Comment : réduire des plages ou des sélections dans des documents par programmation](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Comment : récupérer par programme des caractères de début et de fin dans les plages](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Comment : exclure les marques de paragraphe par programmation lors de la création de plages](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  