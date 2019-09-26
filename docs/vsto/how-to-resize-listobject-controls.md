---
title: 'Procédure : Redimensionner les contrôles ListObject'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d7dac99088dc57b538f7a26ffbd0bdc0e3e05b5a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252127"
---
# <a name="how-to-resize-listobject-controls"></a>Procédure : Redimensionner les contrôles ListObject
  Vous définissez la taille d’un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lorsque vous l’ajoutez à un classeur Microsoft Office Excel. Toutefois, vous souhaiterez peut-être le redimensionner ultérieurement. Par exemple, vous pourriez modifier une liste à deux colonnes en liste à trois colonnes.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Vous pouvez redimensionner des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> au moment du design ou au moment de l’exécution dans des projets au niveau du document. Vous pouvez redimensionner <xref:Microsoft.Office.Tools.Excel.ListObject> les contrôles au moment de l’exécution dans un projet de complément VSTO.

 Cette rubrique décrit les tâches suivantes :

- [Redimensionner les contrôles ListObject au moment du design](#designtime)

- [Redimensionner les contrôles ListObject au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)

- [Redimensionner les contrôles ListObject au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)

  Pour plus d’informations <xref:Microsoft.Office.Tools.Excel.ListObject> sur les contrôles, consultez [ListObject, contrôle](../vsto/listobject-control.md).

  ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") Pour une démonstration vidéo connexe, [consultez Comment faire : Ajouter des colonnes à un objet de liste lié aux données au moment de l’exécution ? ](http://go.microsoft.com/fwlink/?LinkID=130318).

## <a name="designtime"></a>Redimensionner un contrôle ListObject au moment du design
 Pour redimensionner une liste, vous pouvez cliquer sur l’une des poignées de redimensionnement et la faire glisser, ou vous pouvez redéfinir sa taille dans la boîte de dialogue **Redimensionner la liste** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Pour redimensionner une liste à l’aide de la boîte de dialogue Redimensionner la liste

1. Cliquez n’importe où <xref:Microsoft.Office.Tools.Excel.ListObject> dans le tableau. L’onglet**conception** des **Outils** > de table du ruban s’affiche.

2. Dans la section Propriétés, cliquez sur **redimensionner la table**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Sélectionnez la nouvelle plage de données pour votre table.

4. Cliquez sur **OK**.

## <a name="runtimedoclevel"></a>Redimensionner un contrôle ListObject au moment de l’exécution dans un projet au niveau du document
 Vous pouvez redimensionner un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> au moment de l’exécution à l’aide de la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> . Vous ne pouvez pas utiliser cette méthode pour déplacer le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> vers un nouvel emplacement sur la feuille de calcul. Les en-têtes doivent rester sur la même ligne et le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> redimensionné doit chevaucher l’objet de liste d’origine. Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> redimensionné doit contenir une ligne d’en-tête et au moins une ligne de données.

### <a name="to-resize-a-list-object-programmatically"></a>Pour redimensionner un objet de liste par programmation

1. Créez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> qui couvre les cellules **A1** à **A3** sur `Sheet1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2. Redimensionnez la liste pour inclure les cellules **A1** à **C5**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

## <a name="runtimeaddin"></a>Redimensionner un ListObject au moment de l’exécution dans un projet de complément VSTO
 Vous pouvez redimensionner un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> sur n’importe quelle feuille de calcul ouverte au moment de l’exécution. Pour plus d’informations sur l’ajout d' <xref:Microsoft.Office.Tools.Excel.ListObject> un contrôle à une feuille de calcul à l’aide d’un complément [VSTO, consultez Procédure : Ajoutez des contrôles ListObject aux feuilles](../vsto/how-to-add-listobject-controls-to-worksheets.md)de calcul.

### <a name="to-resize-a-list-object-programmatically"></a>Pour redimensionner un objet de liste par programmation

1. Créez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> qui couvre les cellules **A1** à **A3** sur `Sheet1`.

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2. Redimensionnez la liste pour inclure les cellules **A1** à **C5**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>Voir aussi
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject (contrôle)](../vsto/listobject-control.md)
- [Guide pratique pour Ajouter des contrôles ListObject à des feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Guide pratique pour Redimensionner les contrôles Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Guide pratique pour Redimensionner les contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)
