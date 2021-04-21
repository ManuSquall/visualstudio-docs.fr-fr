---
title: 'Comment : mapper des colonnes ListObject à des données'
description: Découvrez comment vous pouvez mapper les colonnes que vous souhaitez voir apparaître dans le ListObject lorsque vous appelez la méthode SetDataBinding.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68cb12503d0f8ad59de92f965c0ed51fbc0d7f40
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827459"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Comment : mapper des colonnes ListObject à des données
  Lorsque vous liez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> à un <xref:System.Data.DataTable>, vous ne souhaitez peut-être pas afficher toutes les colonnes d’une liste ou vous pouvez avoir certaines colonnes non qui ne sont pas liées aux données. Vous pouvez mapper les colonnes que vous souhaitez voir apparaître dans le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lorsque vous appelez la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Mapper les colonnes

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Pour mapper une table de données aux colonnes d’une liste

1. Créez le <xref:System.Data.DataTable> au niveau de la classe.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet16":::

2. Ajoutez des exemples de colonnes et de données dans le `Startup` Gestionnaire d’événements de la `Sheet1` classe (dans un projet au niveau du document) ou dans la `ThisAddIn` classe (dans un projet de complément VSTO).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet17":::

3. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> et passez les noms des colonnes dans l’ordre dans lequel elles doivent apparaître. L’objet de liste sera lié au nouvellement créé <xref:System.Data.DataTable> , mais l’ordre des colonnes dans l’objet de liste sera différent de l’ordre dans lequel elles apparaissent dans <xref:System.Data.DataTable> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet18":::

## <a name="specify-unmapped-columns"></a>Spécifier des colonnes non mappées
 Lorsque vous mappez des colonnes à un <xref:System.Data.DataTable>, vous pouvez également spécifier que certaines colonnes ne doivent pas être liées aux données en passant une chaîne vide. Une nouvelle colonne qui n’est pas liée aux données est alors ajoutée au contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> .

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Pour spécifier une colonne non mappée lors du mappage de colonnes ListObject

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> et passez les noms des colonnes dans l’ordre dans lequel elles doivent apparaître. Utilisez une chaîne vide pour indiquer l’endroit où une colonne non mappée est ajoutée ; dans le cas présent, entre la colonne de titre et la colonne de nom.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet19":::

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple de code suppose qu’un <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `list1` existe dans la feuille de calcul dans laquelle ce code apparaît.

## <a name="see-also"></a>Voir aussi
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Comment : remplir des contrôles ListObject avec des données](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject (contrôle)](../vsto/listobject-control.md)
