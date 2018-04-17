---
title: 'Comment : utiliser par programme des boîtes de dialogue Word en Mode masqué | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7b9d9b49783e3070e91291460e3f4aa7a4667620
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Comment : utiliser des boîtes de dialogue Word en mode masqué par programmation
  Vous pouvez effectuer des opérations complexes avec un appel de méthode en appelant les boîtes de dialogue intégrées dans Microsoft Office Word sans les afficher à l’utilisateur. Procéder à l’aide de la <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> méthode de la <xref:Microsoft.Office.Interop.Word.Dialog> objet sans appeler le <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> (méthode).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>Exemples  
 Les exemples de code suivants montrent comment utiliser le **mise en Page** boîte de dialogue en mode masqué pour définir plusieurs propriétés de mise en page sans entrée d’utilisateur. Les exemples utilisent un <xref:Microsoft.Office.Interop.Word.Dialog> pour configurer une taille de page personnalisée. Les paramètres spécifiques de la mise en page, tels que la marge supérieure, marge inférieure et ainsi de suite, sont disponibles en tant que propriétés à liaison tardive de la <xref:Microsoft.Office.Interop.Word.Dialog> objet. Ces propriétés sont créées dynamiquement par Word au moment de l’exécution.  
  
 L’exemple suivant montre comment effectuer cette tâche dans les projets Visual Basic où **Option Strict** est désactivé et dans les projets Visual c# qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Dans ces projets, vous pouvez utiliser les fonctions de liaison tardive dans les compilateurs Visual Basic et Visual c#. Pour utiliser cet exemple, exécutez-le à partir de la `ThisDocument` ou `ThisAddIn` classe dans votre projet.  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 L’exemple suivant montre comment effectuer cette tâche dans les projets Visual Basic où **Option Strict** sur. Dans ces projets, vous devez utiliser la réflexion pour accéder aux propriétés à liaison tardive. Pour utiliser cet exemple, exécutez-le à partir de la `ThisDocument` ou `ThisAddIn` classe dans votre projet.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : utiliser par programme des boîtes de dialogue intégrées dans Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Vue d’ensemble du modèle d’objet Word](../vsto/word-object-model-overview.md)   
 [Liaison tardive dans les Solutions Office](../vsto/late-binding-in-office-solutions.md)   
 [Réflexion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Réflexion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  