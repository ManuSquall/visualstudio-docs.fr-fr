---
title: 'Procédure : Compter les caractères dans les documents par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb4bbb124575346c930fa5539801deb3c9981cac
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102170"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Procédure : Compter les caractères dans les documents par programmation
  Le premier caractère dans un document est à la position de caractère 0, qui représente le point d’insertion. La position du dernier caractère est égale au nombre total de caractères dans le document. Vous pouvez déterminer le nombre de caractères dans un document à l’aide de la propriété <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> de la collection <xref:Microsoft.Office.Interop.Word.Characters> .

 Tous les caractères du document sont comptés, y compris les espaces, les marques de paragraphe et autres caractères normalement masqués. Même un document vide retourne un nombre de caractères égal à « 1 », car il contient une marque de paragraphe.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Pour afficher le nombre de caractères dans une personnalisation au niveau du document

1. Sélectionnez tout le document.

     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]

2. Affichez le nombre de caractères dans le document dans une boîte de message.

     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Pour afficher le nombre de caractères dans un complément, VSTO

1. Sélectionnez tout le document. L’exemple suivant sélectionne le document actif.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]

2. Affichez le nombre de caractères dans le document dans une boîte de message.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Récupérer par programme des caractères de début et de fin dans les plages](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Guide pratique pour Définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
