---
title: 'Procédure : Utiliser les boîtes de dialogue Word en mode masqué par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e32c97069e3400b447f8756f9638c9d88d38d99a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255847"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Procédure : Utiliser les boîtes de dialogue Word en mode masqué par programmation
  Vous pouvez effectuer des opérations complexes avec un appel de méthode en appelant les boîtes de dialogue intégrées dans Microsoft Office mot sans les afficher à l’utilisateur. Pour ce faire, vous pouvez utiliser <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> la méthode de <xref:Microsoft.Office.Interop.Word.Dialog> l’objet sans appeler <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> la méthode.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Exemples
 Les exemples de code suivants montrent comment utiliser la boîte de dialogue **mise en page** en mode masqué pour définir plusieurs propriétés de mise en page sans entrée utilisateur. Les exemples utilisent un <xref:Microsoft.Office.Interop.Word.Dialog> objet pour configurer une taille de page personnalisée. Les paramètres spécifiques pour la mise en page, tels que la marge supérieure, la marge inférieure, etc., sont disponibles en tant que propriétés à <xref:Microsoft.Office.Interop.Word.Dialog> liaison tardive de l’objet. Ces propriétés sont créées dynamiquement par Word au moment de l’exécution.

 L’exemple suivant montre comment effectuer cette tâche dans Visual Basic projets où **option strict** est désactivé et dans les C# [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]projets visuels qui ciblent. Dans ces projets, vous pouvez utiliser les fonctionnalités de liaison tardive dans le Visual Basic C# et les compilateurs visuels. Pour utiliser cet exemple, exécutez-le à `ThisDocument` partir `ThisAddIn` de la classe ou de votre projet.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 L’exemple suivant montre comment effectuer cette tâche dans Visual Basic projets où **option strict** a la valeur on. Dans ces projets, vous devez utiliser la réflexion pour accéder aux propriétés à liaison tardive. Pour utiliser cet exemple, exécutez-le à `ThisDocument` partir `ThisAddIn` de la classe ou de votre projet.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Utiliser les boîtes de dialogue intégrées dans Word par programmation](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md)
- [Liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md)
- [Réflexion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Réflexion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
