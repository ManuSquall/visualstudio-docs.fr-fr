---
title: "Comment&#160;: v&#233;rifier l&#39;orthographe dans les feuilles de calcul par programmation | Microsoft Docs"
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
  - "vérification de l'orthographe"
  - "vérificateur d’orthographe, feuilles de calcul"
  - "feuilles de calcul, vérifier l’orthographe"
  - "orthographe, vérifier dans des feuilles de calcul"
ms.assetid: 16367c5d-2075-4174-bb87-dfc59f02c84c
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Comment&#160;: v&#233;rifier l&#39;orthographe dans les feuilles de calcul par programmation
  Vous pouvez vérifier par programmation l’orthographe des mots contenus dans une feuille de calcul. La boîte de dialogue **Orthographe** s’affiche automatiquement si des mots mal orthographiés figurent dans la feuille de calcul.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Pour vérifier l’orthographe d’une feuille de calcul dans une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> de la feuille de calcul.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#45)]  
  
### Pour vérifier l’orthographe d’une feuille de calcul dans un complément VSTO  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> de la feuille de calcul active.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#22)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : exécuter des calculs Excel par programmation](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  