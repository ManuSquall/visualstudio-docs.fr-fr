---
title: 'Comment : compter des caractères dans les documents par programmation'
description: Découvrez comment vous pouvez déterminer le nombre de caractères dans un document à l’aide de la propriété Count de la collection Characters.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68ddc86183eacd7f76e39bb06e47968c0129849c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824001"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Comment : compter des caractères dans les documents par programmation
  Le premier caractère dans un document est à la position de caractère 0, qui représente le point d’insertion. La position du dernier caractère est égale au nombre total de caractères dans le document. Vous pouvez déterminer le nombre de caractères dans un document à l’aide de la propriété <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> de la collection <xref:Microsoft.Office.Interop.Word.Characters> .

 Tous les caractères du document sont comptés, y compris les espaces, les marques de paragraphe et autres caractères normalement masqués. Même un document vide retourne un nombre de caractères égal à « 1 », car il contient une marque de paragraphe.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Pour afficher le nombre de caractères dans une personnalisation au niveau du document

1. Sélectionnez tout le document.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet98":::

2. Affichez le nombre de caractères dans le document dans une boîte de message.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet99":::

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Pour afficher le nombre de caractères dans un complément VSTO

1. Sélectionnez tout le document. L’exemple suivant sélectionne le document actif.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet98":::

2. Affichez le nombre de caractères dans le document dans une boîte de message.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet99":::

## <a name="see-also"></a>Voir aussi
- [Comment : récupérer des caractères de début et de fin dans les plages par programmation](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
