---
title: 'Comment : parcourir les éléments trouvés dans les documents par programmation'
description: Découvrez comment vous pouvez parcourir par programmation les éléments trouvés dans un document Microsoft Word à l’aide de Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- loops, through found items in documents
- documents [Office development in Visual Studio], searching
- text [Office development in Visual Studio], searching in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ce3153eb4e2fd7fd44318097a6b76ef6e0346086
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827342"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Comment : parcourir les éléments trouvés dans les documents par programmation
  La classe <xref:Microsoft.Office.Interop.Word.Find> a une propriété <xref:Microsoft.Office.Interop.Word.Find.Found%2A> , qui retourne **true** chaque fois qu’un élément recherché est trouvé. Vous pouvez exécuter en boucle toutes les instances trouvées dans un <xref:Microsoft.Office.Interop.Word.Range> à l’aide de la méthode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>Pour exécuter en boucle les éléments trouvés

1. Déclarez un objet <xref:Microsoft.Office.Interop.Word.Range> .

    L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet79":::

    L'exemple de code suivant peut être utilisé dans un complément VSTO. Cet exemple utilise le document actif.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet79":::

2. Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Find.Found%2A> d’une boucle pour rechercher toutes les occurrences de la chaîne dans le document, puis incrémentez une variable entière de 1 chaque fois que la chaîne est trouvée.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet80":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet80":::

3. Affichez le nombre de fois où que la chaîne a été trouvée dans une boîte de message.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet81":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet81":::

   Les exemples suivants montrent la méthode complète.

## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document

### <a name="to-loop-through-items-in-a-document-level-customization"></a>Pour exécuter en boucle les éléments d’une personnalisation au niveau du document

1. L'exemple suivant montre le code complet pour une personnalisation au niveau du document. Pour utiliser ce code, exécutez-le à partir de la classe `ThisDocument` de votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet78":::

## <a name="vsto-add-in-example"></a>Exemple de complément VSTO

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>Pour parcourir les éléments d’un complément VSTO

1. L'exemple suivant montre le code complet pour un complément VSTO. Pour utiliser ce code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet78":::

## <a name="see-also"></a>Voir aussi
- [Comment : Rechercher et remplacer des Rext dans des documents par programmation](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Comment : définir des options de recherche dans Word par programmation](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Comment : restaurer des sélections après des recherches par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
