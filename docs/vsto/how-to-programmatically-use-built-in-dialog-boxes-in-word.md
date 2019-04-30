---
title: 'Procédure : Utiliser par programmation les boîtes de dialogue intégrées dans Word'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: f8037e4d91aa7706c7ffd7b9f32778dfeac79488
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961639"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Procédure : Utiliser par programmation les boîtes de dialogue intégrées dans Word
  Lorsque vous travaillez avec Microsoft Office Word, voici les heures lorsque vous avez besoin pour afficher des boîtes de dialogue pour l’entrée utilisateur. Bien que vous pouvez créer votre propre, vous souhaiterez également adoptez l’approche de l’utilisation des boîtes de dialogue intégrées dans Word, qui sont exposés dans le <xref:Microsoft.Office.Interop.Word.Dialogs> collection de la <xref:Microsoft.Office.Interop.Word.Application> objet. Cela permet d’accéder à plus de 200 des boîtes de dialogue, qui sont représentées en tant qu’énumérations.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Afficher des boîtes de dialogue
 Pour afficher une boîte de dialogue, utilisez une des valeurs de la <xref:Microsoft.Office.Interop.Word.WdWordDialog> énumération pour créer un <xref:Microsoft.Office.Interop.Word.Dialog> objet qui représente la boîte de dialogue que vous souhaitez afficher. Ensuite, appelez le <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> méthode de la <xref:Microsoft.Office.Interop.Word.Dialog> objet.

 L’exemple de code suivant montre comment afficher le **ouvrir le fichier** boîte de dialogue. Pour utiliser cet exemple, exécutez-le à partir de la `ThisDocument` ou `ThisAddIn` classe dans votre projet.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Membres de boîte de dialogue accès sont disponibles via la liaison tardive
 Certaines propriétés et méthodes des boîtes de dialogue dans Word sont disponibles uniquement par le biais de la liaison tardive. En Visual Basic, projets où **Option Strict** est activé, vous devez utiliser la réflexion pour accéder à ces membres. Pour plus d’informations, consultez [la liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md).

 L’exemple de code suivant montre comment utiliser le **nom** propriété de la **ouvrir le fichier** boîte de dialogue dans Visual Basic projets où **Option Strict** est sous tension ou en Visual c# les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Pour utiliser cet exemple, exécutez-le à partir de la `ThisDocument` ou `ThisAddIn` classe dans votre projet.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 L’exemple de code suivant montre comment utiliser la réflexion pour accéder à la **nom** propriété de la **ouvrir le fichier** boîte de dialogue dans Visual Basic projets où **Option Strict** est sur. Pour utiliser cet exemple, exécutez-le à partir de la `ThisDocument` ou `ThisAddIn` classe dans votre projet.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Utiliser par programmation les boîtes de dialogue Word en mode masqué](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Vue d’ensemble du modèle d’objet Word](../vsto/word-object-model-overview.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
- [Option strict, instruction](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Réflexion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Réflexion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
