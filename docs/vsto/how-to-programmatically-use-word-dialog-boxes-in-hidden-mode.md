---
title: "Comment&#160;: utiliser des bo&#238;tes de dialogue Word en mode masqu&#233; par programmation | Microsoft Docs"
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
  - "boîtes de dialogue, mode masqué dans Word"
  - "boîtes de dialogue masquées"
  - "Word (développement Office dans Visual Studio), boîtes de dialogue"
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Comment&#160;: utiliser des bo&#238;tes de dialogue Word en mode masqu&#233; par programmation
  Vous pouvez effectuer des opérations complexes à l'aide d'un seul appel de méthode en appelant les boîtes de dialogue intégrées dans Microsoft Office Word sans les afficher à l'utilisateur.  Pour ce faire, utilisez la méthode <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Dialog> sans appeler la méthode <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Exemples  
 Les exemples de code suivants montrent comment utiliser la boîte de dialogue **Mise en page** en mode masqué pour définir plusieurs propriétés de mise en page sans entrée d'utilisateur.  Ces exemples utilisent un objet <xref:Microsoft.Office.Interop.Word.Dialog> pour configurer une taille de page personnalisée.  Les paramètres spécifiques pour la mise en page, tels que les paramètres de marge supérieure, marge inférieure, etc., sont disponibles en tant que propriétés à liaison tardive de l'objet <xref:Microsoft.Office.Interop.Word.Dialog>.  Ces propriétés sont créées dynamiquement par Word au moment de l'exécution.  
  
 L'exemple suivant montre comment effectuer cette tâche dans les projets Visual Basic dans lesquels **Option Strict** est désactivé et dans les projets Visual C\# qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  Dans ces projets, vous pouvez utiliser des fonctionnalités de liaison tardive dans les compilateurs Visual C\# et Visual Basic.  Pour utiliser cet exemple de code, exécutez\-le dans votre projet à partir de la classe `ThisDocument` ou `ThisAddIn`.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#123](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#123)]
 [!code-vb[Trin_VstcoreWordAutomation#123](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#123)]  
  
 L'exemple suivant montre comment effectuer cette tâche dans les projets Visual Basic où **Option Strict** est activé.  Dans ces projets, vous devez utiliser la réflexion pour accéder aux propriétés à liaison tardive.  Pour utiliser cet exemple de code, exécutez\-le dans votre projet à partir de la classe `ThisDocument` ou `ThisAddIn`.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#104)]  
  
## Voir aussi  
 [Comment : utiliser les boîtes de dialogue intégrées dans Word par programmation](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md)   
 [Liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md)   
 [Réflexion &#40;C&#35; et Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
  
  