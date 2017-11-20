---
title: "Comment : réinitialiser des plages dans Word par programmation des Documents | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
ms.assetid: 45ea9434-e548-4d24-938f-4f1ffa5010d0
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74d144a7a566235ddac1317b51c1e9164247d14c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Comment : réinitialiser des plages dans les documents Word par programmation
  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> pour redimensionner une plage existante dans un document Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-reset-an-existing-range"></a>Pour réinitialiser une plage existante  
  
1.  Définissez une plage initiale commençant par les sept premiers caractères du document.  
  
     Vous pouvez utiliser l’exemple de code suivant dans une personnalisation au niveau du document.  
  
     [!code-vb[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#43)]  
  
     Vous pouvez utiliser l’exemple de code suivant dans un complément VSTO. Ce code utilise le document actif.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#43)]  
  
2.  Utilisez <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> pour commencer la plage au niveau de la deuxième phrase et la terminer à la fin de la cinquième phrase.  
  
     [!code-vb[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#44)]
     [!code-csharp[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#44)]  
  
## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document  
  
#### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Pour réinitialiser une plage existante dans une personnalisation au niveau du document  
  
1.  L’exemple suivant montre le code complet pour une personnalisation au niveau du document. Pour utiliser ce code, exécutez-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#42)]  
  
## <a name="vsto-add-in-example"></a>Exemple de complément VSTO  
  
#### <a name="to-reset-an-existing-range-in-an-vsto-add-in"></a>Pour réinitialiser une plage existante dans un complément VSTO  
  
1.  L’exemple suivant montre le code complet pour un complément VSTO. Pour utiliser ce code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#42)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : étendre des plages dans des Documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Comment : définir par programme et sélectionner des plages dans des Documents](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Comment : récupérer les caractères de début et fin dans les plages par programmation](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Guide pratique pour réduire des plages ou des sélections dans des documents par programmation](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)  
  
  