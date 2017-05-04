---
title: "Comment&#160;: restaurer des s&#233;lections apr&#232;s des recherches par programmation | Microsoft Docs"
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
  - "documents (développement Office dans Visual Studio), restaurer des sélections"
  - "recherches, restaurer une sélection après une"
  - "sélections, restaurer après une recherche"
ms.assetid: 1e6131ad-0e5b-4189-be67-5b2ed87d193d
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Comment&#160;: restaurer des s&#233;lections apr&#232;s des recherches par programmation
  Si vous recherchez et remplacez du texte dans un document, il vous est possible de rétablir la sélection initiale de l'utilisateur une fois la recherche terminée.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Dans l'exemple de procédure, le code utilise deux objets <xref:Microsoft.Office.Interop.Word.Range>.  L'un stocke la <xref:Microsoft.Office.Interop.Word.Selection> actuelle, l'autre définit la totalité du document comme plage de recherche.  
  
### Pour rétablir la sélection initiale de l'utilisateur après une recherche  
  
1.  Créez les objets <xref:Microsoft.Office.Interop.Word.Range> pour le document et la sélection actuelle.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#83](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#83)]
     [!code-vb[Trin_VstcoreWordAutomation#83](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#83)]  
  
2.  Exécutez l'opération de recherche et de remplacement.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#84](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#84)]
     [!code-vb[Trin_VstcoreWordAutomation#84](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#84)]  
  
3.  Sélectionnez la plage de départ pour rétablir la sélection initiale de l'utilisateur.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#85](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#85)]
     [!code-vb[Trin_VstcoreWordAutomation#85](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#85)]  
  
 L'exemple suivant illustre la méthode complète.  
  
## Exemple  
 [!code-csharp[Trin_VstcoreWordAutomation#82](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#82)]
 [!code-vb[Trin_VstcoreWordAutomation#82](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#82)]  
  
## Voir aussi  
 [Comment : rechercher et remplacer du texte dans les documents par programmation](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Comment : définir les options de recherche dans Word par programmation](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Comment : parcourir les éléments trouvés dans les documents par programmation](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  