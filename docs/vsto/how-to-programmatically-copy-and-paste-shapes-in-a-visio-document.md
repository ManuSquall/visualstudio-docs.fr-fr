---
title: "Comment&#160;: copier et coller des formes dans un document Visio par programmation"
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
  - "formes (développement Office dans Visual Studio), copie et collage de formes Visio"
  - "Visio (développement Office dans Visual Studio), copie et collage de formes Visio"
ms.assetid: 762d95cf-2d5c-4dea-988b-8f4da88fa1f1
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: copier et coller des formes dans un document Visio par programmation
  Vous pouvez copier des formes par programmation sur une page d’un document, et les coller dans une nouvelle page du même document. Vous pouvez choisir de les coller à l’emplacement par défaut \(au centre de la fenêtre active\) ou aux mêmes coordonnées que dans la page d’origine.  
  
## Copie et collage de formes  
 Pour plus d’informations sur le modèle objet, consultez la documentation de référence VBA sur les méthodes [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](HV10070304), [Microsoft.Office.Interop.Visio.Shape.DrawOval](HV10070300), [Microsoft.Office.Interop.Visio.Shape.Copy](HV10070291) et [Microsoft.Office.Interop.Visio.Shape.Paste](HV10070437), ainsi que sur l’indicateur [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](HV10071835).  
  
#### Pour copier des formes au centre d’une autre page  
  
-   L’exemple suivant montre comment copier les formes de la première page, et les coller au centre de la seconde page.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#14)]  
  
## Copie et collage de formes aux mêmes emplacements  
 Pour plus d’informations sur le modèle objet, consultez la documentation de référence VBA sur les méthodes [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](HV10070304), [Microsoft.Office.Interop.Visio.Shape.DrawOval](HV10070300), [Microsoft.Office.Interop.Visio.Shape.Copy](HV10070291) et [Microsoft.Office.Interop.Visio.Shape.Paste](HV10070437), ainsi que sur l’indicateur [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](HV10071835).  
  
 Si vous devez contrôler le format des informations collées et \(éventuellement\) établir un lien vers un fichier source \(par exemple un document Microsoft Office Word\), utilisez la méthode PasteSpecial.  
  
#### Pour copier des formes et des emplacements de forme vers une autre page  
  
-   L’exemple suivant montre comment copier les formes de la première page, et les coller au centre de la seconde page avec leurs coordonnées d’origine.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#15)]  
  
## Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Vue d'ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)   
 [Utilisation de formes Visio](../vsto/working-with-visio-shapes.md)   
 [Comment : ajouter des formes à un document Visio par programmation](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  