---
title: 'Procédure : Insérer du texte dans les documents Word par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e04f3b4420cc8f3b56eee304ae199cf87fa4a3a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412575"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Procédure : Insérer du texte dans les documents Word par programmation
  Il existe trois principaux moyens pour insérer du texte dans des documents Microsoft Office Word :

- insérer du texte dans une plage ;

- remplacer du texte dans une plage par un nouveau texte ;

- utiliser la méthode <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Selection> pour insérer du texte au niveau du curseur ou de la sélection.

> [!NOTE]
> Vous pouvez également insérer du texte dans les contrôles de contenu et les signets. Pour plus d’informations, consultez [contrôles de contenu](../vsto/content-controls.md) et [Bookmark (contrôle)](../vsto/bookmark-control.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="insert-text-in-a-range"></a>Insérer du texte dans une plage
 Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Range> pour insérer du texte dans un document.

### <a name="to-insert-text-in-a-range"></a>Pour insérer du texte dans une plage

1. Spécifiez une plage au début d’un document et insérer le texte **New Text**.

     Vous pouvez utiliser l’exemple de code suivant dans une personnalisation au niveau du document.

     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]

     L'exemple de code suivant peut être utilisé dans un complément VSTO. Ce code utilise le document actif.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]

2. Sélectionnez l'objet <xref:Microsoft.Office.Interop.Word.Range> , qui s'est développé à partir d'un caractère jusqu'à la longueur correspondant au texte inséré.

     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]

## <a name="replace-text-in-a-range"></a>Remplacer du texte dans une plage
 Si la plage spécifiée contient du texte, tout le texte de la plage est remplacé par le texte inséré.

### <a name="to-replace-text-in-a-range"></a>Pour remplacer du texte dans une plage

1. Créez un objet <xref:Microsoft.Office.Interop.Word.Range> comprenant les 12 premiers caractères du document.

     Vous pouvez utiliser l’exemple de code suivant dans une personnalisation au niveau du document.

     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]

     L'exemple de code suivant peut être utilisé dans un complément VSTO. Ce code utilise le document actif.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]

2. Remplacez ces caractères par la chaîne **New Text**.

     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]

3. Sélectionnez la plage.

     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]

## <a name="insert-text-using-typetext"></a>Insérer du texte à l’aide de TypeText
 La méthode <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> insère du texte au niveau de la sélection. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> se comporte différemment selon les options définies sur l'ordinateur de l'utilisateur. Le code de la procédure suivante déclare une variable objet <xref:Microsoft.Office.Interop.Word.Selection> , puis désactive l'option **Overtype** , si elle est activée. Si l'option **Overtype** est activée, le texte situé à proximité du curseur est remplacé.

### <a name="to-insert-text-using-the-typetext-method"></a>Pour insérer du texte à l'aide de la méthode TypeText

1. Déclarez une variable objet <xref:Microsoft.Office.Interop.Word.Selection> .

    [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
    [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]

2. Désactivez l'option **Overtype** , si elle est activée.

    [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
    [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]

3. Vérifiez si la sélection actuelle est un point d'insertion.

    Si tel est le cas, le code insère une phrase à l'aide de <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>, puis une marque de paragraphe à l'aide de la méthode <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> .

    [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
    [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]

4. Le code du bloc **ElseIf** vérifie si la sélection est une sélection normale. Si tel est le cas, un autre bloc **If** vérifie si l'option **ReplaceSelection** est activée. Si tel est le cas, le code utilise la méthode <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> de la sélection pour réduire cette dernière à un point d'insertion au début du bloc de texte sélectionné. Insérez le texte et une marque de paragraphe.

    [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
    [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]

5. Si la sélection n'est pas un point d'insertion ou un bloc de texte sélectionné, le code du bloc **Else** ne fait rien.

    [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
    [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]

   Vous pouvez également utiliser le <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> méthode de la <xref:Microsoft.Office.Interop.Word.Selection> objet, qui reproduit la fonctionnalité de la **retour arrière** clé de votre clavier. Toutefois, quand il s'agit d'insérer et de manipuler du texte, l'objet <xref:Microsoft.Office.Interop.Word.Range> vous offre davantage de contrôle.

   L'exemple suivant montre le code complet. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisDocument` ou `ThisAddIn` dans votre projet.

   [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
   [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Formater le texte par programmation dans des documents](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Guide pratique pour Définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Guide pratique pour Étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
