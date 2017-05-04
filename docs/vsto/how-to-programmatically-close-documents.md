---
title: "Comment&#160;: fermer des documents par programmation | Microsoft Docs"
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
  - "documents (développement Office dans Visual Studio), fermer"
  - "Word (développement Office dans Visual Studio), fermer les documents"
ms.assetid: d5bee1dc-63d1-4307-828f-b7b077e20fb9
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Comment&#160;: fermer des documents par programmation
  Vous pouvez fermer le document actif ou spécifier un document à fermer.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Fermeture du document actif  
 Il existe deux procédures distinctes pour fermer le document actif : une pour les personnalisations au niveau du document et une autre pour les compléments VSTO.  
  
#### Pour fermer le document actif dans une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.Close%2A> de la classe `ThisDocument` dans votre projet pour fermer le document associé à la personnalisation. Pour utiliser l'exemple de code suivant, exécutez\-le à partir de la classe `ThisDocument`.  
  
    > [!NOTE]  
    >  Cet exemple transmet la valeur <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> au paramètre *SaveChanges* afin de fermer sans enregistrement des modifications apportées ou sans validation de l'utilisateur.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomation#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#3)]  
  
#### Pour fermer le document actif dans un complément VSTO  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.Close%2A> de la propriété <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> pour fermer le document actif. Pour utiliser l'exemple de code suivant, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
    > [!NOTE]  
    >  Cet exemple transmet la valeur <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> au paramètre *SaveChanges* afin de fermer sans enregistrement des modifications apportées ou sans validation de l'utilisateur.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Fermeture d'un document dont vous spécifiez le nom  
 La procédure de fermeture d’un document dont vous spécifiez le nom est la même pour les compléments VSTO et les personnalisations au niveau du document.  
  
#### Pour fermer un document dont vous spécifiez le nom  
  
1.  Spécifiez le nom du document comme argument à la collection <xref:Microsoft.Office.Interop.Word._Application.Documents%2A>, puis appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.Close%2A>. L’exemple de code suivant suppose qu’un document nommé **NewDocument** est ouvert dans Word.  
  
    > [!NOTE]  
    >  Cet exemple transmet la valeur <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> au paramètre *SaveChanges* afin de fermer sans enregistrement des modifications apportées ou sans validation de l'utilisateur.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreWordAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#4)]  
  
## Voir aussi  
 [Comment : ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Comment : enregistrer des documents par programmation](../vsto/how-to-programmatically-save-documents.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  