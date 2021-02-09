---
title: Paramètres facultatifs dans les solutions Office
description: Découvrez comment vous n’êtes pas obligé de passer une valeur pour les paramètres facultatifs, car les valeurs par défaut sont automatiquement utilisées pour chaque paramètre manquant.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d6824d53d552a27a68a49d63497156147283fd29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847698"
---
# <a name="optional-parameters-in-office-solutions"></a>Paramètres facultatifs dans les solutions Office
  De nombreuses méthodes des modèles objet fournis dans les applications Microsoft Office acceptent les paramètres optionnels. Si vous utilisez Visual Basic pour développer une solution Office dans Visual Studio, vous n'avez pas besoin de passer de valeur pour les paramètres optionnels, car les valeurs par défaut sont automatiquement utilisées pour les paramètres manquants. Dans la plupart des cas, vous pouvez également omettre les paramètres optionnels dans les projets Visual C#. Toutefois, vous ne pouvez pas omettre les paramètres **ref** facultatifs de la `ThisDocument` classe dans les projets Word au niveau du document.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Pour plus d’informations sur l’utilisation des paramètres optionnels dans les projets Visual C# et Visual Basic, consultez [arguments nommés et facultatifs &#40;Guide de programmation C&#35;&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) et [paramètres facultatifs &#40;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)Visual Basic&#41;.

> [!NOTE]
> Dans les versions antérieures de Visual Studio, vous devez passer une valeur pour chaque paramètre optionnel défini dans les projets Visual C#. Pour des raisons pratiques, ces projets incluent une variable globale nommée `missing` que vous pouvez passer à un paramètre optionnel quand vous voulez utiliser la valeur par défaut du paramètre. Les projets Visual C# pour Office dans Visual Studio incluent toujours la `missing` variable, mais vous n’avez généralement pas besoin de l’utiliser lorsque vous développez des solutions Office dans [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , sauf lorsque vous appelez des méthodes avec des paramètres **ref** facultatifs dans la `ThisDocument` classe dans des projets au niveau du document pour Word.

## <a name="example-in-excel"></a>Exemple dans Excel
 La méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> possède de nombreux paramètres optionnels. Vous pouvez spécifier des valeurs pour certains paramètres et accepter la valeur par défaut pour d'autres, comme indiqué dans l'exemple de code suivant. Cet exemple utilise un projet de niveau document avec une classe de feuille de calcul nommée `Sheet1`.

 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]

## <a name="example-in-word"></a>Exemple dans Word
 La méthode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> possède de nombreux paramètres optionnels. Vous pouvez spécifier des valeurs pour certains paramètres et accepter la valeur par défaut pour d'autres, comme indiqué dans l'exemple de code suivant.

 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Utiliser des paramètres facultatifs de méthodes dans la classe ThisDocument dans les projets de niveau document Visual C# pour Word
 Le modèle objet Word contient de nombreuses méthodes avec des paramètres **ref** facultatifs qui acceptent des <xref:System.Object> valeurs. Toutefois, vous ne pouvez pas omettre les paramètres **ref** facultatifs des méthodes de la `ThisDocument` classe générée dans les projets de niveau document Visual C# pour Word. Visual C# vous permet d’omettre les paramètres **ref** facultatifs uniquement pour les méthodes d’interface, et non pour les classes. Par exemple, l’exemple de code suivant ne se compile pas, car vous ne pouvez pas omettre les paramètres **ref** facultatifs de la <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> méthode de la `ThisDocument` classe.

 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]

 Quand vous appelez des méthodes de la classe `ThisDocument`, suivez ces consignes :

- Pour accepter la valeur par défaut d’un paramètre **ref** facultatif, transmettez la `missing` variable au paramètre. La variable `missing` est automatiquement définie dans les projets Office Visual C# et est assignée à la valeur <xref:System.Type.Missing> dans le code de projet généré.

- Pour spécifier votre propre valeur pour un paramètre **ref** facultatif, déclarez un objet qui est assigné à la valeur que vous souhaitez spécifier, puis transmettez l’objet au paramètre.

  L’exemple de code suivant montre comment appeler la <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> méthode en spécifiant une valeur pour le paramètre *IgnoreUppercase* et en acceptant la valeur par défaut pour les autres paramètres.

  [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]

  Si vous souhaitez écrire du code qui omet les paramètres **ref** facultatifs d’une méthode dans la `ThisDocument` classe, vous pouvez également appeler la même méthode sur l' <xref:Microsoft.Office.Interop.Word.Document> objet retourné par la <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> propriété et omettre les paramètres de cette méthode. Vous pouvez faire cela dans la mesure où <xref:Microsoft.Office.Interop.Word.Document> est une interface, pas une classe.

  [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]

  Pour plus d’informations sur les paramètres de type valeur et référence, consultez [passer des arguments par valeur et par référence &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (pour Visual Basic) et [paramètres Pass &#40;guide de programmation&#35; C ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)&#41;.

## <a name="see-also"></a>Voir aussi
- [Développer des solutions Office](../vsto/developing-office-solutions.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
