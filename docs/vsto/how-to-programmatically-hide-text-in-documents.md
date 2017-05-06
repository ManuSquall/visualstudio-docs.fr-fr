---
title: "Comment&#160;: masquer du texte dans des documents par programmation"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "documents (développement Office dans Visual Studio), masquer le texte"
  - "texte (développement Office dans Visual Studio), masquer dans les documents"
ms.assetid: f5ced4ec-22ca-463b-b963-d34ce631b486
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Comment&#160;: masquer du texte dans des documents par programmation
  Vous pouvez masquer du texte dans un document en définissant la propriété <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> de <xref:Microsoft.Office.Interop.Word.Range.Font%2A> pour une plage de texte particulière.  
  
 Par exemple, vous pouvez masquer temporairement le texte dans un <xref:Microsoft.Office.Tools.Word.Bookmark> \(dans une personnalisation au niveau du document\) ou un <xref:Microsoft.Office.Interop.Word.Bookmark> \(dans un complément VSTO\) avant d’envoyer un document à une imprimante.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Pour masquer du texte dans un contrôle Bookmark pendant l’impression du document  
  
1.  Créez une procédure qui masque tout le texte figurant dans une plage spécifiée.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#105](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#105)]
     [!code-vb[Trin_VstcoreWordAutomation#105](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#105)]  
  
2.  Créez une procédure qui affiche tout le texte figurant dans une plage spécifiée.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#106](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#106)]
     [!code-vb[Trin_VstcoreWordAutomation#106](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#106)]  
  
3.  Passez la plage d’un signet à la méthode `HideText`, imprimez le document, puis passez la même plage à la méthode `UnhideText`.  
  
     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document. Pour utiliser cet exemple, exécutez\-le à partir de la classe `ThisDocument` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#107](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#107)]
     [!code-vb[Trin_VstcoreWordAutomation#107](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#107)]  
  
     Vous pouvez utiliser l’exemple de code suivant dans un complément VSTO. Cet exemple utilise le document actif. Pour utiliser l'exemple, exécutez\-le à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#107)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#107)]  
  
## Compilation du code  
 Cet exemple de code suppose que le document contient un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> \(dans une personnalisation au niveau du document\) ou un contrôle <xref:Microsoft.Office.Interop.Word.Bookmark> \(dans un complément VSTO\) nommé `bookmark1`.  
  
## Voir aussi  
 [Comment : imprimer des documents par programmation](../vsto/how-to-programmatically-print-documents.md)   
 [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Comment : réinitialiser des plages dans les documents Word par programmation](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Comment : mettre à jour le texte d'un signet par programmation](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  