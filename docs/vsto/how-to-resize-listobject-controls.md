---
title: 'Comment : redimensionner les contrôles ListObject | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 12a81e6bb4a0484b79ad42b8fbab77db97ea82c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-resize-listobject-controls"></a>Comment : redimensionner les contrôles ListObject
  Vous définissez la taille d’un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lorsque vous l’ajoutez à un classeur Microsoft Office Excel. Toutefois, vous souhaiterez peut-être le redimensionner ultérieurement. Par exemple, vous pourriez modifier une liste à deux colonnes en liste à trois colonnes.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Vous pouvez redimensionner des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> au moment du design ou au moment de l’exécution dans des projets au niveau du document. Vous pouvez redimensionner des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> au moment de l’exécution dans un projet de complément VSTO.  
  
 Cette rubrique décrit les tâches suivantes :  
  
-   [Redimensionnement de contrôles ListObject au moment du design](#designtime)  
  
-   [Redimensionnement de contrôles ListObject au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)  
  
-   [Redimensionnement de contrôles ListObject au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)  
  
 Pour plus d’informations sur les contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> , consultez [ListObject Control](../vsto/listobject-control.md).  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment ajouter des colonnes à un objet de liste lié aux données lors de l’exécution ?](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> Redimensionnement d’un contrôle ListObject au moment du design  
 Pour redimensionner une liste, vous pouvez cliquer sur l’une des poignées de redimensionnement et la faire glisser, ou vous pouvez redéfinir sa taille dans la boîte de dialogue **Redimensionner la liste** .  
  
#### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Pour redimensionner une liste à l’aide de la boîte de dialogue Redimensionner la liste  
  
  
1.  Cliquez n’importe où dans le <xref:Microsoft.Office.Tools.Excel.ListObject> table. Le **outils de tableau, la conception** onglet dans le ruban s’affiche.  
  
2.  Dans la section Propriétés, cliquez sur **redimensionner le tableau**.  

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)
  
3.  Sélectionnez la nouvelle plage de données pour votre table.  
  
4.  Cliquez sur **OK**.  
  
##  <a name="runtimedoclevel"></a> Redimensionnement d’un contrôle ListObject au moment de l’exécution dans un projet au niveau du document  
 Vous pouvez redimensionner un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> au moment de l’exécution à l’aide de la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> . Vous ne pouvez pas utiliser cette méthode pour déplacer le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> vers un nouvel emplacement sur la feuille de calcul. Les en-têtes doivent rester sur la même ligne et le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> redimensionné doit chevaucher l’objet de liste d’origine. Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> redimensionné doit contenir une ligne d’en-tête et au moins une ligne de données.  
  
#### <a name="to-resize-a-list-object-programmatically"></a>Pour redimensionner un objet de liste par programmation  
  
1.  Créez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> qui couvre les cellules **A1** à **A3** sur `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]  
  
2.  Redimensionnez la liste pour inclure les cellules **A1** à **C5**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> Redimensionnement d’un contrôle ListObject au moment de l’exécution dans un projet de complément VSTO  
 Vous pouvez redimensionner un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> sur n’importe quelle feuille de calcul ouverte au moment de l’exécution. Pour plus d’informations sur la façon d’ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul à l’aide d’un complément VSTO, consultez [How to: Add ListObject Controls to Worksheets](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
#### <a name="to-resize-a-list-object-programmatically"></a>Pour redimensionner un objet de liste par programmation  
  
1.  Créez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> qui couvre les cellules **A1** à **A3** sur `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]  
  
2.  Redimensionnez la liste pour inclure les cellules **A1** à **C5**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de Documents Word et classeurs Excel dans des Compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject (contrôle)](../vsto/listobject-control.md)   
 [Comment : ajouter des contrôles ListObject aux feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Comment : redimensionner les contrôles Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Guide pratique pour redimensionner les contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)  
  
  