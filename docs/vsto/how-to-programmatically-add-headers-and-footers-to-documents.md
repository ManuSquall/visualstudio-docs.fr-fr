---
title: "Comment&#160;: ajouter des en-t&#234;tes et des pieds de page aux documents par programmation | Microsoft Docs"
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
  - "documents (développement Office dans Visual Studio), ajouter des pieds de page"
  - "documents (développement Office dans Visual Studio), ajouter des en-têtes"
  - "pieds de page, ajouter à des documents"
  - "en-têtes, ajouter à des documents Office"
ms.assetid: c7a5cc8a-d8c0-48e9-81d3-108aa6bfbb74
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Comment&#160;: ajouter des en-t&#234;tes et des pieds de page aux documents par programmation
  Vous pouvez ajouter du texte aux en\-têtes et pieds de page dans votre document à l'aide de la propriété <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> et de la propriété <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> de <xref:Microsoft.Office.Interop.Word.Section>.  Chaque section d'un document contient trois en\-têtes et pieds de page :  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 Les procédures sont différentes pour les personnalisations au niveau du document et les compléments VSTO.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Personnalisations au niveau du document  
 Pour utiliser les exemples de code suivants, exécutez\-les à partir de la classe `ThisDocument` de votre projet.  
  
#### Pour ajouter du texte dans les pieds de page du document  
  
1.  L'exemple de code suivant définit la police du texte à insérer dans le pied de page principal de chaque section du document, puis insère le texte dans le pied de page.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#114](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#114)]
     [!code-vb[Trin_VstcoreWordAutomation#114](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#114)]  
  
#### Pour ajouter du texte dans les en\-têtes du document  
  
1.  L'exemple de code suivant ajoute un champ pour afficher le numéro de page dans chaque en\-tête du document, puis définit l'alignement du paragraphe afin d'aligner le texte à droite de l'en\-tête.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#116](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#116)]
     [!code-vb[Trin_VstcoreWordAutomation#116](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#116)]  
  
## Compléments VSTO  
 Pour utiliser les exemples de code suivants, exécutez\-les à partir de la classe `ThisAddIn` de votre projet.  
  
#### Pour ajouter du texte dans les pieds de page d'un document  
  
1.  L'exemple de code suivant définit la police du texte à insérer dans le pied de page principal de chaque section du document, puis insère le texte dans le pied de page.  Cet exemple de code utilise le document actif.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#114)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#114)]  
  
#### Pour ajouter du texte dans les en\-têtes du document  
  
1.  L'exemple de code suivant ajoute un champ pour afficher le numéro de page dans chaque en\-tête du document, puis définit l'alignement du paragraphe afin d'aligner le texte à droite de l'en\-tête.  Cet exemple de code utilise le document actif.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#116)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#116)]  
  
## Voir aussi  
 [Comment : créer des documents par programmation](../vsto/how-to-programmatically-create-new-documents.md)   
 [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Comment : parcourir les éléments trouvés dans les documents par programmation](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
  
  