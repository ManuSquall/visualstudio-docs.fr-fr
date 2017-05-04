---
title: "Comment&#160;: appliquer des styles &#224; des plages dans les classeurs par programmation | Microsoft Docs"
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
  - "plages, styles"
  - "styles, plages de classeur"
  - "classeurs, styles"
ms.assetid: c7e781ed-f366-45bb-aeb6-69c10d19d842
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Comment&#160;: appliquer des styles &#224; des plages dans les classeurs par programmation
  Vous pouvez appliquer des styles nommés à des zones dans les classeurs. Excel fournit différents styles prédéfinis.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 La boîte de dialogue **Format de cellule** affiche toutes les options que vous pouvez utiliser pour formater des cellules, et chacune de ces options est disponible à partir de votre code. Pour afficher cette boîte de dialogue dans Excel, cliquez sur **Cellules** dans le menu **Format**.  
  
### Pour appliquer un style à une plage nommée dans une personnalisation au niveau du document  
  
1.  Créez un style et définissez ses attributs.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#53)]  
  
2.  Créez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>, affectez\-lui du texte, puis appliquez le nouveau style. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#54](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#54)]  
  
### Pour supprimer un style d'une plage nommée dans une personnalisation au niveau du document  
  
1.  Appliquez le style Normal à la plage. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#55](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#55)]  
  
### Pour appliquer un style à une plage nommée dans un complément VSTO  
  
1.  Créez un style et définissez ses attributs.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#28)]  
  
2.  Créez <xref:Microsoft.Office.Interop.Excel.Range>, affectez\-lui du texte, puis appliquez le nouveau style.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#29)]  
  
### Pour effacer un style d’une plage nommée dans un complément VSTO  
  
1.  Appliquez le style Normal à la plage.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#56](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#56)]  
  
## Voir aussi  
 [Utilisation des plages](../vsto/working-with-ranges.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  