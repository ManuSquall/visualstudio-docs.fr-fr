---
title: Protéger des documents et des parties de documents par programmation
description: Découvrez comment vous pouvez ajouter une protection aux documents Microsoft Word pour empêcher les utilisateurs d’apporter des modifications au document.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af3cc1d9c34bf0d6dc503ca2aabe35de5848265c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827602"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Comment : protéger des documents et des parties de documents par programmation
  Vous pouvez ajouter une protection aux documents Microsoft Office Word pour empêcher les utilisateurs d’y apporter des modifications.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Vous pouvez également marquer certaines zones du document comme des exceptions, pour que les utilisateurs spécifiés puissent modifier uniquement ces zones du document. Par exemple, vous souhaiterez peut-être protéger un document entier à l’exception d’un signet particulier. Vous pouvez éventuellement ajouter un mot de passe pour que seuls les utilisateurs qui le connaissent puissent supprimer la protection du document.

> [!NOTE]
> L’exemple suivant n’utilise pas de protection par mot de passe. Toutefois, vous pouvez utiliser un mot de passe lors de l’ajout de la protection de document. Pour plus d’informations, consultez l’exemple de protection de document dans [exemples de développement Office et procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).

 Vous pouvez également utiliser des contrôles de contenu pour protéger certaines parties d’un document. Pour plus d’informations, consultez [Comment : protéger des parties de documents à l’aide de contrôles de contenu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Protéger un document qui fait partie d’une personnalisation au niveau du document

### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Pour protéger un document qui fait partie d’une personnalisation au niveau du document

1. Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> de la classe `ThisDocument` dans votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet111":::

### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Pour exclure un contrôle Bookmark de la protection de document

1. Protégez le document entier à l’aide de la méthode <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet111":::

2. Excluez `Bookmark1` de la protection de document.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet112":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet112":::

### <a name="compile-the-code"></a>Compiler le code
 Pour utiliser ces exemples de code, exécutez-les à partir de la classe `ThisDocument` de votre projet. Ces exemples de code partent du principe qu’il existe un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> nommé `Bookmark1` dans le document dans lequel ce code apparaît.

## <a name="protect-a-document-by-using-a-vsto-add-in"></a>Protéger un document à l’aide d’un complément VSTO

### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Pour protéger un document à l’aide d’un complément VSTO de niveau application

1. Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> du <xref:Microsoft.Office.Interop.Word.Document> que vous souhaitez protéger.

     L’exemple de code suivant protège le document actif. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet111":::

## <a name="see-also"></a>Voir aussi
- [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)
- [Protection par mot de passe sur les documents Office](../vsto/password-protection-on-office-documents.md)
- [Comment : autoriser le code à s’exécuter derrière des documents avec des autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
