---
title: "Comment&#160;: faire r&#233;f&#233;rence aux plages de la feuille de calcul dans le code par programmation | Microsoft Docs"
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
  - "Excel (développement Office dans Visual Studio), référencer des plages de feuille de calcul"
  - "plages, référencer"
  - "référencer des plages de feuille de calcul"
  - "feuilles de calcul, référencer des plages"
ms.assetid: 113633b8-426a-4d02-b6b8-d459d1f110ea
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Comment&#160;: faire r&#233;f&#233;rence aux plages de la feuille de calcul dans le code par programmation
  Vous utilisez un processus semblable pour faire référence au contenu d'un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> ou d'un objet de plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Utilisation d'un contrôle NamedRange  
 L'exemple suivant ajoute un <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul, puis ajoute du texte à la cellule dans la plage.  
  
#### Pour faire référence à un contrôle NamedRange  
  
1.  Assignez une chaîne à la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> du contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>.  Ce code doit être placé dans une classe sheet et non dans la classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#46)]  
  
## Utilisation de plages Excel natives  
 L'exemple suivant ajoute une plage Excel native à une feuille de calcul, puis ajoute du texte à la cellule dans la plage.  
  
#### Pour faire référence à un objet de plage native  
  
1.  Assignez une chaîne à la <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> de la plage.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#47)]  
  
## Voir aussi  
 [Utilisation des plages](../vsto/working-with-ranges.md)   
 [Comment : vérifier l'orthographe dans les feuilles de calcul par programmation](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Comment : appliquer des styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Comment : remplir automatiquement des plages avec des données soumises à modification incrémentielle par programmation](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Comment : rechercher du texte dans les plages de la feuille de calcul par programmation](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  