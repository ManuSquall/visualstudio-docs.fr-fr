---
title: "Comment&#160;: prot&#233;ger des documents et des parties de documents par programmation | Microsoft Docs"
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
  - "protection du document"
  - "documents (développement Office dans Visual Studio), protection des documents"
  - "documents Word, protection"
ms.assetid: af8390fc-c4c7-48c7-94b8-4fedbaac0757
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Comment&#160;: prot&#233;ger des documents et des parties de documents par programmation
  Vous pouvez ajouter une protection aux documents Microsoft Office Word pour empêcher les utilisateurs d’y apporter des modifications.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Vous pouvez également marquer certaines zones du document comme des exceptions, pour que les utilisateurs spécifiés puissent modifier uniquement ces zones du document. Par exemple, vous souhaiterez peut\-être protéger un document entier à l’exception d’un signet particulier. Vous pouvez éventuellement ajouter un mot de passe pour que seuls les utilisateurs qui le connaissent puissent supprimer la protection du document.  
  
> [!NOTE]  
>  L’exemple suivant n’utilise pas de protection par mot de passe. Toutefois, vous pouvez utiliser un mot de passe lors de l’ajout de la protection de document. Pour plus d’informations, consultez l’exemple de protection de document à l’adresse [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 Vous pouvez également utiliser des contrôles de contenu pour protéger certaines parties d’un document. Pour plus d'informations, consultez [Comment : protéger des parties de documents à l'aide de contrôles de contenu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## Protection d’un document qui fait partie d’une personnalisation au niveau du document  
  
#### Pour protéger un document qui fait partie d’une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> de la classe `ThisDocument` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
#### Pour exclure un contrôle Bookmark de la protection de document  
  
1.  Protégez le document entier à l’aide de la méthode <xref:Microsoft.Office.Tools.Word.Document.Protect%2A>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
2.  Excluez `Bookmark1` de la protection de document.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#112](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#112)]
     [!code-vb[Trin_VstcoreWordAutomation#112](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#112)]  
  
### Compilation du code  
 Pour utiliser ces exemples de code, exécutez\-les à partir de la classe `ThisDocument` de votre projet. Ces exemples de code partent du principe qu’il existe un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> nommé `Bookmark1` dans le document dans lequel ce code apparaît.  
  
## Protection d’un document à l’aide d’un complément VSTO  
  
#### Pour protéger un document à l’aide d’un complément VSTO de niveau application  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> du <xref:Microsoft.Office.Interop.Word.Document> que vous souhaitez protéger.  
  
     L’exemple de code suivant protège le document actif. Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#111)]  
  
## Voir aussi  
 [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)   
 [Protection par mot de passe des documents Office](../vsto/password-protection-on-office-documents.md)   
 [Comment : permettre au code de s'exécuter derrière des documents dotés d'autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  