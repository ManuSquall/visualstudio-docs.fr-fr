---
title: "Comment&#160;: copier des donn&#233;es et une mise en forme d&#39;une feuille de calcul &#224; l&#39;autre par programmation"
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
  - "copier les données, développement Office dans Visual Studio"
  - "données (développement Office dans Visual Studio), copier entre feuilles de calcul"
  - "mettre en forme (développement Office dans Visual Studio)"
  - "feuilles de calcul, copier les données"
ms.assetid: eed7dbaf-bdb5-4330-ba2e-5f3d50817eca
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Comment&#160;: copier des donn&#233;es et une mise en forme d&#39;une feuille de calcul &#224; l&#39;autre par programmation
  Vous pouvez copier les données à partir d'une plage d'une feuille vers toutes les autres feuilles d'un classeur à l'aide de la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A>.  Spécifiez une plage, puis indiquez si vous souhaitez copier les données, la mise en forme ou les deux.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Exemple  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#44)]  
  
## Compilation du code  
 Cet exemple requiert une plage nommée `rangeData` dans une feuille de calcul.  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : ajouter des feuilles de calcul à des classeurs par programmation](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Comment : modifier la mise en forme des lignes de feuille de calcul contenant des cellules sélectionnées par programmation](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  