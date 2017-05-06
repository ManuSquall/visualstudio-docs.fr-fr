---
title: "Comment&#160;: regrouper des lignes dans une feuille de calcul par programmation"
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
  - "colonnes (développement Office dans Visual Studio), dégrouper"
  - "groupes"
  - "groupes (développement Office dans Visual Studio), effacer dans les feuilles de calcul"
  - "groupes, créer dans des feuilles de calcul"
  - "plages, créer des groupes"
  - "lignes (développement Office dans Visual Studio), dégrouper"
  - "feuilles de calcul, effacer des groupes"
  - "feuilles de calcul, créer des groupes"
  - "feuilles de calcul, dégrouper des lignes et des colonnes"
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Comment&#160;: regrouper des lignes dans une feuille de calcul par programmation
  Vous pouvez regrouper une ou plusieurs lignes entières.  Pour créer un groupe dans une feuille de calcul, utilisez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> ou un objet plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Utilisation d'un contrôle NamedRange  
 Si vous ajoutez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à un projet au niveau du document au moment du design, vous pouvez utiliser ce contrôle pour créer un groupe par programme.  L'exemple suivant suppose qu'il existe trois contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> sur la même feuille de calcul : `data2001`, `data2002` et `dataAll`.  Chaque plage nommée fait référence à une ligne entière dans la feuille de calcul.  
  
#### Pour créer un groupe de contrôles NamedRange sur une feuille de calcul  
  
1.  Regroupez trois plages nommées en appelant la méthode <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> de chaque plage.  Ce code doit être placé dans une classe sheet et non dans la classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Pour dissocier des lignes, appelez la méthode <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A>.  
  
## Utilisation de plages Excel natives  
 Le code suppose que vous possédez trois plages Excel nommées `data2001`, `data2002` et `dataAll` dans une feuille de calcul.  
  
#### Pour créer un groupe de plages Excel dans une feuille de calcul  
  
1.  Regroupez trois plages nommées en appelant la méthode <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> de chaque plage.  L'exemple suivant suppose que la feuille de calcul contient trois contrôles <xref:Microsoft.Office.Interop.Excel.Range> nommés `data2001`, `data2002` et `dataAll`.  Chaque plage nommée fait référence à une ligne entière dans la feuille de calcul.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Pour dissocier des lignes, appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A>.  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  