---
title: 'Procédure : Ajouter par programmation des images et des effets WordArt aux documents'
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f805153a35517c473e95beb871ae7d12a2776bd4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967606"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Procédure : Ajouter par programmation des images et des effets WordArt aux documents
  Vous pouvez ajouter des images et des objets de dessin à vos documents au moment du design ou de l'exécution. WordArt vous permet d'ajouter du texte décoratif aux documents Microsoft Office Word. Ces effets de texte spéciaux sont des objets de dessin que vous pouvez personnaliser et insérer dans votre document.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Ajouter une image au moment du design
 Si vous développez une personnalisation au niveau du document, vous pouvez ajouter une image au document au moment du design.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Pour ajouter une image à un document Word au moment du design

1. Placez votre curseur à l'emplacement où vous souhaitez insérer l'image dans le document.

2. Cliquez sur le **insérer** onglet du ruban.

3. Dans le **Illustrations** de groupe, cliquez sur **image**.

4. Dans le **insérer une image** boîte de dialogue, accédez à l’image que vous souhaitez insérer, puis cliquez sur **insérer**.

     L'image est ajoutée à votre document à l'emplacement du curseur.

## <a name="add-a-picture-at-runtime"></a>Ajouter une image lors de l’exécution
 Vous pouvez insérer une image dans un document à l'emplacement du curseur.

### <a name="to-add-a-picture-at-the-cursor-location"></a>Pour ajouter une image à l'emplacement du curseur

1. Appelez la méthode <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> de la collection <xref:Microsoft.Office.Interop.Word.InlineShapes> et passez-lui le nom du fichier.

     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]

## <a name="add-wordart-at-design-time"></a>Ajouter un objet WordArt au moment du design
 Si vous développez une personnalisation au niveau du document, vous pouvez ajouter un objet WordArt au document au moment du design.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Pour ajouter un objet WordArt à un document Word au moment du design

1. Placez votre curseur à l'emplacement où vous souhaitez insérer l'objet WordArt dans le document.

2. Cliquez sur le **insérer** onglet du ruban.

3. Dans le **texte** de groupe, cliquez sur **WordArt**, puis sélectionnez un style WordArt.

4. Ajoutez le texte que vous souhaitez voir apparaître dans le document à la **modification du texte WordArt** boîte de dialogue et cliquez sur **OK**.

     Le texte est ajouté à votre document et le style WordArt sélectionné lui est appliqué.

## <a name="add-wordart-at-runtime"></a>Ajouter un objet WordArt lors de l’exécution
 Vous pouvez insérer un objet WordArt dans un document à l'emplacement du curseur. La procédure est différente pour les personnalisations de niveau document et les compléments VSTO.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Pour ajouter un objet WordArt à l'emplacement du curseur dans une personnalisation au niveau du document

1. Obtenez la position gauche et supérieure de l'emplacement du curseur.

     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]

2. Appelez la méthode <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Shapes> dans le document.

     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Pour ajouter un objet WordArt à l’emplacement du curseur dans un complément VSTO

1. Obtenez la position gauche et supérieure de l'emplacement du curseur.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]

2. Appelez la méthode <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Shapes> du document actif (ou d'un autre document que vous spécifiez).

     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]

## <a name="compile-the-code"></a>Compiler le code

- Une image nommée *SamplePicture.jpg* doit exister sur le lecteur C.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)
- [Guide pratique pour Insérer du texte dans les documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Guide pratique pour Restaurer des sélections après des recherches par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Guide pratique pour Enregistrer des documents par programmation](../vsto/how-to-programmatically-save-documents.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
