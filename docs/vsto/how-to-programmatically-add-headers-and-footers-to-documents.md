---
title: 'Comment : ajouter des en-têtes et des pieds de page à des documents par programmation'
description: Découvrez comment ajouter du texte aux en-têtes et aux pieds de page de votre document à l’aide de la propriété en-têtes propriété et pieds de page de la section.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 73844d19ef6bb85c623706ab0d359836e42a3b14
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828740"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Comment : ajouter des en-têtes et des pieds de page à des documents par programmation
  Vous pouvez ajouter du texte aux en-têtes et pieds de page dans votre document à l'aide de la propriété <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> et de la propriété <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> de <xref:Microsoft.Office.Interop.Word.Section>. Chaque section d'un document contient trois en-têtes et pieds de page :

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>

  Les procédures sont différentes pour les personnalisations au niveau du document et les compléments VSTO.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customizations"></a>Personnalisations au niveau du document
 Pour utiliser les exemples de code suivants, exécutez-les à partir de la classe `ThisDocument` de votre projet.

### <a name="to-add-text-to-footers-in-the-document"></a>Pour ajouter du texte dans les pieds de page du document

1. L'exemple de code suivant définit la police du texte à insérer dans le pied de page principal de chaque section du document, puis insère le texte dans le pied de page.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Pour ajouter du texte dans les en-têtes du document

1. L'exemple de code suivant ajoute un champ pour afficher le numéro de page dans chaque en-tête du document, puis définit l'alignement du paragraphe afin d'aligner le texte à droite de l'en-tête.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet116":::

## <a name="vsto-add-ins"></a>Compléments VSTO
 Pour utiliser les exemples de code suivants, exécutez-les à partir de la classe `ThisAddIn` de votre projet.

### <a name="to-add-text-to-footers-in-a-document"></a>Pour ajouter du texte dans les pieds de page d'un document

1. L'exemple de code suivant définit la police du texte à insérer dans le pied de page principal de chaque section du document, puis insère le texte dans le pied de page. Cet exemple de code utilise le document actif.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Pour ajouter du texte dans les en-têtes du document

1. L'exemple de code suivant ajoute un champ pour afficher le numéro de page dans chaque en-tête du document, puis définit l'alignement du paragraphe afin d'aligner le texte à droite de l'en-tête. Cet exemple de code utilise le document actif.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet116":::

## <a name="see-also"></a>Voir aussi
- [Comment : créer des documents par programmation](../vsto/how-to-programmatically-create-new-documents.md)
- [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Comment : parcourir les éléments trouvés dans les documents par programmation](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
