---
title: "Comment&#160;: copier des feuilles de calcul par programmation | Microsoft Docs"
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
  - "Excel (développement Office dans Visual Studio), copier des feuilles de calcul"
  - "feuilles de calcul, copier"
ms.assetid: e49e03f5-7b2f-416b-b5fe-0965336c47e1
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Comment&#160;: copier des feuilles de calcul par programmation
  Vous pouvez créer une copie d'une feuille de calcul et insérer cette feuille de calcul avant ou après une feuille existante dans le classeur.  Si vous ne spécifiez pas d'emplacement d'insertion de la feuille de calcul, Excel crée un nouveau classeur dans lequel la placer.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Que vous copiiez la feuille de calcul par programmation ou que l'utilisateur final la copie manuellement, la nouvelle feuille de calcul n'a pas de code\-behind et les contrôles sur la nouvelle feuille de calcul ne fonctionnent pas.  Cela est dû au fait que la feuille de calcul récemment copiée est un objet <xref:Microsoft.Office.Interop.Excel.Worksheet>, non un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet>.  Les contrôles Windows Forms et les contrôles hôtes peuvent uniquement être ajoutés aux éléments hôtes.  Pour plus d'informations, consultez [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### Pour ajouter une copie de feuille de calcul à un classeur dans une personnalisation au niveau du document  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> pour copier la première feuille de calcul du classeur actif et placez la copie après la troisième feuille.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#16)]  
  
### Pour ajouter une copie de feuille de calcul à un classeur dans un complément VSTO  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> pour copier la première feuille de calcul du classeur actif et placez la copie après la troisième feuille.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Comment : ajouter des feuilles de calcul à des classeurs par programmation](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Comment : supprimer des feuilles de calcul des classeurs par programmation](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Comment : sélectionner des feuilles de calcul par programmation](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  