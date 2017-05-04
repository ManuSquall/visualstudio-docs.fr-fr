---
title: "Comment&#160;: afficher des documents en mode Aper&#231;u avant impression par programmation | Microsoft Docs"
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
  - "Word (développement Office dans Visual Studio), affichage des documents en mode Aperçu avant impression"
  - "documents (développement Office dans Visual Studio), affichage en mode Aperçu avant impression"
ms.assetid: 96c7faea-9c5c-42b4-a009-08894a6d15c9
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Comment&#160;: afficher des documents en mode Aper&#231;u avant impression par programmation
  Si votre solution génère un rapport, vous pouvez afficher ce dernier pour l’utilisateur en mode Aperçu avant impression.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Procédures pour les personnalisations au niveau du document  
  
#### Pour afficher un document en mode Aperçu avant impression en appelant la méthode PrintPreview  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> de la classe <xref:Microsoft.Office.Tools.Word.Document>. Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomation#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#13)]  
  
#### Pour afficher un document en mode Aperçu avant impression en définissant la propriété PrintPreview  
  
1.  Affectez la valeur <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> à la propriété <xref:Microsoft.Office.Interop.Word.Application> de l'objet **true**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## Procédures pour les compléments VSTO  
  
#### Pour afficher un document en mode Aperçu avant impression en appelant la méthode PrintPreview  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> du <xref:Microsoft.Office.Interop.Word.Document> dont vous souhaitez afficher l’aperçu. Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
#### Pour afficher un document en mode Aperçu avant impression en définissant la propriété PrintPreview  
  
1.  Affectez la valeur <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> à la propriété <xref:Microsoft.Office.Interop.Word.Application> de l'objet **true**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## Voir aussi  
 [Comment : imprimer des documents par programmation](../vsto/how-to-programmatically-print-documents.md)   
 [Comment : ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Comment : créer des documents par programmation](../vsto/how-to-programmatically-create-new-documents.md)  
  
  