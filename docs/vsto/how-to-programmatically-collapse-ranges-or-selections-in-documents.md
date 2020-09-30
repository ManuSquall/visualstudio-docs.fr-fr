---
title: Réduire des plages ou des sélections dans des documents par programmation
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bb22f97b6a876029ff5d984abf9bda32cfd3fbc
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585286"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Comment : réduire des plages ou des sélections dans des documents par programmation
  Si vous travaillez avec un objet <xref:Microsoft.Office.Interop.Word.Range> ou <xref:Microsoft.Office.Interop.Word.Selection> , vous pouvez remplacer la sélection par un point d’insertion avant d’insérer du texte, afin d’éviter de remplacer le texte existant. Les deux <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> objets et ont une méthode Collapse, qui utilise les <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> valeurs d’énumération :

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> réduit la sélection au début de la sélection. Il s’agit de la valeur par défaut si vous ne spécifiez pas de valeur d’énumération.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> réduit la sélection à la fin de la sélection.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Pour réduire une plage et insérer un nouveau texte

1. Créez un objet <xref:Microsoft.Office.Interop.Word.Range> constitué du premier paragraphe du document.

    L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.

    [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]

    L'exemple de code suivant peut être utilisé dans un complément VSTO. Ce code utilise le document actif.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]

2. Utilisez la valeur d’énumération <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> pour réduire la plage.

    [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
    [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]

3. Insérez le nouveau texte.

    [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
    [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]

4. Sélectionnez <xref:Microsoft.Office.Interop.Word.Range>.

    [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
    [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]

   Si vous utilisez la valeur d’énumération <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> , le texte est inséré au début du paragraphe suivant.

   [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
   [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]

   Vous pourriez vous attendre à ce que l’insertion d’une nouvelle phrase se fasse avant la marque de paragraphe, mais ce n’est pas le cas, car celle-ci est incluse dans la plage d’origine. Pour plus d’informations, consultez [Comment : exclure par programmation des marques de paragraphe lors](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)de la création de plages.

## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Pour réduire une plage dans une personnalisation au niveau du document

1. L’exemple suivant montre la méthode complète d’une personnalisation au niveau du document. Pour utiliser ce code, exécutez-le à partir de la classe `ThisDocument` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]

## <a name="vsto-add-in-example"></a>Exemple de complément VSTO

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Pour réduire une plage dans un complément VSTO

1. L’exemple suivant montre la méthode complète d’un complément VSTO. Pour utiliser ce code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]

## <a name="see-also"></a>Voir aussi
- [Comment : insérer du texte dans des documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Comment : récupérer des caractères de début et de fin dans les plages par programmation](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Comment : exclure des marques de paragraphe lors de la création de plages par programmation](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Comment : réinitialiser des plages dans les documents Word par programmation](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
