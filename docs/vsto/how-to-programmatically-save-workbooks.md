---
title: "Comment&#160;: enregistrer des classeurs par programmation | Microsoft Docs"
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
  - "classeurs, enregistrer"
  - "classeurs, enregistrer des copies de sauvegarde"
  - "classeurs, enregistrer au format XML"
ms.assetid: 991ccf9b-5213-4094-9030-284ec167bdcc
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# Comment&#160;: enregistrer des classeurs par programmation
  Il existe plusieurs façons d'enregistrer un classeur.  Vous pouvez le faire sans modifier le chemin d'accès.  Si le classeur n'a pas été enregistré auparavant, vous devez l'enregistrer en spécifiant un chemin d'accès.  Sans chemin d'accès explicite, Microsoft Office Excel enregistre le fichier dans le dossier actif avec le nom qui lui a été attribué lors de sa création.  Vous pouvez également enregistrer une copie du classeur sans modifier le classeur ouvert en mémoire.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Enregistrement d'un classeur sans modifier le chemin d'accès  
  
#### Pour enregistrer un classeur associé à une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> de la classe ThisWorkbook.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#4)]  
  
#### Pour enregistrer le classeur actif dans un complément VSTO  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> pour enregistrer le classeur actif.  Pour utiliser l'exemple de code suivant, exécutez\-le dans la classe `ThisAddIn` dans un projet de complément VSTO pour Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Enregistrement d'un classeur avec un nouveau chemin d'accès  
 Vous pouvez enregistrer le classeur spécifié dans un nouvel emplacement ou avec un nouveau nom, en spécifiant éventuellement un format de fichier, un mot de passe, un mode d'accès, etc.  
  
> [!NOTE]  
>  Vous souhaiterez peut\-être affecter la valeur **False** à la propriété <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> avant d'enregistrer le classeur avec un nouveau chemin d'accès car l'enregistrement sous certains formats exige une interaction.  L'affectation de la valeur **False** à cette propriété indique à Excel d'utiliser toutes les valeurs par défaut.  
  
#### Pour enregistrer un classeur associé à une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> de la classe `ThisWorkbook`.  Pour utiliser l'exemple de code suivant, exécutez\-le dans la classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#5)]  
  
#### Pour enregistrer le classeur actif dans un complément VSTO  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> pour enregistrer le classeur actif avec un nouveau chemin d'accès.  Pour utiliser l'exemple de code suivant, exécutez\-le dans la classe `ThisAddIn` dans un projet de complément VSTO pour Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## Enregistrement d'une copie du classeur  
 Vous pouvez enregistrer une copie du classeur dans un fichier sans modifier le classeur ouvert en mémoire.  Cela est utile quand vous souhaitez créer une copie de sauvegarde sans modifier l'emplacement du classeur.  
  
#### Pour enregistrer un classeur associé à une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> de la classe `ThisWorkbook`.  Pour utiliser l'exemple de code suivant, exécutez\-le dans la classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#6)]  
  
#### Pour enregistrer le classeur actif dans un complément VSTO  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> pour enregistrer une copie du classeur actif.  Pour utiliser l'exemple de code suivant, exécutez\-le dans la classe `ThisAddIn` dans un projet de complément VSTO pour Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## Programmation fiable  
 L'annulation interactive d'une quelconque des méthodes qui enregistrent ou copient le classeur génère une erreur d'exécution dans votre code.  Par exemple, si votre procédure appelle la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> mais ne désactive pas les invites d'Excel, et que l'utilisateur clique sur **Annuler** quand il y est invité, Excel génère une erreur d'exécution.  
  
## Voir aussi  
 [Utilisation des classeurs](../vsto/working-with-workbooks.md)   
 [Élément hôte de classeur](../vsto/workbook-host-item.md)   
 [Comment : fermer des classeurs par programmation](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  