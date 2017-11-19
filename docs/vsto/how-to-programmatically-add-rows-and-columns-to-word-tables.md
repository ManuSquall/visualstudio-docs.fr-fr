---
title: "Comment : ajouter par programmation des lignes et des colonnes à des tableaux Word | Documents Microsoft"
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
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
ms.assetid: 01a9b6ca-1373-4a6e-b9e6-2225a1321daf
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bbe1ad8bea69f7d91b7796bae7cc03880fef7b04
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Comment : ajouter des lignes et des colonnes à des tableaux Word par programmation
  Dans un tableau Microsoft Office Word, les cellules sont organisées en lignes et en colonnes. Vous pouvez utiliser la méthode <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Rows> pour ajouter des lignes au tableau et la méthode <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Columns> pour ajouter des colonnes.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customization-examples"></a>Exemples de personnalisation au niveau du document  
 Les exemples de code suivants peuvent être utilisés dans une personnalisation au niveau du document. Pour utiliser ces exemples, exécutez-les à partir de la classe `ThisDocument` de votre projet. Ces exemples supposent que le document associé à votre personnalisation possède déjà au moins un tableau.  
  
> [!IMPORTANT]  
>  Ce code s'exécute uniquement dans les projets que vous créez à l'aide des modèles de projet suivants :  
>   
>  -   Document Word 2013  
> -   Modèle Word 2013  
> -   Document Word 2010  
> -   Modèle Word 2010  
>   
>  Si vous souhaitez effectuer cette tâche dans n’importe quel autre type de projet, vous devez ajouter une référence à la **Microsoft.Office.Interop.Word** assembly et que vous devez utiliser les classes de cet assembly pour ajouter des lignes et des colonnes aux tableaux. Pour plus d’informations, consultez [Comment : cible Office Applications via les assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) et [référence d’Assembly PIA Word 2010 principal](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### <a name="to-add-a-row-to-a-table"></a>Pour ajouter une ligne à un tableau  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> pour ajouter une ligne à un tableau.  
  
     [!code-vb[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]  
  
#### <a name="to-add-a-column-to-a-table"></a>Pour ajouter une colonne à un tableau  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>, puis utilisez la méthode <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> pour que toutes les colonnes aient la même largeur.  
  
     [!code-vb[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]  
  
## <a name="vsto-add-in-examples"></a>Exemples de complément VSTO  
 Les exemples de code suivants peuvent être utilisés dans un complément VSTO. Pour utiliser les exemples, exécutez-les à partir de la classe `ThisAddIn` de votre projet. Ces exemples supposent que le document actif possède déjà au moins un tableau.  
  
> [!IMPORTANT]  
>  Ce code s’exécute uniquement dans les projets que vous créez à l’aide des modèles de complément VSTO Word :  
>   
>  Si vous souhaitez effectuer cette tâche dans n’importe quel autre type de projet, vous devez ajouter une référence à la **Microsoft.Office.Interop.Word** assembly et que vous devez utiliser les classes de cet assembly pour ajouter des lignes et des colonnes aux tableaux. Pour plus d’informations, consultez [Comment : cible Office Applications via les assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) et [référence d’Assembly PIA Word 2010 principal](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### <a name="to-add-a-row-to-a-table"></a>Pour ajouter une ligne à un tableau  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> pour ajouter une ligne à un tableau.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]  
  
#### <a name="to-add-a-column-to-a-table"></a>Pour ajouter une colonne à un tableau  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>, puis utilisez la méthode <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> pour que toutes les colonnes aient la même largeur.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer des tableaux Word par programmation](../vsto/how-to-programmatically-create-word-tables.md)   
 [Comment : ajouter texte et mise en forme aux cellules des tableaux Word par programmation](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Guide pratique pour remplir des tableaux Word avec des propriétés de document par programmation](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  