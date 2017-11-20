---
title: "Comment : mapper des colonnes ListObject aux données | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
ms.assetid: 2108d0c3-d595-410e-a0ae-3dd53bf6bcc7
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bda2e6626e7d636fd4c53ed3ddbb5cfadc42666f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-map-listobject-columns-to-data"></a>Comment : mapper des colonnes ListObject aux données
  Lorsque vous liez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> à un <xref:System.Data.DataTable>, vous ne souhaitez peut-être pas afficher toutes les colonnes d’une liste ou vous pouvez avoir certaines colonnes non qui ne sont pas liées aux données. Vous pouvez mapper les colonnes que vous souhaitez voir apparaître dans le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lorsque vous appelez la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> .  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire pour créer une liste dans Excel qui est connecté à une liste SharePoint ?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
## <a name="mapping-columns"></a>Mappage de colonnes  
  
#### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Pour mapper une table de données aux colonnes d’une liste  
  
1.  Créez le <xref:System.Data.DataTable> au niveau de la classe.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]  
  
2.  Ajoutez des exemples de colonnes et de données dans le gestionnaire d’événements `Startup` de la classe `Sheet1` (dans un projet au niveau du document) ou de la classe `ThisAddIn` (dans un projet de complément VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]  
  
3.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> et passez le nom des colonnes dans l’ordre dans lequel elles doivent apparaître. L’objet de liste sera lié au <xref:System.Data.DataTable>nouvellement créé, mais l’ordre des colonnes dans l’objet de liste sera différent de l’ordre dans lequel elles apparaissent dans le <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]  
  
## <a name="specifying-unmapped-columns"></a>Spécification de colonnes non mappées  
 Lorsque vous mappez des colonnes à un <xref:System.Data.DataTable>, vous pouvez également spécifier que certaines colonnes ne doivent pas être liées aux données en passant une chaîne vide. Une nouvelle colonne qui n’est pas liée aux données est alors ajoutée au contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> .  
  
#### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Pour spécifier une colonne non mappée lors du mappage de colonnes ListObject  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> et passez le nom des colonnes dans l’ordre dans lequel elles doivent apparaître. Utilisez une chaîne vide pour indiquer l’endroit où une colonne non mappée est ajoutée ; dans le cas présent, entre la colonne de titre et la colonne de nom.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple de code suppose qu’un <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `list1` existe dans la feuille de calcul dans laquelle ce code apparaît.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de Documents Word et classeurs Excel dans des Compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Comment : remplir de données des contrôles ListObject](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject, contrôle](../vsto/listobject-control.md)  
  
  