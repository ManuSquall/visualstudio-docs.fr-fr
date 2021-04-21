---
title: 'Comment : afficher une chaîne dans une cellule de feuille de calcul par programmation'
description: Découvrez comment vous pouvez afficher par programmation une chaîne dans une cellule de feuille de calcul Microsoft Excel à l’aide d’un contrôle NamedRange ou d’un objet de plage Excel natif.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8a7bc48df6e30381ff275b9f11dabe04a25d6dd7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825925"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Comment : afficher une chaîne dans une cellule de feuille de calcul par programmation
  Cet exemple montre comment afficher du texte dans une cellule par programmation. Pour afficher du texte dans une cellule, utilisez un objet de type <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou une plage Excel native.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Utiliser un contrôle NamedRange
 Cet exemple utilise un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle nommé `message` . Le contrôle doit être ajouté à une personnalisation au niveau du document au moment du Design. Le code suivant doit être placé dans une classe Sheet et non dans la `ThisWorkbook` classe.

### <a name="to-display-text-in-a-namedrange-control"></a>Pour afficher du texte dans un contrôle NamedRange

1. Définissez la valeur du <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle sur **Hello World**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet68":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet68":::

## <a name="use-a-native-excel-range"></a>Utiliser une plage Excel Native
 Le code suivant crée une nouvelle plage par programme, puis lui assigne une valeur.

### <a name="to-display-text-in-an-excel-range"></a>Pour afficher du texte dans une plage Excel

1. Récupérez la plage à la cellule **a1** `Sheet1` et définissez la valeur sur **Hello World**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet69":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet69":::

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : collecter des données à l’aide d’un Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Résoudre les problèmes des solutions Office](../vsto/troubleshooting-office-solutions.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
