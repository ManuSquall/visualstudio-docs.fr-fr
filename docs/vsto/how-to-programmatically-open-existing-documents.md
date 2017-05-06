---
title: "Comment&#160;: ouvrir des documents existants par programmation"
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
  - "documents (développement Office dans Visual Studio), ouvrir"
  - "Word (développement Office dans Visual Studio), ouvrir des documents"
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Comment&#160;: ouvrir des documents existants par programmation
  La méthode <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> ouvre le document Microsoft Office Word existant spécifié par un chemin d'accès complet et un nom de fichier.  Cette méthode retourne un <xref:Microsoft.Office.Interop.Word.Document> qui représente le document ouvert.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Pour ouvrir un document  
  
-   Appelez la méthode <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> de la collection <xref:Microsoft.Office.Interop.Word.Documents> et fournissez un chemin d'accès au document.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreWordAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#5)]  
  
### Pour ouvrir un document en lecture seule  
  
-   Appelez la méthode <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>, fournissez un chemin d'accès au document et attribuez à l'argument *ReadOnly* la valeur **True** dans l'appel de méthode.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreWordAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#6)]  
  
## Compilation du code  
 Cet exemple de code nécessite ce qui suit :  
  
-   Un document nommé NouveauDocument.doc doit exister dans un répertoire Test sur le lecteur C.  
  
## Voir aussi  
 [Comment : créer des documents par programmation](../vsto/how-to-programmatically-create-new-documents.md)   
 [Comment : fermer des documents par programmation](../vsto/how-to-programmatically-close-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  