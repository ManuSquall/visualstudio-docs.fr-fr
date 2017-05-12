---
title: "Comment&#160;: mettre en forme du texte dans des documents par programmation"
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
  - "mettre en forme (développement Office dans Visual Studio)"
  - "documents (développement Office dans Visual Studio), mettre en forme du texte"
  - "texte (développement Office dans Visual Studio), mettre en forme dans des documents"
ms.assetid: 0a84893b-5ccc-4515-a2dc-95773ee8eaba
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Comment&#160;: mettre en forme du texte dans des documents par programmation
  Vous pouvez utiliser l'objet <xref:Microsoft.Office.Interop.Word.Range> pour mettre en forme le texte dans un document Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L'exemple suivant sélectionne le premier paragraphe du document et modifie la taille de la police, le nom de la police et l'alignement. Ensuite, il sélectionne la plage et affiche un message d'interruption avant l'exécution de la section de code suivante. La section suivante appelle la méthode Undo de l'élément hôte <xref:Microsoft.Office.Tools.Word.Document> \(pour une personnalisation au niveau du document\) ou la classe <xref:Microsoft.Office.Interop.Word.Document> \(pour un complément VSTO\) trois fois. Il applique le style Retrait normal et affiche un message permettant de suspendre le code. Puis, le code appelle la méthode <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> une seule fois et affiche un message.  
  
## Exemple de personnalisation au niveau du document  
  
#### Pour mettre en forme un texte à l'aide d'une personnalisation au niveau du document  
  
1.  L'exemple suivant peut être utilisé dans une personnalisation au niveau du document. Pour utiliser ce code, exécutez\-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#62)]  
  
## Exemple de complément VSTO  
  
#### Pour mettre en forme du texte avec un complément VSTO  
  
1.  L’exemple suivant peut être utilisé dans un complément VSTO. Cet exemple utilise le document actif. Pour utiliser ce code, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#62)]  
  
## Voir aussi  
 [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Comment : insérer du texte dans les documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Comment : rechercher et remplacer du texte dans les documents par programmation](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  