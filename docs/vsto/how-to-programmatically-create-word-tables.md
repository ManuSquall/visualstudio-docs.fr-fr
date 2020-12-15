---
title: 'Comment : créer des tableaux Word par programmation'
description: Apprenez à utiliser la méthode Add de la collection tables pour ajouter un tableau à la plage spécifiée dans un document Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f2d31f656f0f383ec63fb50f10b19ee26fe2509e
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523926"
---
# <a name="how-to-programmatically-create-word-tables"></a>Comment : créer des tableaux Word par programmation
  La collection <xref:Microsoft.Office.Interop.Word.Tables> est membre des classes <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document><xref:Microsoft.Office.Interop.Word.Selection> et <xref:Microsoft.Office.Interop.Word.Range>, ce qui signifie que vous pouvez créer un tableau dans l'un de ces contextes. La méthode <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> de la collection <xref:Microsoft.Office.Interop.Word.Tables> permet d’ajouter un tableau au niveau de la plage spécifiée.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="create-tables-in-document-level-customizations"></a>Créer des tables dans des personnalisations au niveau du document

### <a name="to-add-a-table-to-a-document"></a>Pour ajouter un tableau à un document

- Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> pour ajouter un tableau comprenant trois lignes et quatre colonnes au début du document.

   Pour utiliser l'exemple de code suivant, exécutez-le à partir de la classe `ThisDocument` de votre projet.

   [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]

  Lorsque vous créez un tableau, il est automatiquement ajouté à la collection <xref:Microsoft.Office.Interop.Word.Tables> de l'élément hôte <xref:Microsoft.Office.Tools.Word.Document>. Vous pouvez alors faire référence au tableau par son numéro d'élément à l'aide de la propriété <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, comme illustré dans le code suivant.

### <a name="to-refer-to-a-table-by-item-number"></a>Pour faire référence à un tableau à l'aide de son numéro d'élément

1. Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> et fournissez le numéro d'élément du tableau auquel vous souhaitez faire référence.

    Pour utiliser l'exemple de code suivant, exécutez-le à partir de la classe `ThisDocument` de votre projet.

    [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]

   Chaque objet <xref:Microsoft.Office.Interop.Word.Table> possède également une propriété <xref:Microsoft.Office.Interop.Word.Table.Range%2A> qui vous permet de définir des attributs de mise en forme.

### <a name="to-apply-a-style-to-a-table"></a>Pour appliquer un style à un tableau

1. Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Table.Style%2A> pour appliquer au tableau l'un des styles intégrés de Word.

     Pour utiliser l'exemple de code suivant, exécutez-le à partir de la classe `ThisDocument` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]

## <a name="create-tables-in-vsto-add-ins"></a>Créer des tables dans des compléments VSTO

### <a name="to-add-a-table-to-a-document"></a>Pour ajouter un tableau à un document

- Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> pour ajouter un tableau comprenant trois lignes et quatre colonnes au début du document.

   L'exemple de code suivant ajoute un tableau au document actif. Pour utiliser cet exemple, exécutez-le à partir de la classe `ThisAddIn` dans votre projet.

   [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]

  Lorsque vous créez un tableau, il est automatiquement ajouté à la collection <xref:Microsoft.Office.Interop.Word.Tables> de l'élément <xref:Microsoft.Office.Interop.Word.Document>. Vous pouvez alors faire référence au tableau par son numéro d'élément à l'aide de la propriété <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, comme illustré dans le code suivant.

### <a name="to-refer-to-a-table-by-item-number"></a>Pour faire référence à un tableau à l'aide de son numéro d'élément

1. Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> et fournissez le numéro d'élément du tableau auquel vous souhaitez faire référence.

    L'exemple de code suivant utilise le document actif. Pour utiliser cet exemple, exécutez-le à partir de la classe `ThisAddIn` dans votre projet.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]

   Chaque objet <xref:Microsoft.Office.Interop.Word.Table> possède également une propriété <xref:Microsoft.Office.Interop.Word.Table.Range%2A> qui vous permet de définir des attributs de mise en forme.

### <a name="to-apply-a-style-to-a-table"></a>Pour appliquer un style à un tableau

1. Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Table.Style%2A> pour appliquer au tableau l'un des styles intégrés de Word.

     L'exemple de code suivant utilise le document actif. Pour utiliser cet exemple, exécutez-le à partir de la classe `ThisAddIn` dans votre projet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]

## <a name="see-also"></a>Voir aussi
- [Comment : ajouter du texte et une mise en forme à des cellules dans des tableaux Word par programmation](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Comment : ajouter des lignes et des colonnes à des tableaux Word par programmation](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Comment : remplir des tableaux Word avec des propriétés de document par programmation](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
