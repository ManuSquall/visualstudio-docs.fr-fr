---
title: 'Comment : restaurer des sélections après des recherches par programmation'
description: Découvrez comment vous pouvez utiliser Visual Studio pour restaurer par programmation des sélections après les recherches dans un document Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2a9f804e218ec9dfa0e0550501dec0c1aa8388ff
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824012"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Comment : restaurer des sélections après des recherches par programmation
  Si vous recherchez et remplacez du texte dans un document, vous souhaiterez peut-être restaurer la sélection d’origine de l’utilisateur une fois la recherche terminée.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Le code de l’exemple de procédure utilise deux <xref:Microsoft.Office.Interop.Word.Range> objets. L’une stocke le en cours <xref:Microsoft.Office.Interop.Word.Selection> et l’autre définit le document entier à utiliser comme plage de recherche.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>Pour restaurer la sélection d’origine de l’utilisateur après une recherche

1. Créez les <xref:Microsoft.Office.Interop.Word.Range> objets pour le document et la sélection actuelle.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet83":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet83":::

2. Effectuez l’opération de recherche et de remplacement.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet84":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet84":::

3. Sélectionnez la plage de démarrage pour restaurer la sélection d’origine de l’utilisateur.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet85":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet85":::

   L'exemple suivant montre la méthode complète.

## <a name="example"></a>Exemple
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet82":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet82":::

## <a name="see-also"></a>Voir aussi
- [Comment : Rechercher et remplacer du texte dans des documents par programmation](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Comment : définir des options de recherche dans Word par programmation](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Comment : parcourir les éléments trouvés dans les documents par programmation](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
