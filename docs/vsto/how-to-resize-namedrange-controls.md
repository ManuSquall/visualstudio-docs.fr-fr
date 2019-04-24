---
title: 'Procédure : Redimensionner les contrôles NamedRange'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ba5603fe759f55a85425bc61da0a470aa38d636c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099606"
---
# <a name="how-to-resize-namedrange-controls"></a>Procédure : Redimensionner les contrôles NamedRange
  Vous pouvez définir la taille d’un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> quand vous l’ajoutez à un document Microsoft Office Excel. Toutefois, vous souhaiterez peut-être le redimensionner plus tard.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Vous pouvez redimensionner une plage nommée au moment du design ou au moment de l’exécution dans des projets au niveau du document. Vous pouvez également redimensionner des plages nommées au moment de l’exécution dans des compléments VSTO de niveau application.

 Cette rubrique décrit les tâches suivantes :

- [Redimensionner les contrôles NamedRange au moment du design](#designtime)

- [Redimensionner les contrôles NamedRange au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)

- [Redimensionner les contrôles NamedRange au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)

## <a name="designtime"></a> Redimensionner les contrôles NamedRange au moment du design
 Vous pouvez redimensionner une plage nommée en redéfinissant sa taille dans la boîte de dialogue **Définir un nom** .

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Pour redimensionner une plage nommée à l’aide de la boîte de dialogue Définir un nom

1. Cliquez avec le bouton droit sur un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> .

2. Cliquez dans le menu contextuel sur **Gérer les plages nommées** .

     La boîte de dialogue **Définir un nom** s’affiche.

3. Sélectionnez la plage nommée à redimensionner.

4. Effacez le contenu de la zone **Fait référence à** .

5. Sélectionnez les cellules que vous souhaitez utiliser pour définir la taille de la plage nommée.

6. Cliquez sur **OK**.

## <a name="runtimedoclevel"></a> Redimensionner les contrôles NamedRange au moment de l’exécution dans un projet au niveau du document
 Vous pouvez redimensionner une plage nommée par programmation à l’aide de la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> .

> [!NOTE]
>  Dans la fenêtre **Propriétés** , la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> est marquée comme étant en lecture seule.

### <a name="to-resize-a-named-range-programmatically"></a>Pour redimensionner une plage nommée par programmation

1. Créez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> dans la cellule **A1** de `Sheet1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]

2. Redimensionnez la plage nommée pour inclure la cellule **B1**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]

## <a name="runtimeaddin"></a> Redimensionner les contrôles NamedRange au moment de l’exécution dans un projet de complément VSTO
 Vous pouvez redimensionner un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle sur une feuille de calcul ouverte lors de l’exécution. Pour plus d’informations sur l’ajout d’un <xref:Microsoft.Office.Tools.Excel.NamedRange> le contrôle à une feuille de calcul en utilisant un complément, VSTO, consultez [Comment : Ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

### <a name="to-resize-a-named-range-programmatically"></a>Pour redimensionner une plage nommée par programmation

1. Créez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> dans la cellule **A1** de `Sheet1`.

     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]

2. Redimensionnez la plage nommée pour inclure la cellule **B1**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]

## <a name="see-also"></a>Voir aussi
- [Étendre des documents Word et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)
- [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange (contrôle)](../vsto/namedrange-control.md)
- [Guide pratique pour Ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Guide pratique pour Redimensionner les contrôles Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Guide pratique pour Redimensionner les contrôles ListObject](../vsto/how-to-resize-listobject-controls.md)
