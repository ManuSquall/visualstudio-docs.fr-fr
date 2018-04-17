---
title: 'Comment : ajouter par programme des images et des effets WordArt aux Documents | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7b8db629695e929dc257687e3bc73db6fc78b37e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Comment : ajouter des images et des effets WordArt aux documents par programmation
  Vous pouvez ajouter des images et des objets de dessin à vos documents au moment du design ou de l'exécution. WordArt vous permet d'ajouter du texte décoratif aux documents Microsoft Office Word. Ces effets de texte spéciaux sont des objets de dessin que vous pouvez personnaliser et insérer dans votre document.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="adding-a-picture-at-design-time"></a>Ajout d'une image au moment du design  
 Si vous développez une personnalisation au niveau du document, vous pouvez ajouter une image au document au moment du design.  
  
#### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Pour ajouter une image à un document Word au moment du design  
  
1.  Placez votre curseur à l'emplacement où vous souhaitez insérer l'image dans le document.  
  
2.  Cliquez sur le **insérer** onglet du ruban.  
  
3.  Dans le **Illustrations** , cliquez sur **image**.  
  
4.  Dans le **insérer une image** boîte de dialogue, accédez à l’image que vous souhaitez insérer, puis cliquez sur **insérer**.  
  
     L'image est ajoutée à votre document à l'emplacement du curseur.  
  
## <a name="adding-a-picture-at-run-time"></a>Ajout d'une image au moment de l'exécution  
 Vous pouvez insérer une image dans un document à l'emplacement du curseur.  
  
#### <a name="to-add-a-picture-at-the-cursor-location"></a>Pour ajouter une image à l'emplacement du curseur  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> de la collection <xref:Microsoft.Office.Interop.Word.InlineShapes> et passez-lui le nom du fichier.  
  
     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]  
  
## <a name="adding-wordart-at-design-time"></a>Ajout d'un objet WordArt au moment du design  
 Si vous développez une personnalisation au niveau du document, vous pouvez ajouter un objet WordArt au document au moment du design.  
  
#### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Pour ajouter un objet WordArt à un document Word au moment du design  
  
1.  Placez votre curseur à l'emplacement où vous souhaitez insérer l'objet WordArt dans le document.  
  
2.  Cliquez sur le **insérer** onglet du ruban.  
  
3.  Dans le **texte** , cliquez sur **WordArt**, puis sélectionnez un style WordArt.  
  
4.  Ajoutez le texte que vous souhaitez voir apparaître dans le document à la **modifier le texte WordArt** boîte de dialogue et cliquez sur **OK**.  
  
     Le texte est ajouté à votre document et le style WordArt sélectionné lui est appliqué.  
  
## <a name="adding-wordart-at-run-time"></a>Ajout d'un objet WordArt au moment de l'exécution  
 Vous pouvez insérer un objet WordArt dans un document à l'emplacement du curseur. La procédure est différente pour les personnalisations de niveau document et les compléments VSTO.  
  
#### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Pour ajouter un objet WordArt à l'emplacement du curseur dans une personnalisation au niveau du document  
  
1.  Obtenez la position gauche et supérieure de l'emplacement du curseur.  
  
     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]  
  
2.  Appelez la méthode <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Shapes> dans le document.  
  
     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]  
  
#### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Pour ajouter un objet WordArt à l’emplacement du curseur dans un complément VSTO  
  
1.  Obtenez la position gauche et supérieure de l'emplacement du curseur.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]  
  
2.  Appelez la méthode <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Shapes> du document actif (ou d'un autre document que vous spécifiez).  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Une image nommée **SamplePicture.jpg** doit exister sur le lecteur C.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : ouvrir des Documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Comment : insérer du texte dans des Documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Comment : restaurer des sélections après des recherches de par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Comment : enregistrer des Documents par programmation](../vsto/how-to-programmatically-save-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  