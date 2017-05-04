---
title: "Comment&#160;: imprimer des documents par programmation | Microsoft Docs"
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
  - "Word (développement Office dans Visual Studio), impression de documents"
  - "documents (développement Office dans Visual Studio), impression"
ms.assetid: 99285d98-1bb7-4ccb-83d9-e917b0a9ea42
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Comment&#160;: imprimer des documents par programmation
  Vous pouvez imprimer tout un document Microsoft Office Word, ou seulement une partie, vers votre imprimante par défaut.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Impression d’un document qui fait partie d’une personnalisation au niveau du document  
  
#### Pour imprimer tout le document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> de la classe `ThisDocument` dans votre projet pour imprimer tout le document. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#11)]  
  
#### Pour imprimer la page active du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> de la classe `ThisDocument` dans votre projet et spécifiez l’impression d’une seule copie de la page active. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomation#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#12)]  
  
## Impression d’un document à l’aide d’un complément VSTO  
  
#### Pour imprimer tout un document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Document> à imprimer. L’exemple de code suivant imprime le document actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
#### Pour imprimer la page active d’un document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Document> à imprimer, puis spécifiez l’impression d’une seule copie de la page active. L’exemple de code suivant imprime le document actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## Voir aussi  
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  