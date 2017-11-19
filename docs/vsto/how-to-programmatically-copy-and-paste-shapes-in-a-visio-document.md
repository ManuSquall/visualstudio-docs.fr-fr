---
title: "Comment : copier par programmation et coller des formes dans un Document Visio | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
ms.assetid: 762d95cf-2d5c-4dea-988b-8f4da88fa1f1
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f3454a6514c22f1da82ef95407a0ff6be1fe442c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Comment : copier et coller des formes dans un document Visio par programmation
  Vous pouvez copier des formes par programmation sur une page d’un document, et les coller dans une nouvelle page du même document. Vous pouvez choisir de les coller à l’emplacement par défaut (au centre de la fenêtre active) ou aux mêmes coordonnées que dans la page d’origine.  
  
## <a name="copying-and-pasting-shapes"></a>Copie et collage de formes  
 Pour plus d’informations sur le modèle objet, consultez la documentation de référence VBA sur les méthodes [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)et [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) , ainsi que sur l’indicateur [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
#### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Pour copier des formes au centre d’une autre page  
  
-   L’exemple suivant montre comment copier les formes de la première page, et les coller au centre de la seconde page.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copying-and-pasting-shapes-with-the-same-positions"></a>Copie et collage de formes aux mêmes emplacements  
 Pour plus d’informations sur le modèle objet, consultez la documentation de référence VBA sur les méthodes [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)et [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) , ainsi que sur l’indicateur [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
 Si vous devez contrôler le format des informations collées et (éventuellement) établir un lien vers un fichier source (par exemple, un document Microsoft Office Word), utilisez la méthode PasteSpecial.  
  
#### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Pour copier des formes et des emplacements de forme vers une autre page  
  
-   L’exemple suivant montre comment copier les formes de la première page, et les coller au centre de la seconde page avec leurs coordonnées d’origine.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)   
 [Utilisation des formes Visio](../vsto/working-with-visio-shapes.md)   
 [Guide pratique pour ajouter des formes à un document Visio par programmation](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  