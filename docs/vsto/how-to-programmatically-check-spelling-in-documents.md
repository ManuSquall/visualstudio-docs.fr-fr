---
title: 'Comment : vérifier l’orthographe dans les documents par programmation'
description: En savoir plus sur la vérification de l’orthographe dans un document par programmation, vous pouvez utiliser la méthode CheckSpelling.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 85294b21e9fd1f52f5cc707fc6824a87530e3cda
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848311"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Comment : vérifier l’orthographe dans les documents par programmation
  Pour vérifier l’orthographe d’un document, utilisez la <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> méthode. Cette méthode retourne une valeur booléenne qui indique si le paramètre fourni est correctement orthographié.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Pour vérifier l’orthographe et afficher les résultats dans une boîte de message

1. Appelez la <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> méthode et transmettez-lui une plage de texte pour rechercher les fautes d’orthographe. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>Voir aussi
- [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
