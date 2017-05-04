---
title: "Comment&#160;: utiliser les bo&#238;tes de dialogue int&#233;gr&#233;es dans Word par programmation | Microsoft Docs"
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
  - "Word (développement Office dans Visual Studio), boîtes de dialogue"
  - "boîtes de dialogue, Word"
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Comment&#160;: utiliser les bo&#238;tes de dialogue int&#233;gr&#233;es dans Word par programmation
  Lorsque vous utilisez Microsoft Office Word, vous devez parfois afficher des boîtes de dialogue pour permettre la saisie de données par vos utilisateurs.  Vous pouvez choisir de créer vos propres boîtes de dialogue ou d'utiliser celles qui sont intégrées dans Word et exposées dans la collection <xref:Microsoft.Office.Interop.Word.Dialogs> de l'objet <xref:Microsoft.Office.Interop.Word.Application>.  Cela vous permet d'accéder à plus de 200 boîtes de dialogue intégrées, représentées comme des énumérations.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Affichage des boîtes de dialogue  
 Pour afficher une boîte de dialogue, utilisez l'une des valeurs de l'énumération <xref:Microsoft.Office.Interop.Word.WdWordDialog> afin de créer un objet <xref:Microsoft.Office.Interop.Word.Dialog> qui représente la boîte de dialogue à afficher.  Appelez ensuite la méthode <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Dialog>.  
  
 L'exemple de code suivant montre comment afficher la boîte de dialogue **Ouvrir**.  Pour utiliser cet exemple de code, exécutez\-le dans votre projet à partir de la classe `ThisDocument` ou `ThisAddIn`.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#100](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreWordAutomation#100](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#100)]  
  
### Accès aux membres de boîte de dialogue disponibles via une liaison tardive  
 Certaines propriétés et méthodes des boîtes de dialogue dans Word sont uniquement disponibles via liaison tardive.  Dans les projets Visual Basic où **Option Strict** est activé, vous devez utiliser la réflexion pour accéder à ces membres.  Pour plus d'informations, consultez [Liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md).  
  
 L'exemple de code suivant montre comment utiliser la propriété d' **Name** de la boîte de dialogue **Ouvrir** dans les projets Visual Basic en dehors de l' **Option Strict** est activé ou dans les projets Visual c qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)].  Pour utiliser cet exemple de code, exécutez\-le dans votre projet à partir de la classe `ThisDocument` ou `ThisAddIn`.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 L'exemple de code suivant montre comment utiliser la réflexion pour accéder à la propriété d' **Name** de la boîte de dialogue **Ouvrir** dans les projets Visual Basic où **Option Strict** est activé.  Pour utiliser cet exemple de code, exécutez\-le dans votre projet à partir de la classe `ThisDocument` ou `ThisAddIn`.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## Voir aussi  
 [Comment : utiliser des boîtes de dialogue Word en mode masqué par programmation](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Réflexion &#40;C&#35; et Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
  
  