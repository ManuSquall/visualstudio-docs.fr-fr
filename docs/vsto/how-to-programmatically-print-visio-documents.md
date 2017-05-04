---
title: "Comment&#160;: imprimer des documents Visio par programmation | Microsoft Docs"
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
  - "Visio (développement Office dans Visual Studio), impression de documents Visio"
  - "documents (développement Office dans Visual Studio), impression de documents Visio"
ms.assetid: 606a2678-5eb8-40b2-a50a-305cecb1b3d4
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Comment&#160;: imprimer des documents Visio par programmation
  Vous pouvez imprimer un document Microsoft Office Visio complet ou uniquement une page spécifique.  
  
 Pour plus d’informations sur les méthodes d’impression, consultez la documentation de référence de VBA pour la méthode [Microsoft.Office.Interop.Visio.Document.Print](HV10070345) et la méthode [Microsoft.Office.Interop.Visio.Page.Print](HV10070404).  
  
## Impression d’un document Visio  
  
#### Pour imprimer un document complet  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Document.Print de l’objet Microsoft.Office.Interop.Visio.Document à imprimer.  
  
     L’exemple de code suivant imprime le document actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#8)]  
  
## Impression d’une page d’un document Visio  
  
#### Pour imprimer une page d’un document  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Pages.Print de l’objet Microsoft.Office.Interop.Visio.Pages à imprimer.  
  
     L’exemple de code suivant imprime la première page du document actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Vue d'ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)   
 [Comment : créer des documents Visio par programmation](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Comment : ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Comment : fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Comment : enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  