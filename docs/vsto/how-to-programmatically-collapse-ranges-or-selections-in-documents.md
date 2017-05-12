---
title: "Comment&#160;: r&#233;duire des plages ou des s&#233;lections dans des documents par programmation"
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
  - "sélections, réduire"
  - "documents (développement Office dans Visual Studio), réduire des plages"
  - "réduire des sélections"
  - "plages, réduire"
  - "réduire des plages"
ms.assetid: 0bd059dd-8606-42ae-a8a9-97f8f3bd5cc5
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Comment&#160;: r&#233;duire des plages ou des s&#233;lections dans des documents par programmation
  Si vous travaillez avec un objet <xref:Microsoft.Office.Interop.Word.Range> ou <xref:Microsoft.Office.Interop.Word.Selection>, vous pouvez remplacer la sélection par un point d’insertion avant d’insérer du texte, afin d’éviter de remplacer le texte existant. Les objets <xref:Microsoft.Office.Interop.Word.Range> et <xref:Microsoft.Office.Interop.Word.Selection> ont tous les deux une méthode Collapse qui utilise les valeurs d’énumération <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> :  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> réduit la sélection au début de la sélection. Il s’agit de la valeur par défaut si vous ne spécifiez pas de valeur d’énumération.  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> réduit la sélection à la fin de la sélection.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Pour réduire une plage et insérer un nouveau texte  
  
1.  Créez un objet <xref:Microsoft.Office.Interop.Word.Range> constitué du premier paragraphe du document.  
  
     L’exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#46)]
     [!code-vb[Trin_VstcoreWordAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#46)]  
  
     L’exemple de code suivant peut être utilisé dans une personnalisation dans un complément VSTO. Ce code utilise le document actif.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#46)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#46)]  
  
2.  Utilisez la valeur d’énumération <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> pour réduire la plage.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#47)]
     [!code-vb[Trin_VstcoreWordAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#47)]  
  
3.  Insérez le nouveau texte.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#48](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#48)]
     [!code-vb[Trin_VstcoreWordAutomation#48](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#48)]  
  
4.  Sélectionnez le contrôle <xref:Microsoft.Office.Interop.Word.Range>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#49)]
     [!code-vb[Trin_VstcoreWordAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#49)]  
  
 Si vous utilisez la valeur d’énumération <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd>, le texte est inséré au début du paragraphe suivant.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#50)]
 [!code-vb[Trin_VstcoreWordAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#50)]  
  
 Vous pourriez vous attendre à ce que l’insertion d’une nouvelle phrase se fasse avant la marque de paragraphe, mais ce n’est pas le cas, car celle\-ci est incluse dans la plage d’origine. Pour plus d'informations, consultez [Comment : exclure les marques de paragraphe lors de la création de plages par programmation](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).  
  
## Exemple de personnalisation au niveau du document  
  
#### Pour réduire une plage dans une personnalisation au niveau du document  
  
1.  L’exemple suivant affiche la méthode complète correspondant à la personnalisation au niveau du document. Pour utiliser ce code, exécutez\-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#45)]
     [!code-vb[Trin_VstcoreWordAutomation#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#45)]  
  
## Exemple de complément VSTO  
  
#### Pour réduire une plage dans un complément VSTO  
  
1.  L’exemple suivant affiche la méthode complète correspondant à un complément VSTO. Pour utiliser ce code, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#45)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#45)]  
  
## Voir aussi  
 [Comment : insérer du texte dans les documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Comment : récupérer les caractères de début et de fin dans les plages par programmation](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Comment : exclure les marques de paragraphe lors de la création de plages par programmation](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Comment : réinitialiser des plages dans les documents Word par programmation](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
  
  