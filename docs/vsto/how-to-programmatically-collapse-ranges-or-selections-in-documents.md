---
title: Réduire des plages ou des sélections dans des documents par programmation
description: Sachez que si vous utilisez un objet Range ou Selection, vous souhaiterez peut-être remplacer la sélection par un point d’insertion avant d’insérer du texte.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5d1fb41943690da5144fb06245ed7f4aa70250aa
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828642"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Comment : réduire des plages ou des sélections dans des documents par programmation
  Si vous travaillez avec un objet <xref:Microsoft.Office.Interop.Word.Range> ou <xref:Microsoft.Office.Interop.Word.Selection> , vous pouvez remplacer la sélection par un point d’insertion avant d’insérer du texte, afin d’éviter de remplacer le texte existant. Les deux <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> objets et ont une méthode Collapse, qui utilise les <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> valeurs d’énumération :

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> réduit la sélection au début de la sélection. Il s’agit de la valeur par défaut si vous ne spécifiez pas de valeur d’énumération.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> réduit la sélection à la fin de la sélection.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Pour réduire une plage et insérer un nouveau texte

1. Créez un objet <xref:Microsoft.Office.Interop.Word.Range> constitué du premier paragraphe du document.

    L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet46":::

    L'exemple de code suivant peut être utilisé dans un complément VSTO. Ce code utilise le document actif.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet46":::

2. Utilisez la valeur d’énumération <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> pour réduire la plage.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet47":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet47":::

3. Insérez le nouveau texte.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet48":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet48":::

4. Sélectionnez <xref:Microsoft.Office.Interop.Word.Range>.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet49":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet49":::

   Si vous utilisez la valeur d’énumération <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> , le texte est inséré au début du paragraphe suivant.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet50":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet50":::

   Vous pourriez vous attendre à ce que l’insertion d’une nouvelle phrase se fasse avant la marque de paragraphe, mais ce n’est pas le cas, car celle-ci est incluse dans la plage d’origine. Pour plus d’informations, consultez [Comment : exclure par programmation des marques de paragraphe lors](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)de la création de plages.

## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Pour réduire une plage dans une personnalisation au niveau du document

1. L’exemple suivant montre la méthode complète d’une personnalisation au niveau du document. Pour utiliser ce code, exécutez-le à partir de la classe `ThisDocument` de votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet45":::

## <a name="vsto-add-in-example"></a>Exemple de complément VSTO

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Pour réduire une plage dans un complément VSTO

1. L’exemple suivant montre la méthode complète d’un complément VSTO. Pour utiliser ce code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet45":::

## <a name="see-also"></a>Voir aussi
- [Comment : insérer du texte dans des documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Comment : récupérer des caractères de début et de fin dans les plages par programmation](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Comment : exclure des marques de paragraphe lors de la création de plages par programmation](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Comment : réinitialiser des plages dans les documents Word par programmation](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
