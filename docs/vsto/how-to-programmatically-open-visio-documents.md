---
title: "Comment&#160;: ouvrir des documents Visio par programmation | Microsoft Docs"
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
  - "documents (développement Office dans Visual Studio), ouvrir des documents Visio"
  - "Visio (développement Office dans Visual Studio), ouvrir des documents Visio"
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Comment&#160;: ouvrir des documents Visio par programmation
  Il existe deux méthodes pour ouvrir des documents Microsoft Office Visio : Open et OpenEx. La méthode OpenEx est identique à la méthode Open à ceci près qu’elle fournit des arguments dans lesquels l’appelant peut indiquer comment le document doit s’ouvrir.  
  
 Pour plus d’informations sur le modèle objet, consultez la documentation de référence de VBA pour la méthode [Microsoft.Office.Interop.Visio.Documents.Open](HV10070351) et la méthode [Microsoft.Office.Interop.Visio.Documents.OpenEx](HV10071456).  
  
## Ouverture d’un document Visio  
  
#### Pour ouvrir un document Visio  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Documents.Open et fournissez le chemin complet du document Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## Ouverture d’un document Visio avec des arguments spécifiés  
  
#### Pour ouvrir un document Visio en lecture seule et ancré  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Documents.OpenEx, fournissez le chemin complet du document Visio et incluez les arguments à utiliser. Dans le cas présent, Docked et RO \(read\-only, en lecture seule\).  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
## Compilation du code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Un document Visio nommé `myDrawing.vsd` doit se trouver dans un répertoire nommé `Test` du dossier Mes documents \(Windows XP ou version antérieure\) ou du dossier Documents \(Windows Vista\).  
  
## Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Vue d'ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)   
 [Comment : créer des documents Visio par programmation](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Comment : fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Comment : enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Comment : imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  