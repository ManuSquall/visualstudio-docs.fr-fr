---
title: Copier et coller des formes dans un document Visio par programmation
description: Découvrez comment vous pouvez copier des formes par programmation sur une page d’un document et les coller dans une nouvelle page du même document.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b7cda46330967ef2b2b08db2109a030bbef8cace
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828551"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Comment : copier et coller des formes dans un document Visio par programmation
  Vous pouvez copier des formes par programmation sur une page d’un document, et les coller dans une nouvelle page du même document. Vous pouvez choisir de les coller à l’emplacement par défaut (au centre de la fenêtre active) ou aux mêmes coordonnées que dans la page d’origine.

## <a name="copy-and-paste-shapes"></a>Copier et coller des formes
 Pour plus d’informations sur le modèle objet, consultez la documentation de référence VBA sur les méthodes [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)et [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) , ainsi que sur l’indicateur [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) .

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Pour copier des formes au centre d’une autre page

- L’exemple suivant montre comment copier les formes de la première page, et les coller au centre de la seconde page.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet14":::

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Copier et coller des formes avec les mêmes positions
 Pour plus d’informations sur le modèle objet, consultez la documentation de référence VBA sur les méthodes [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)et [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) , ainsi que sur l’indicateur [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) .

 Si vous devez contrôler le format des informations collées et (éventuellement) établir un lien vers un fichier source (par exemple, un Microsoft Office document Word), utilisez la méthode PasteSpecial.

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Pour copier des formes et des emplacements de forme vers une autre page

- L’exemple suivant montre comment copier les formes de la première page, et les coller au centre de la seconde page avec leurs coordonnées d’origine.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>Voir aussi
- [Solutions Visio](../vsto/visio-solutions.md)
- [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)
- [Utiliser des formes Visio](../vsto/working-with-visio-shapes.md)
- [Comment : ajouter des formes à un document Visio par programmation](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
