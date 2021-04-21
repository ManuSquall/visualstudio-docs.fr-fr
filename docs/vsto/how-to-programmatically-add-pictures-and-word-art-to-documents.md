---
title: Ajouter des images et des illustrations Word à des documents par programmation
description: Découvrez comment ajouter des images et des objets de dessin à vos documents au moment du design ou au moment de l’exécution.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 445857200dfb269dd71f7cb3d446d025048cb3ac
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828434"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Comment : ajouter des images et des mots WordArt à des documents par programmation
  Vous pouvez ajouter des images et des objets de dessin à vos documents au moment du design ou de l'exécution. WordArt vous permet d'ajouter du texte décoratif aux documents Microsoft Office Word. Ces effets de texte spéciaux sont des objets de dessin que vous pouvez personnaliser et insérer dans votre document.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Ajouter une image au moment du design
 Si vous développez une personnalisation au niveau du document, vous pouvez ajouter une image au document au moment du design.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Pour ajouter une image à un document Word au moment du design

1. Placez votre curseur à l'emplacement où vous souhaitez insérer l'image dans le document.

2. Cliquez sur l’onglet **Insérer** du ruban.

3. Dans le groupe **illustrations** , cliquez sur **image**.

4. Dans la boîte de dialogue **Insérer une image** , accédez à l’image que vous souhaitez insérer, puis cliquez sur **Insérer**.

     L'image est ajoutée à votre document à l'emplacement du curseur.

## <a name="add-a-picture-at-run-time"></a>Ajouter une image au moment de l’exécution
 Vous pouvez insérer une image dans un document à l'emplacement du curseur.

### <a name="to-add-a-picture-at-the-cursor-location"></a>Pour ajouter une image à l'emplacement du curseur

1. Appelez la méthode <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> de la collection <xref:Microsoft.Office.Interop.Word.InlineShapes> et passez-lui le nom du fichier.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet108":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet108":::

## <a name="add-wordart-at-design-time"></a>Ajouter un objet WordArt au moment du design
 Si vous développez une personnalisation au niveau du document, vous pouvez ajouter un objet WordArt au document au moment du design.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Pour ajouter un objet WordArt à un document Word au moment du design

1. Placez votre curseur à l'emplacement où vous souhaitez insérer l'objet WordArt dans le document.

2. Cliquez sur l’onglet **Insérer** du ruban.

3. Dans le groupe **texte** , cliquez sur **WordArt**, puis sélectionnez un style WordArt.

4. Ajoutez le texte que vous souhaitez voir apparaître dans le document dans la boîte de dialogue **modifier le texte WordArt** , puis cliquez sur **OK**.

     Le texte est ajouté à votre document et le style WordArt sélectionné lui est appliqué.

## <a name="add-wordart-at-run-time"></a>Ajouter un objet WordArt au moment de l’exécution
 Vous pouvez insérer un objet WordArt dans un document à l'emplacement du curseur. La procédure est différente pour les personnalisations de niveau document et les compléments VSTO.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Pour ajouter un objet WordArt à l'emplacement du curseur dans une personnalisation au niveau du document

1. Obtenez la position gauche et supérieure de l'emplacement du curseur.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet109":::

2. Appelez la méthode <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Shapes> dans le document.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet110":::

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Pour ajouter un objet WordArt à l’emplacement du curseur dans un complément VSTO

1. Obtenez la position gauche et supérieure de l'emplacement du curseur.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet109":::

2. Appelez la méthode <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Shapes> du document actif (ou d'un autre document que vous spécifiez).

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet110":::

## <a name="compile-the-code"></a>Compiler le code

- Une image nommée *SamplePicture.jpg* doit exister sur le lecteur C.

## <a name="see-also"></a>Voir aussi
- [Comment : ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)
- [Comment : insérer du texte dans des documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Comment : restaurer des sélections après des recherches par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Comment : enregistrer des documents par programmation](../vsto/how-to-programmatically-save-documents.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
