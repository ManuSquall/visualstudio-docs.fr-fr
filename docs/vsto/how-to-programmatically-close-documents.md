---
title: 'Procédure : Fermer des documents par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dd5e73a272243aeb2ddc38ea5c2f49bb1b62e6a0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598360"
---
# <a name="how-to-programmatically-close-documents"></a>Procédure : Fermer des documents par programmation
  Vous pouvez fermer le document actif ou spécifier un document à fermer.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="close-the-active-document"></a>Fermer le document actif
 Il existe deux procédures distinctes pour fermer le document actif : une pour les personnalisations au niveau du document et une autre pour les compléments VSTO.

### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Pour fermer le document actif dans une personnalisation au niveau du document

1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.Close%2A> de la classe `ThisDocument` dans votre projet pour fermer le document associé à la personnalisation. Pour utiliser l'exemple de code suivant, exécutez-le à partir de la classe `ThisDocument` .

    > [!NOTE]
    >  Cet exemple transmet la valeur <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> au paramètre *SaveChanges* afin de fermer sans enregistrement des modifications apportées ou sans validation de l'utilisateur.

     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]

### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>Pour fermer le document actif dans un complément VSTO

1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.Close%2A> de la propriété <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> pour fermer le document actif. Pour utiliser l'exemple de code suivant, exécutez-le à partir de la classe `ThisAddIn` de votre projet.

    > [!NOTE]
    >  Cet exemple transmet la valeur <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> au paramètre *SaveChanges* afin de fermer sans enregistrement des modifications apportées ou sans validation de l'utilisateur.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]

## <a name="close-a-document-that-you-specify-by-name"></a>Fermer un document que vous spécifiez par nom
 La procédure de fermeture d’un document dont vous spécifiez le nom est la même pour les compléments VSTO et les personnalisations au niveau du document.

### <a name="to-close-a-document-that-you-specify-by-name"></a>Pour fermer un document dont vous spécifiez le nom

1.  Spécifiez le nom du document comme argument à la collection <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> , puis appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.Close%2A> . L’exemple de code suivant suppose qu’un document nommé **NewDocument** est ouvert dans Word.

    > [!NOTE]
    >  Cet exemple transmet la valeur <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> au paramètre *SaveChanges* afin de fermer sans enregistrement des modifications apportées ou sans validation de l'utilisateur.

     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)
- [Guide pratique pour Enregistrer des documents par programmation](../vsto/how-to-programmatically-save-documents.md)
- [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
