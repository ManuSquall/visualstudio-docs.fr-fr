---
title: Exclure les marques de paragraphe lors de la création de plages par programmation
description: Découvrez comment vous pouvez exclure par programmation les marques de paragraphe lors de la création de plages dans un document Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c0929ccf3bb2567099dc7f3b795ad2257da0edb3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825795"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Comment : exclure des marques de paragraphe lors de la création de plages par programmation
  Chaque fois que vous créez un objet <xref:Microsoft.Office.Interop.Word.Range> basé sur un paragraphe, tous les caractères non imprimables, comme les marques de paragraphe, sont inclus dans la plage. Vous pouvez insérer le texte d’un paragraphe source dans un paragraphe de destination. Si vous ne voulez pas fractionner le paragraphe de destination en paragraphes distincts, alors vous devez d’abord supprimer la marque de paragraphe du paragraphe source. De plus, dans la mesure où des informations de mise en forme sont stockées au sein de la marque de paragraphe, vous ne voulez peut-être pas l’inclure quand vous insérez la plage dans un paragraphe existant.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 L’exemple de procédure suivant déclare deux variables de chaîne, extrait le contenu des premier et deuxième paragraphes du document actif, puis intervertit leur contenu. L’exemple illustre ensuite la suppression de la marque de paragraphe de la plage à l’aide de la méthode <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> et l’insertion du texte à l’intérieur du paragraphe.

## <a name="to-control-paragraph-structure-when-inserting-text"></a>Pour contrôler la structure de paragraphe lors de l’insertion de texte

1. Créez deux variables de plage pour les premier et deuxième paragraphes, puis extrayez leur contenu à l’aide de la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> .

     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet27":::

     L’exemple de code suivant peut être utilisé dans un complément VSTO au niveau de l’application. Ce code utilise le document actif.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet27":::

2. Affectez la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> , en intervertissant le texte des deux paragraphes.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet28":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet28":::

3. Sélectionnez chaque plage une par une, puis effectuez une pause pour afficher les résultats dans une boîte de message.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet29":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet29":::

4. Ajustez `firstRange` à l’aide de la méthode <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> pour que la marque de paragraphe ne fasse plus partie de `firstRange`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet30":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet30":::

5. Remplacez le reste du texte dans le premier paragraphe, en affectant une nouvelle chaîne à la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> de la plage.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet31":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet31":::

6. Remplacez le texte dans `secondRange`, en incluant la marque de paragraphe.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet32":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet32":::

7. Sélectionnez `firstRange` et effectuez une pause pour afficher les résultats dans une boîte de message, puis procédez de la même façon avec `secondRange`.

     Étant donné que `firstRange` a été redéfini pour exclure la marque de paragraphe, la mise en forme d’origine du paragraphe est conservée. En revanche, une phrase a été insérée à la place de la marque de paragraphe dans `secondRange`, supprimant ainsi le paragraphe distinct.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet33":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet33":::

     Le contenu d’origine des deux plages a été enregistré sous forme de chaînes, donc vous pouvez rétablir le document à son état d’origine.

8. Réajustez `firstRange` pour inclure la marque de paragraphe à l’aide <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> de la méthode pour la position d’un caractère.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet34":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet34":::

9. Supprimez `secondRange`. Cette opération rétablit le paragraphe trois à sa position d’origine.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet35":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet35":::

10. Rétablissez le texte du paragraphe d’origine dans `firstRange`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet36":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet36":::

11. Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range> pour insérer le contenu du paragraphe deux d’origine après `firstRange`, puis sélectionnez `firstRange`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet37":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet37":::

## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document

### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Pour contrôler la structure de paragraphe lors de l’insertion de texte dans des personnalisations au niveau du document

1. L’exemple suivant montre la méthode complète d’une personnalisation au niveau du document. Pour utiliser ce code, exécutez-le à partir de la classe `ThisDocument` de votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet26":::

## <a name="vsto-add-in-example"></a>Exemple de complément VSTO

### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>Pour contrôler la structure de paragraphe lors de l’insertion de texte dans un complément VSTO

1. L’exemple suivant montre la méthode complète d’un complément VSTO. Pour utiliser ce code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet26":::

## <a name="see-also"></a>Voir aussi
- [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Comment : réduire des plages ou des sélections dans des documents par programmation](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Comment : insérer du texte dans des documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Comment : réinitialiser des plages dans les documents Word par programmation](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
