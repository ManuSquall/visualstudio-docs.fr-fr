---
title: "Comment&#160;: supprimer tous les commentaires des documents par programmation"
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
  - "documents (développement Office dans Visual Studio), suppression des commentaires"
  - "commentaires, suppression des documents"
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Comment&#160;: supprimer tous les commentaires des documents par programmation
  Utilisez la méthode DeleteAllComments pour supprimer tous les commentaires d’un document Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Pour supprimer tous les commentaires d’un document qui fait partie d’une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> de la classe `ThisDocument` dans votre projet. Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomation#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#119)]  
  
### Pour supprimer tous les commentaires d’un document à l’aide d’un complément VSTO  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> du <xref:Microsoft.Office.Interop.Word.Document> à partir duquel vous souhaitez supprimer les commentaires.  
  
     L’exemple de code suivant supprime tous les commentaires du document actif. Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#119)]  
  
## Voir aussi  
 [Comment : ajouter des commentaires à du texte dans des documents par programmation](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Élément hôte de document](../vsto/document-host-item.md)  
  
  