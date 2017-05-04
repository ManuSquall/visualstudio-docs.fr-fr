---
title: "Comment&#160;: s&#233;lectionner des feuilles de calcul par programmation | Microsoft Docs"
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
  - "projets Excel, sélectionner des feuilles de calcul"
  - "feuilles de calcul, sélectionner"
ms.assetid: 9e7cdb11-e825-4c9f-abcd-d46fd20dc5e0
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Comment&#160;: s&#233;lectionner des feuilles de calcul par programmation
  La méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> méthode sélectionne l'objet spécifié, ce qui déplace la sélection de l'utilisateur vers le nouvel objet.  Utilisez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> si vous souhaitez donner le focus à l'objet sans modifier la sélection de l'utilisateur.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Si vous souhaitez sélectionner une feuille de calcul existante dans un complément VSTO ou si la feuille de calcul a été créée au moment de l'exécution dans une personnalisation au niveau du document, vous devez utiliser la collection Excel <xref:Microsoft.Office.Interop.Excel.Sheets> du classeur Excel pour y accéder. Sinon, vous pouvez accéder directement à l'élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet>.  
  
## Utilisation de l'élément hôte de feuille de calcul  
 Dans une personnalisation au niveau du document, ajoutez le code suivant à **Sheet1.vb** ou à **Sheet1.cs**.  
  
#### Pour sélectionner la première feuille de calcul d'un classeur à l'aide d'un élément hôte  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> de `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#19)]  
  
## Utilisation de la collection Sheets du classeur Excel  
 Accédez à la feuille de calcul en utilisant la collection Excel <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
#### Pour sélectionner la première feuille de calcul d'un classeur en utilisant la collection Sheets du classeur Excel  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> de la collection <xref:Microsoft.Office.Interop.Excel.Sheets> pour sélectionner la première feuille de calcul du classeur actif.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#20)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : imprimer des feuilles de calcul par programmation](../vsto/how-to-programmatically-print-worksheets.md)   
 [Comment : supprimer des feuilles de calcul des classeurs par programmation](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  