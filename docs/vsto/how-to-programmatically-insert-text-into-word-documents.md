---
title: 'Comment : insérer du texte dans des documents Word par programmation'
description: Découvrez comment vous pouvez insérer du texte dans un document Microsoft Word à l’aide de Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f17828b4617f84cb104761918787b4bbb79f7afc
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827355"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Comment : insérer du texte dans des documents Word par programmation
  Il existe trois principaux moyens pour insérer du texte dans des documents Microsoft Office Word :

- insérer du texte dans une plage ;

- remplacer du texte dans une plage par un nouveau texte ;

- utiliser la méthode <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Selection> pour insérer du texte au niveau du curseur ou de la sélection.

> [!NOTE]
> Vous pouvez également insérer du texte dans les contrôles de contenu et les signets. Pour plus d’informations, consultez [contrôles de contenu](../vsto/content-controls.md) et contrôle de [signet](../vsto/bookmark-control.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="insert-text-in-a-range"></a>Insérer du texte dans une plage
 Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Range> pour insérer du texte dans un document.

### <a name="to-insert-text-in-a-range"></a>Pour insérer du texte dans une plage

1. Spécifiez une plage au début d’un document et insérer le texte **New Text**.

     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet51":::

     L'exemple de code suivant peut être utilisé dans un complément VSTO. Ce code utilise le document actif.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet51":::

2. Sélectionnez l'objet <xref:Microsoft.Office.Interop.Word.Range> , qui s'est développé à partir d'un caractère jusqu'à la longueur correspondant au texte inséré.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet52":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet52":::

## <a name="replace-text-in-a-range"></a>Remplacer du texte dans une plage
 Si la plage spécifiée contient du texte, tout le texte de la plage est remplacé par le texte inséré.

### <a name="to-replace-text-in-a-range"></a>Pour remplacer du texte dans une plage

1. Créez un objet <xref:Microsoft.Office.Interop.Word.Range> comprenant les 12 premiers caractères du document.

     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet53":::

     L'exemple de code suivant peut être utilisé dans un complément VSTO. Ce code utilise le document actif.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet53":::

2. Remplacez ces caractères par la chaîne **New Text**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet54":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet54":::

3. Sélectionnez la plage.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet55":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet55":::

## <a name="insert-text-using-typetext"></a>Insérer du texte à l’aide de TypeText
 La méthode <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> insère du texte au niveau de la sélection. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> se comporte différemment selon les options définies sur l'ordinateur de l'utilisateur. Le code de la procédure suivante déclare une variable objet <xref:Microsoft.Office.Interop.Word.Selection> , puis désactive l'option **Overtype** , si elle est activée. Si l'option **Overtype** est activée, le texte situé à proximité du curseur est remplacé.

### <a name="to-insert-text-using-the-typetext-method"></a>Pour insérer du texte à l'aide de la méthode TypeText

1. Déclarez une variable objet <xref:Microsoft.Office.Interop.Word.Selection>,

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet57":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet57":::

2. Désactivez l'option **Overtype** , si elle est activée.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet58":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet58":::

3. Vérifiez si la sélection actuelle est un point d'insertion.

    Si tel est le cas, le code insère une phrase à l'aide de <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>, puis une marque de paragraphe à l'aide de la méthode <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> .

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet59":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet59":::

4. Le code du bloc **ElseIf** vérifie si la sélection est une sélection normale. Si tel est le cas, un autre bloc **If** vérifie si l'option **ReplaceSelection** est activée. Si tel est le cas, le code utilise la méthode <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> de la sélection pour réduire cette dernière à un point d'insertion au début du bloc de texte sélectionné. Insérez le texte et une marque de paragraphe.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet60":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet60":::

5. Si la sélection n'est pas un point d'insertion ou un bloc de texte sélectionné, le code du bloc **Else** ne fait rien.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet61":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet61":::

   Vous pouvez également utiliser la <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> méthode de l' <xref:Microsoft.Office.Interop.Word.Selection> objet, qui reproduit la fonctionnalité de la touche **retour arrière** de votre clavier. Toutefois, quand il s'agit d'insérer et de manipuler du texte, l'objet <xref:Microsoft.Office.Interop.Word.Range> vous offre davantage de contrôle.

   L'exemple suivant montre le code complet. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisDocument` ou `ThisAddIn` dans votre projet.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet56":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet56":::

## <a name="see-also"></a>Voir aussi
- [Comment : mettre en forme du texte dans des documents par programmation](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
