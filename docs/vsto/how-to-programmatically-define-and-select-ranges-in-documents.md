---
title: "Comment&#160;: d&#233;finir et s&#233;lectionner des plages dans les documents par programmation | Microsoft Docs"
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
  - "documents (développement Office dans Visual Studio), plages"
  - "documents (développement Office dans Visual Studio), sélectionner des phrases"
  - "plages, définir dans des documents"
  - "plages, sélectionner dans des documents"
  - "phrases, sélectionner dans des documents"
ms.assetid: 0727c1cb-d44c-4f1c-a699-4365dd13be5d
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Comment&#160;: d&#233;finir et s&#233;lectionner des plages dans les documents par programmation
  Vous pouvez définir une plage dans un document Microsoft Office Word en utilisant un objet <xref:Microsoft.Office.Interop.Word.Range>.  Vous pouvez sélectionner la totalité du document d'un certain nombre de façons, par exemple, à l'aide de la méthode <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Range>, ou en utilisant la propriété Content de la classe <xref:Microsoft.Office.Tools.Word.Document> \(dans une personnalisation au niveau du document\) ou de la classe <xref:Microsoft.Office.Interop.Word.Document> \(dans un complément VSTO\).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Définition d'une plage  
 L'exemple suivant montre comment créer un objet <xref:Microsoft.Office.Interop.Word.Range> incluant les sept premiers caractères du document actif, y compris les caractères non imprimables.  Puis, il sélectionne le texte dans la plage.  
  
#### Pour définir une plage dans une personnalisation au niveau du document  
  
1.  Ajoutez la plage au document en passant un caractère de début et de fin à la méthode <xref:Microsoft.Office.Tools.Word.Document.Range%2A> de la classe <xref:Microsoft.Office.Tools.Word.Document>.  Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#18)]  
  
#### Pour définir une plage en utilisant un complément VSTO  
  
1.  Ajoutez la plage au document en passant un caractère de début et de fin à la méthode <xref:Microsoft.Office.Interop.Word._Document.Range%2A> de la classe <xref:Microsoft.Office.Interop.Word.Document>.  L'exemple de code suivant ajoute une plage au document actif.  Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## Sélection d'une plage dans une personnalisation au niveau du document  
 Les exemples suivants montrent comment sélectionner le document entier à l'aide de la méthode <xref:Microsoft.Office.Interop.Word.Range.Select%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Range> ou de la propriété <xref:Microsoft.Office.Tools.Word.Document.Content%2A> de la classe <xref:Microsoft.Office.Tools.Word.Document>.  
  
#### Pour sélectionner la totalité du document comme plage à l'aide de la méthode Select  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Range.Select%2A> d'un <xref:Microsoft.Office.Interop.Word.Range>qui contient la totalité du document.  Pour utiliser l'exemple de code suivant, exécutez\-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#19)]  
  
#### Pour sélectionner la totalité du document comme plage à l'aide de la propriété Content  
  
1.  Utilisez la propriété <xref:Microsoft.Office.Tools.Word.Document.Content%2A> pour définir une plage qui englobe la totalité du document.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#20)]  
  
 Vous pouvez également utiliser les méthodes et les propriétés d'autres objets pour définir une plage.  
  
#### Pour sélectionner une phrase dans le document actif  
  
1.  Définissez la plage à l'aide de la collection <xref:Microsoft.Office.Interop.Word.Sentences>.  Utilisez l'index de la phrase que vous souhaitez sélectionner.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#21)]  
  
 Une autre façon de sélectionner une phrase consiste à définir manuellement les valeurs de début et de fin de la plage.  
  
#### Pour sélectionner une phrase en définissant manuellement les valeurs de début et de fin  
  
1.  Créez une variable de plage.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#23)]  
  
2.  Vérifiez s'il existe au moins deux phrases dans le document, définissez les arguments *Start* et *End* de la plage, puis sélectionnez la plage.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomation#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#24)]  
  
## Sélection d'une plage à l'aide d'un complément VSTO  
 Les exemples suivants montrent comment sélectionner le document entier à l'aide de la méthode <xref:Microsoft.Office.Interop.Word.Range.Select%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Range> ou de la propriété <xref:Microsoft.Office.Interop.Word._Document.Content%2A> de la classe <xref:Microsoft.Office.Interop.Word.Document>.  
  
#### Pour sélectionner la totalité du document comme plage à l'aide de la méthode Select  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Range.Select%2A> d'un <xref:Microsoft.Office.Interop.Word.Range>qui contient la totalité du document.  L'exemple de code suivant sélectionne le contenu du document actif.  Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
#### Pour sélectionner la totalité du document comme plage à l'aide de la propriété Content  
  
1.  Utilisez la propriété <xref:Microsoft.Office.Interop.Word._Document.Content%2A> pour définir une plage qui englobe la totalité du document.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
 Vous pouvez également utiliser les méthodes et les propriétés d'autres objets pour définir une plage.  
  
#### Pour sélectionner une phrase dans le document actif  
  
1.  Définissez la plage à l'aide de la collection <xref:Microsoft.Office.Interop.Word.Sentences>.  Utilisez l'index de la phrase que vous souhaitez sélectionner.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
 Une autre façon de sélectionner une phrase consiste à définir manuellement les valeurs de début et de fin de la plage.  
  
#### Pour sélectionner une phrase en définissant manuellement les valeurs de début et de fin  
  
1.  Créez une variable de plage.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
2.  Vérifiez s'il existe au moins deux phrases dans le document, définissez les arguments *Start* et *End* de la plage, puis sélectionnez la plage.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## Voir aussi  
 [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md)   
 [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Comment : récupérer les caractères de début et de fin dans les plages par programmation](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Comment : réinitialiser des plages dans les documents Word par programmation](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Comment : réduire des plages ou des sélections dans des documents par programmation](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Comment : exclure les marques de paragraphe lors de la création de plages par programmation](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  