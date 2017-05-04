---
title: "Comment&#160;: stocker et r&#233;cup&#233;rer des valeurs de date dans des plages Excel par programmation | Microsoft Docs"
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
  - "valeurs de dates"
  - "valeurs de dates, stocker dans les plages Excel"
  - "dates, récupérer à partir de plages Excel"
  - "dates, stocker dans les plages Excel"
  - "Excel (développement Office dans Visual Studio), récupérer les valeurs de date à partir de plages"
  - "Excel (développement Office dans Visual Studio), stocker des valeurs de date dans les plages"
  - "plages, récupérer les valeurs de date"
  - "plages, stocker des valeurs de date"
ms.assetid: e1cdd262-0356-4499-8bc5-e730f74235a2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Comment&#160;: stocker et r&#233;cup&#233;rer des valeurs de date dans des plages Excel par programmation
  Vous pouvez stocker et extraire des valeurs dans un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> ou un objet de plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Si vous stockez une valeur de date d'une plage égale ou supérieure au 01\/01\/1900 à l'aide des outils de développement Office dans Visual Studio, elle est stockée au format OA \(OLE Automation\).  Vous devez utiliser la méthode <xref:System.DateTime.FromOADate%2A> pour récupérer la valeur des dates OLE Automation.  Si la date est antérieure au 1\/1\/1900, elle est stockée comme une chaîne.  
  
> [!NOTE]  
>  Les dates Excel diffèrent des dates OLE Automation pour les deux premiers mois de l'année 1900.  Il existe également d'autres différences si l'option **Calendrier depuis 1904** est activée.  Les exemples de code ci\-dessous ne traitent pas ces différences.  
  
## Utilisation d'un contrôle NamedRange  
  
-   Cet exemple illustre des personnalisations au niveau du document.  Le code suivant doit être placé dans une classe Sheet, et non dans la classe `ThisWorkbook`.  
  
#### Pour stocker une valeur de date dans une plage nommée  
  
1.  Créez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> dans la cellule **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#50)]  
  
2.  Définissez la date d'aujourd'hui comme valeur pour `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#51)]  
  
#### Pour récupérer une valeur de date d'une plage nommée  
  
1.  Récupérez la valeur de date de `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#52)]  
  
## Utilisation de plages Excel natives  
  
#### Pour stocker une valeur de date dans un objet de plage Excel natif  
  
1.  Créez un <xref:Microsoft.Office.Interop.Excel.Range> qui présente la cellule **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
2.  Définissez la date d'aujourd'hui comme valeur pour `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
#### Pour extraire une valeur de date à partir d'un objet de plage Excel natif  
  
1.  Récupérez la valeur de date de `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
## Voir aussi  
 [Utilisation des plages](../vsto/working-with-ranges.md)   
 [Vue d'ensemble du modèle objet Excel](../vsto/excel-object-model-overview.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Comment : faire référence aux plages de la feuille de calcul dans le code par programmation](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  