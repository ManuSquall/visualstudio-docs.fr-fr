---
title: "Comment&#160;: compter des caract&#232;res dans les documents par programmation"
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
  - "caractères, compter dans des documents"
  - "compter des caractères dans des documents"
  - "documents (développement Office dans Visual Studio), compter des caractères"
ms.assetid: ab64fe87-896a-4b56-bdf8-91c4326b540e
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Comment&#160;: compter des caract&#232;res dans les documents par programmation
  Le premier caractère dans un document est à la position de caractère 0, qui représente le point d’insertion. La position du dernier caractère est égale au nombre total de caractères dans le document. Vous pouvez déterminer le nombre de caractères dans un document à l’aide de la propriété <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> de la collection <xref:Microsoft.Office.Interop.Word.Characters>.  
  
 Tous les caractères du document sont comptés, y compris les espaces, les marques de paragraphe et autres caractères normalement masqués. Même un document vide retourne un nombre de caractères égal à « 1 », car il contient une marque de paragraphe.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Pour afficher le nombre de caractères dans une personnalisation au niveau du document  
  
1.  Sélectionnez tout le document.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#98](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#98)]
     [!code-vb[Trin_VstcoreWordAutomation#98](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#98)]  
  
2.  Affichez le nombre de caractères dans le document dans une boîte de message.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#99](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#99)]
     [!code-vb[Trin_VstcoreWordAutomation#99](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#99)]  
  
### Pour afficher le nombre de caractères dans un complément VSTO  
  
1.  Sélectionnez tout le document. L’exemple suivant sélectionne le document actif.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#98)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#98)]  
  
2.  Affichez le nombre de caractères dans le document dans une boîte de message.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#99)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#99)]  
  
## Voir aussi  
 [Comment : récupérer les caractères de début et de fin dans les plages par programmation](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
  
  