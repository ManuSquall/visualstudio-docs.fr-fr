---
title: "Comment&#160;: redimensionner les contr&#244;les ListObject"
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
  - "ListObject (contrôle), redimensionnement"
ms.assetid: a4c7dceb-7b55-447e-9b88-c3596a2fc361
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Comment&#160;: redimensionner les contr&#244;les ListObject
  Vous définissez la taille d’un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lorsque vous l’ajoutez à un classeur Microsoft Office Excel. Toutefois, vous souhaiterez peut\-être le redimensionner ultérieurement. Par exemple, vous pourriez modifier une liste à deux colonnes en liste à trois colonnes.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Vous pouvez redimensionner des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> au moment du design ou au moment de l’exécution dans des projets au niveau du document. Vous pouvez redimensionner des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> au moment de l’exécution dans un projet de complément VSTO.  
  
 Cette rubrique décrit les tâches suivantes :  
  
-   [Redimensionnement de contrôles ListObject au moment du design](#designtime)  
  
-   [Redimensionnement de contrôles ListObject au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)  
  
-   [Redimensionnement de contrôles ListObject au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)  
  
 Pour plus d’informations sur les contrôles <xref:Microsoft.Office.Tools.Excel.ListObject>, consultez [ListObject, contrôle](../vsto/listobject-control.md).  
  
 ![lien vers la vidéo](~/docs/data-tools/media/playvideo.gif "lien vers la vidéo") Pour obtenir une démonstration vidéo connexe, consultez [Comment ajouter des colonnes à un objet de liste lié aux données au moment de l’exécution ?](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> Redimensionnement d’un contrôle ListObject au moment du design  
 Pour redimensionner une liste, vous pouvez cliquer sur l’une des poignées de redimensionnement et la faire glisser, ou vous pouvez redéfinir sa taille dans la boîte de dialogue **Redimensionner la liste**.  
  
#### Pour redimensionner une liste à l’aide de la boîte de dialogue Redimensionner la liste  
  
1.  Cliquez avec le bouton droit sur un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
2.  Pointez sur **Liste**, puis cliquez sur **Redimensionner la liste** dans le menu contextuel.  
  
3.  Sélectionnez les cellules que vous souhaitez utiliser pour définir la taille de la liste.  
  
4.  Cliquez sur **OK**.  
  
##  <a name="runtimedoclevel"></a> Redimensionnement d’un contrôle ListObject au moment de l’exécution dans un projet au niveau du document  
 Vous pouvez redimensionner un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> au moment de l’exécution à l’aide de la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A>. Vous ne pouvez pas utiliser cette méthode pour déplacer le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> vers un nouvel emplacement sur la feuille de calcul. Les en\-têtes doivent rester sur la même ligne et le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> redimensionné doit chevaucher l’objet de liste d’origine. Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> redimensionné doit contenir une ligne d’en\-tête et au moins une ligne de données.  
  
#### Pour redimensionner un objet de liste par programmation  
  
1.  Créez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> qui couvre les cellules **A1** à **A3** sur `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#6)]  
  
2.  Redimensionnez la liste pour inclure les cellules **A1** à **C5**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> Redimensionnement d’un contrôle ListObject au moment de l’exécution dans un projet de complément VSTO  
 Vous pouvez redimensionner un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> sur n’importe quelle feuille de calcul ouverte au moment de l’exécution. Pour plus d’informations sur la façon d’ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul à l’aide d’un complément VSTO, consultez [Comment : ajouter des contrôles ListObject aux feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
#### Pour redimensionner un objet de liste par programmation  
  
1.  Créez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> qui couvre les cellules **A1** à **A3** sur `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#12)]  
  
2.  Redimensionnez la liste pour inclure les cellules **A1** à **C5**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#13)]  
  
## Voir aussi  
 [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject, contrôle](../vsto/listobject-control.md)   
 [Comment : ajouter des contrôles ListObject aux feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Comment : redimensionner les contrôles Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Comment : redimensionner les contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)  
  
  