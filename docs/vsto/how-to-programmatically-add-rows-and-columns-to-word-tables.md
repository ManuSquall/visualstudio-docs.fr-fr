---
title: 'Comment : ajouter des lignes et des colonnes à des tableaux Word par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cc8fbc80a58afcb6f2256c56b1071276c50f319b
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985847"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Comment : ajouter des lignes et des colonnes à des tableaux Word par programmation
  Dans un tableau Microsoft Office Word, les cellules sont organisées en lignes et en colonnes. Vous pouvez utiliser la méthode <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Rows> pour ajouter des lignes au tableau et la méthode <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Columns> pour ajouter des colonnes.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Exemples de personnalisation au niveau du document
 Les exemples de code suivants peuvent être utilisés dans une personnalisation au niveau du document. Pour utiliser ces exemples, exécutez-les à partir de la classe `ThisDocument` de votre projet. Ces exemples supposent que le document associé à votre personnalisation possède déjà au moins un tableau.

> [!IMPORTANT]
> Ce code s'exécute uniquement dans les projets que vous créez à l'aide des modèles de projet suivants :
>
> - Document Word 2013
> - Modèle Word 2013
> - Document Word 2010
> - Modèle Word 2010
>
>   Si vous souhaitez effectuer cette tâche dans tout autre type de projet, vous devez ajouter une référence à l’assembly **Microsoft. Office. Interop. Word** , puis vous devez utiliser des classes de cet assembly pour ajouter des lignes et des colonnes à des tables. Pour plus d’informations, consultez [Guide pratique pour cibler des applications Office à l’aide d’assemblys PIA (Primary Interop](how-to-target-office-applications-through-primary-interop-assemblies.md) [assembly) et référence d’assembly PIA Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Pour ajouter une ligne à un tableau

1. Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> pour ajouter une ligne à un tableau.

     [!code-vb[Trin_VstcoreWordAutomation#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Pour ajouter une colonne à un tableau

1. Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>, puis utilisez la méthode <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> pour que toutes les colonnes aient la même largeur.

     [!code-vb[Trin_VstcoreWordAutomation#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]

## <a name="vsto-add-in-examples"></a>Exemples de compléments VSTO
 Les exemples de code suivants peuvent être utilisés dans un complément VSTO. Pour utiliser les exemples, exécutez-les à partir de la classe `ThisAddIn` de votre projet. Ces exemples supposent que le document actif possède déjà au moins un tableau.

> [!IMPORTANT]
> Ce code s'exécute uniquement dans les projets que vous créez à l'aide des modèles de complément VSTO Word :
>
> Si vous souhaitez effectuer cette tâche dans tout autre type de projet, vous devez ajouter une référence à l’assembly **Microsoft. Office. Interop. Word** , puis vous devez utiliser des classes de cet assembly pour ajouter des lignes et des colonnes à des tables. Pour plus d’informations, consultez [Guide pratique pour cibler des applications Office à l’aide d’assemblys PIA (Primary Interop](how-to-target-office-applications-through-primary-interop-assemblies.md) [assembly) et référence d’assembly PIA Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Pour ajouter une ligne à un tableau

1. Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> pour ajouter une ligne à un tableau.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Pour ajouter une colonne à un tableau

1. Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>, puis utilisez la méthode <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> pour que toutes les colonnes aient la même largeur.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]

## <a name="see-also"></a>Voir aussi
- [Comment : créer des tableaux Word par programmation](how-to-programmatically-create-word-tables.md)
- [Comment : ajouter du texte et une mise en forme à des cellules dans des tableaux Word par programmation](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Comment : remplir des tableaux Word avec des propriétés de document par programmation](how-to-programmatically-populate-word-tables-with-document-properties.md)
