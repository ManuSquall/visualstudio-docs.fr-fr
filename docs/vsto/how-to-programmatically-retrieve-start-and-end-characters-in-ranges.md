---
title: "Comment&#160;: r&#233;cup&#233;rer les caract&#232;res de d&#233;but et de fin dans les plages par programmation"
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
  - "plages, récupération des caractères de début et de fin"
  - "caractères de fin"
  - "caractères de début"
  - "documents (développement Office dans Visual Studio), récupération de plages"
ms.assetid: 734c630c-abc9-491d-94b6-429d1fc7a4cc
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Comment&#160;: r&#233;cup&#233;rer les caract&#232;res de d&#233;but et de fin dans les plages par programmation
  Cet exemple montre comment vous pouvez récupérer les positions de début et de fin des caractères d’une plage.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Pour récupérer les caractères de début et de fin d’une plage dans une personnalisation au niveau du document  
  
1.  Obtenez les valeurs des propriétés <xref:Microsoft.Office.Interop.Word.Range.Start%2A> et <xref:Microsoft.Office.Interop.Word.Range.End%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range>. L’exemple de code suivant obtient la position de début et de fin de la deuxième phrase du document. Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#25)]  
  
### Pour récupérer les caractères de début et de fin d’une plage en utilisant un complément VSTO  
  
1.  Obtenez les valeurs des propriétés <xref:Microsoft.Office.Interop.Word.Range.Start%2A> et <xref:Microsoft.Office.Interop.Word.Range.End%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range>. L’exemple de code suivant obtient la position de début et de fin de la deuxième phrase du document actif. Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
## Voir aussi  
 [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Comment : réinitialiser des plages dans les documents Word par programmation](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Comment : réduire des plages ou des sélections dans des documents par programmation](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Comment : exclure les marques de paragraphe lors de la création de plages par programmation](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Comment : compter des caractères dans les documents par programmation](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  