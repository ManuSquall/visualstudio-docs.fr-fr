---
title: "Comment&#160;: d&#233;placer des feuilles de calcul dans les classeurs par programmation | Microsoft Docs"
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
  - "feuilles de calcul, déplacement"
  - "classeurs, déplacement de feuilles de calcul dans"
ms.assetid: a010a633-412e-4299-9587-cacb035842c1
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Comment&#160;: d&#233;placer des feuilles de calcul dans les classeurs par programmation
  Vous pouvez modifier par programmation la position des feuilles de calcul les unes par rapport aux autres dans un classeur. Si vous ne spécifiez pas d’emplacement pour la feuille déplacée, Excel crée un classeur pour le contenir.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Pour déplacer une feuille de calcul dans une personnalisation au niveau du document  
  
1.  Affectez le nombre total de feuilles dans le classeur à une variable, puis déplacez la première feuille de calcul pour qu’elle devienne la dernière.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#24)]  
  
### Pour déplacer une feuille de calcul dans un complément VSTO  
  
1.  Affectez le nombre total de feuilles dans le classeur à une variable, puis déplacez la première feuille de calcul pour qu’elle devienne la dernière.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#16)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Comment : supprimer des feuilles de calcul des classeurs par programmation](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  