---
title: "Comment&#160;: trier les donn&#233;es par programmation dans les feuilles de calcul | Microsoft Docs"
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
  - "données (développement Office dans Visual Studio), trier dans des feuilles de calcul"
  - "trier les données, feuilles de calcul"
  - "trier les données, dans des feuilles de calcul"
  - "feuilles de calcul, trier les données"
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Comment&#160;: trier les donn&#233;es par programmation dans les feuilles de calcul
  Vous pouvez trier les données contenues dans les listes et les plages de feuille de calcul au moment de l'exécution.  Le code suivant trie une plage à colonnes multiples nommée `Fruits` sur les données de la première colonne, puis sur les données de la deuxième colonne.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Tri des données dans une personnalisation au niveau du document  
  
#### Pour trier les des données d'un contrôle NamedRange  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> du contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>.  L'exemple suivant requiert un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> nommé `Fruits` sur une feuille de calcul.  Ce code doit être placé dans une classe sheet et non dans la classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#78)]  
  
 Placez le code suivant dans Sheet1.vb ou Sheet1.cs pour trier les données d'un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject>.  Le code suppose que vous avez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `fruitList` dans une feuille de calcul nommée `Sheet1`.  
  
#### Pour trier les données d'un contrôle ListObject  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> de la propriété <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> du contrôle hôte <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#79)]  
  
## Tri de données dans un complément VSTO  
  
#### Pour trier les données d'une plage native  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> du contrôle Excel <xref:Microsoft.Office.Interop.Excel.Range> natif.  L'exemple suivant requiert un contrôle Excel nommé `Fruits` sur une feuille de calcul.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
#### Pour trier les données d'un contrôle ListObject  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> de la propriété <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> du contrôle Excel <xref:Microsoft.Office.Interop.Excel.ListObject> natif.  L'exemple suivant suppose que vous disposez d'un contrôle Excel <xref:Microsoft.Office.Interop.Excel.ListObject> natif nommé `fruitList` dans la feuille de calcul active.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : remplir automatiquement des plages avec des données soumises à modification incrémentielle par programmation](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Comment : faire référence aux plages de la feuille de calcul dans le code par programmation](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Comment : appliquer des styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [ListObject, contrôle](../vsto/listobject-control.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  