---
title: "Comment&#160;: afficher une cha&#238;ne dans une cellule de feuille de calcul par programmation | Microsoft Docs"
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
  - "texte (développement Office dans Visual Studio), ajouter à des feuilles de calcul"
  - "feuilles de calcul, afficher du texte dans des cellules"
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Comment&#160;: afficher une cha&#238;ne dans une cellule de feuille de calcul par programmation
  Cet exemple montre comment afficher du texte dans une cellule par programmation.  Pour afficher du texte dans une cellule, utilisez au choix un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> ou un objet de plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Utilisation d'un contrôle NamedRange  
 Cet exemple utilise un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> nommé `message` .  Le contrôle doit être ajouté à une personnalisation au niveau du document au moment du design.  Le code suivant doit être placé dans une classe Sheet, et non dans la classe `ThisWorkbook`.  
  
#### Pour afficher du texte dans un contrôle NamedRange  
  
1.  Affectez au contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> la valeur **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#68)]  
  
## Utilisation d'une plage Excel native  
 Le code suivant crée une plage par programmation, puis lui assigne une valeur.  
  
#### Pour afficher du texte dans une plage Excel  
  
1.  Récupérez la plage à la cellule **A1** sur `Sheet1` et définissez la valeur **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#69)]  
  
## Voir aussi  
 [Procédure pas à pas : collecte de données à l'aide d'un Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Dépannage des solutions Office](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  