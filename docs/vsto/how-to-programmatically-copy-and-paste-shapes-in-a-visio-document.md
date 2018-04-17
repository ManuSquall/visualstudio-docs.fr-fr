---
title: 'Comment : copier par programmation et coller des formes dans un Document Visio | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 488cda5519a211754498b50a88995de64a8ed366
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
  