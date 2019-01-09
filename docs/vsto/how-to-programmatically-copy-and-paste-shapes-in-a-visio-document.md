---
title: 'Procédure : Copier et coller des formes dans un document Visio par programme'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b9b4f756c1b553f41f79dbbaaaf8a4c27bdfbc64
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093949"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Procédure : Copier et coller des formes dans un document Visio par programme
  Vous pouvez copier des formes par programmation sur une page d’un document, et les coller dans une nouvelle page du même document. Vous pouvez choisir de les coller à l’emplacement par défaut (au centre de la fenêtre active) ou aux mêmes coordonnées que dans la page d’origine.  
  
## <a name="copy-and-paste-shapes"></a>Copier et coller des formes  
 Pour plus d’informations sur le modèle objet, consultez la documentation de référence VBA sur les méthodes [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)et [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) , ainsi que sur l’indicateur [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) .  
  
### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Pour copier des formes au centre d’une autre page  
  
-   L’exemple suivant montre comment copier les formes de la première page, et les coller au centre de la seconde page.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Copier et coller des formes avec les mêmes positions  
 Pour plus d’informations sur le modèle objet, consultez la documentation de référence VBA sur les méthodes [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)et [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) , ainsi que sur l’indicateur [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) .  
  
 Si vous avez besoin contrôler le format des informations collées et (éventuellement) établir un lien vers un fichier source (par exemple, un document Microsoft Office Word), utilisez la méthode PasteSpecial.  
  
### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Pour copier des formes et des emplacements de forme vers une autre page  
  
-   L’exemple suivant montre comment copier les formes de la première page, et les coller au centre de la seconde page avec leurs coordonnées d’origine.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)   
 [Utilisez des formes Visio](../vsto/working-with-visio-shapes.md)   
 [Guide pratique pour Ajouter par programmation des formes à un document Visio](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
