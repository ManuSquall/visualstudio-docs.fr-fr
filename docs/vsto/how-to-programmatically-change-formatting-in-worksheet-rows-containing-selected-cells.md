---
title: "Comment&#160;: modifier la mise en forme des lignes de feuille de calcul contenant des cellules s&#233;lectionn&#233;es par programmation | Microsoft Docs"
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
  - "mettre en forme (développement Office dans Visual Studio)"
  - "lignes (développement Office dans Visual Studio)"
  - "feuilles de calcul, modifier la mise en forme"
ms.assetid: c55cd488-98d1-46c6-9715-0e9212d178de
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Comment&#160;: modifier la mise en forme des lignes de feuille de calcul contenant des cellules s&#233;lectionn&#233;es par programmation
  Vous pouvez modifier la police d'une ligne entière contenant une cellule sélectionnée, de manière à ce que le texte soit en gras.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Pour mettre la ligne active en gras et faire passer en style normal la ligne précédente  
  
1.  Déclarez une variable statique pour garder une trace de la ligne précédemment sélectionnée.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#37)]
     [!code-vb[Trin_VstcoreExcelAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#37)]  
  
2.  Récupérez une référence à la cellule active à l'aide de la propriété <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#38)]
     [!code-vb[Trin_VstcoreExcelAutomation#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#38)]  
  
3.  Mettez la ligne active en gras à l'aide de la propriété <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A> de la cellule active.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#39)]
     [!code-vb[Trin_VstcoreExcelAutomation#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#39)]  
  
4.  Vérifiez que la valeur actuelle de `previousRow` n'est pas 0.  Un 0 \(zéro\) indique qu'il s'agit de la première ligne du code.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#40](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#40)]
     [!code-vb[Trin_VstcoreExcelAutomation#40](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#40)]  
  
5.  Vérifiez que la ligne actuelle est différente de la précédente.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#41](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#41)]
     [!code-vb[Trin_VstcoreExcelAutomation#41](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#41)]  
  
6.  Récupérez une référence à une plage représentant la ligne précédemment sélectionnée et définissez\-la pour qu'elle ne soit pas en gras.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#42)]
     [!code-vb[Trin_VstcoreExcelAutomation#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#42)]  
  
7.  Stockez la ligne actuelle pour qu'elle devienne la ligne précédente pour le test suivant.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#43)]
     [!code-vb[Trin_VstcoreExcelAutomation#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#43)]  
  
 L'exemple suivant illustre la méthode complète.  
  
## Exemple  
 [!code-csharp[Trin_VstcoreExcelAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#36)]
 [!code-vb[Trin_VstcoreExcelAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#36)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : appliquer des styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Comment : copier des données et une mise en forme d'une feuille de calcul à l'autre par programmation](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  