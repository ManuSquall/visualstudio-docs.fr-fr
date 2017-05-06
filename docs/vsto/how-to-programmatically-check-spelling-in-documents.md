---
title: "Comment&#160;: v&#233;rifier l&#39;orthographe dans les documents par programmation"
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
  - "documents (développement Office dans Visual Studio), vérifier l'orthographe"
  - "vérificateur d'orthographe, documents"
ms.assetid: 5bbe3a8d-fc65-4f57-bd63-5bb549dbc4bd
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Comment&#160;: v&#233;rifier l&#39;orthographe dans les documents par programmation
  Pour vérifier l'orthographe dans un document, utilisez la méthode <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>.  Cette méthode retourne une valeur booléenne indiquant si le paramètre fourni est correctement orthographié.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Pour vérifier l'orthographe et afficher les résultats dans un message  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> et passez\-lui une plage de texte pour laquelle vérifier les fautes d'orthographe.  Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisDocument` ou `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#113](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#113)]
     [!code-vb[Trin_VstcoreWordAutomation#113](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#113)]  
  
## Voir aussi  
 [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  