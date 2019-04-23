---
title: 'Procédure : Réinitialisation par programmation des plages dans des documents Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 622d807da832c4c07baf8b62c902c2b1d25cc14d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072069"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Procédure : Réinitialisation par programmation des plages dans des documents Word
  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> pour redimensionner une plage existante dans un document Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>Pour réinitialiser une plage existante

1. Définissez une plage initiale commençant par les sept premiers caractères du document.

     Vous pouvez utiliser l’exemple de code suivant dans une personnalisation au niveau du document.

     [!code-vb[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#43)]

     L'exemple de code suivant peut être utilisé dans un complément VSTO. Ce code utilise le document actif.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#43)]

2. Utilisez <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> pour commencer la plage au niveau de la deuxième phrase et la terminer à la fin de la cinquième phrase.

     [!code-vb[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#44)]
     [!code-csharp[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#44)]

## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Pour réinitialiser une plage existante dans une personnalisation au niveau du document

1. L’exemple suivant montre le code complet pour une personnalisation au niveau du document. Pour utiliser ce code, exécutez-le à partir de la classe `ThisDocument` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#42)]

## <a name="vsto-add-in-example"></a>Exemple de complément VSTO

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>Pour réinitialiser une plage existante dans un complément, VSTO

1. L’exemple suivant montre un exemple complet pour un composant logiciel complément VSTO. Pour utiliser ce code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#42)]

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Guide pratique pour Définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Guide pratique pour Récupérer par programme des caractères de début et de fin dans les plages](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Guide pratique pour Réduire des plages ou des sélections dans des documents par programmation](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
