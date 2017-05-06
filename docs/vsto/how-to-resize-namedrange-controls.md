---
title: "Comment&#160;: redimensionner les contr&#244;les NamedRange"
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
  - "contrôles (développement Office dans Visual Studio), redimensionnement"
  - "NamedRange (contrôle), redimensionnement"
  - "plages, redimensionnement dans Excel"
ms.assetid: 7d6f0b2f-be46-49b7-9f38-b4c8849683f7
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Comment&#160;: redimensionner les contr&#244;les NamedRange
  Vous pouvez définir la taille d’un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> quand vous l’ajoutez à un document Microsoft Office Excel. Toutefois, vous souhaiterez peut\-être le redimensionner plus tard.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Vous pouvez redimensionner une plage nommée au moment du design ou au moment de l’exécution dans des projets au niveau du document. Vous pouvez également redimensionner des plages nommées au moment de l’exécution dans des compléments VSTO de niveau application.  
  
 Cette rubrique décrit les tâches suivantes :  
  
-   [Redimensionnement de contrôles NamedRange au moment du design](#designtime)  
  
-   [Redimensionnement de contrôles NamedRange au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)  
  
-   [Redimensionnement de contrôles NamedRange au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)  
  
##  <a name="designtime"></a> Redimensionnement de contrôles NamedRange au moment du design  
 Vous pouvez redimensionner une plage nommée en redéfinissant sa taille dans la boîte de dialogue **Définir un nom**.  
  
#### Pour redimensionner une plage nommée à l’aide de la boîte de dialogue Définir un nom  
  
1.  Cliquez avec le bouton droit sur un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
2.  Cliquez dans le menu contextuel sur **Gérer les plages nommées**.  
  
     La boîte de dialogue **Définir un nom** s’affiche.  
  
3.  Sélectionnez la plage nommée à redimensionner.  
  
4.  Effacez le contenu de la zone **Fait référence à**.  
  
5.  Sélectionnez les cellules que vous souhaitez utiliser pour définir la taille de la plage nommée.  
  
6.  Cliquez sur **OK**.  
  
##  <a name="runtimedoclevel"></a> Redimensionnement de contrôles NamedRange au moment de l’exécution dans un projet au niveau du document  
 Vous pouvez redimensionner une plage nommée par programmation à l’aide de la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A>.  
  
> [!NOTE]  
>  Dans la fenêtre **Propriétés**, la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> est marquée comme étant en lecture seule.  
  
#### Pour redimensionner une plage nommée par programmation  
  
1.  Créez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> dans la cellule **A1** de `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#4)]  
  
2.  Redimensionnez la plage nommée pour inclure la cellule **B1**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> Redimensionnement de contrôles NamedRange au moment de l’exécution dans un projet de complément VSTO  
 Vous pouvez redimensionner un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> sur n’importe quelle feuille de calcul ouverte au moment de l’exécution. Pour plus d’informations sur la façon d’ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul à l’aide d’un complément VSTO, consultez [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
#### Pour redimensionner une plage nommée par programmation  
  
1.  Créez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> dans la cellule **A1** de `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#10)]  
  
2.  Redimensionnez la plage nommée pour inclure la cellule **B1**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#11)]  
  
## Voir aussi  
 [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Comment : redimensionner les contrôles Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Comment : redimensionner les contrôles ListObject](../vsto/how-to-resize-listobject-controls.md)  
  
  