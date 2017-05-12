---
title: "Comment&#160;: cr&#233;er des documents par programmation"
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
  - "documents (développement Office dans Visual Studio), créer"
  - "modèles (développement Office dans Visual Studio), document personnalisé"
  - "Word (développement Office dans Visual Studio), créer des documents"
ms.assetid: c24bb8a3-1303-438e-9b33-ba8b00b29c3b
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Comment&#160;: cr&#233;er des documents par programmation
  Quand vous créez un document par programmation, le nouveau document est un objet <xref:Microsoft.Office.Interop.Word.Document>natif.  Cet objet ne possède pas les fonctionnalités de liaison de données et les événements supplémentaires d'un élément hôte <xref:Microsoft.Office.Tools.Word.Document>.  Pour plus d'informations, consultez [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Quand vous développez un projet au niveau du document, vous ne pouvez pas ajouter par programmation d'éléments hôtes <xref:Microsoft.Office.Tools.Word.Document> à votre projet.  Dans un projet de complément VSTO, vous pouvez convertir tout objet <xref:Microsoft.Office.Interop.Word.Document> en un élément hôte <xref:Microsoft.Office.Tools.Word.Document> au moment de l'exécution.  Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### Pour créer un nouveau document basé sur le modèle Normal  
  
-   Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> de la collection <xref:Microsoft.Office.Interop.Word.Documents> pour créer un nouveau document basé sur le modèle Normal.  Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreWordAutomation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#1)]  
  
## Utilisation de modèles personnalisés  
 La méthode <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> possède un argument *Template* facultatif pour créer un nouveau document basé sur un modèle autre que le modèle Normal.  Vous devez fournir le nom de fichier et le chemin d'accès complet du modèle.  
  
#### Pour créer un nouveau document basé sur un modèle personnalisé  
  
-   Appelez la méthode <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> de la collection <xref:Microsoft.Office.Interop.Word.Documents> et spécifiez le chemin d'accès au modèle.  Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreWordAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#2)]  
  
## Voir aussi  
 [Comment : ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  