---
title: 'Comment : utiliser des boîtes de dialogue intégrées dans Word par programmation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c3273b22d98be1c22cf0c8cea2cb57e277b9b48
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537616"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Comment : utiliser des boîtes de dialogue intégrées dans Word par programmation
  Lorsque vous travaillez avec Microsoft Office Word, vous devez parfois afficher des boîtes de dialogue pour les entrées utilisateur. Bien que vous puissiez créer les vôtres, vous souhaiterez peut-être également utiliser les boîtes de dialogue intégrées dans Word, qui sont exposées dans la <xref:Microsoft.Office.Interop.Word.Dialogs> collection de l' <xref:Microsoft.Office.Interop.Word.Application> objet. Cela vous permet d’accéder à plus de 200 des boîtes de dialogue prédéfinies, qui sont représentées en tant qu’énumérations.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Afficher les boîtes de dialogue
 Pour afficher une boîte de dialogue, utilisez l’une des valeurs de l' <xref:Microsoft.Office.Interop.Word.WdWordDialog> énumération pour créer un <xref:Microsoft.Office.Interop.Word.Dialog> objet qui représente la boîte de dialogue que vous souhaitez afficher. Ensuite, appelez la <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> méthode de l' <xref:Microsoft.Office.Interop.Word.Dialog> objet.

 L’exemple de code suivant montre comment afficher la boîte de dialogue **ouvrir un fichier** . Pour utiliser cet exemple, exécutez-le à partir de la `ThisDocument` `ThisAddIn` classe ou de votre projet.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Accéder aux membres de la boîte de dialogue qui sont disponibles via une liaison tardive
 Certaines propriétés et méthodes des boîtes de dialogue dans Word sont disponibles uniquement via la liaison tardive. Dans Visual Basic projets où **option strict** a la valeur on, vous devez utiliser la réflexion pour accéder à ces membres. Pour plus d’informations, consultez [liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md).

 L’exemple de code suivant montre comment utiliser la propriété **Name** de la boîte de dialogue d' **ouverture de fichier** dans Visual Basic projets où **option strict** a la valeur OFF ou dans les projets Visual C# qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Pour utiliser cet exemple, exécutez-le à partir de la `ThisDocument` `ThisAddIn` classe ou de votre projet.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 L’exemple de code suivant montre comment utiliser la réflexion pour accéder à la propriété **Name** de la boîte de dialogue d' **ouverture de fichier** dans Visual Basic projets où **option strict** a la valeur on. Pour utiliser cet exemple, exécutez-le à partir de la `ThisDocument` `ThisAddIn` classe ou de votre projet.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Voir aussi
- [Comment : utiliser des boîtes de dialogue Word en mode masqué par programmation](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
- [Option strict, instruction](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Réflexion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Réflexion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
