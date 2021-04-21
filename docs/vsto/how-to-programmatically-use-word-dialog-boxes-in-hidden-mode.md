---
title: 'Comment : utiliser des boîtes de dialogue Word en mode masqué par programmation'
description: Découvrez comment vous pouvez utiliser Visual Studio pour utiliser les boîtes de dialogue Microsoft Word en mode masqué par programmation.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 39a81ccec284541d93d3a5901211d8a46ea6b61a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826185"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Comment : utiliser des boîtes de dialogue Word en mode masqué par programmation
  Vous pouvez effectuer des opérations complexes avec un appel de méthode en appelant les boîtes de dialogue intégrées dans Microsoft Office mot sans les afficher à l’utilisateur. Pour ce faire, vous pouvez utiliser la <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> méthode de l' <xref:Microsoft.Office.Interop.Word.Dialog> objet sans appeler la <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> méthode.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Exemples
 Les exemples de code suivants montrent comment utiliser la boîte de dialogue **mise en page** en mode masqué pour définir plusieurs propriétés de mise en page sans entrée utilisateur. Les exemples utilisent un <xref:Microsoft.Office.Interop.Word.Dialog> objet pour configurer une taille de page personnalisée. Les paramètres spécifiques pour la mise en page, tels que la marge supérieure, la marge inférieure, etc., sont disponibles en tant que propriétés à liaison tardive de l' <xref:Microsoft.Office.Interop.Word.Dialog> objet. Ces propriétés sont créées dynamiquement par Word au moment de l’exécution.

 L’exemple suivant montre comment effectuer cette tâche dans Visual Basic projets où **option strict** est désactivé et dans les projets Visual C# qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Dans ces projets, vous pouvez utiliser les fonctionnalités de liaison tardive dans les compilateurs Visual Basic et Visual C#. Pour utiliser cet exemple, exécutez-le à partir de la `ThisDocument` `ThisAddIn` classe ou de votre projet.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet123":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet123":::

 L’exemple suivant montre comment effectuer cette tâche dans Visual Basic projets où **option strict** a la valeur on. Dans ces projets, vous devez utiliser la réflexion pour accéder aux propriétés à liaison tardive. Pour utiliser cet exemple, exécutez-le à partir de la `ThisDocument` `ThisAddIn` classe ou de votre projet.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet104":::

## <a name="see-also"></a>Voir aussi
- [Comment : utiliser des boîtes de dialogue intégrées dans Word par programmation](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md)
- [Liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md)
- [Réflexion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Réflexion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
