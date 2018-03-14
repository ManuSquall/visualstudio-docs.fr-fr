---
title: "Comment : protéger des Documents et des parties de Documents par programmation | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 8655a03659bd3b69e23fd155620d42df6d52386c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Comment : protéger des documents et des parties de documents par programmation
  Vous pouvez ajouter une protection aux documents Microsoft Office Word pour empêcher les utilisateurs d’y apporter des modifications.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Vous pouvez également marquer certaines zones du document comme des exceptions, pour que les utilisateurs spécifiés puissent modifier uniquement ces zones du document. Par exemple, vous souhaiterez peut-être protéger un document entier à l’exception d’un signet particulier. Vous pouvez éventuellement ajouter un mot de passe pour que seuls les utilisateurs qui le connaissent puissent supprimer la protection du document.  
  
> [!NOTE]  
>  L’exemple suivant n’utilise pas de protection par mot de passe. Toutefois, vous pouvez utiliser un mot de passe lors de l’ajout de la protection de document. Pour plus d’informations, consultez l’exemple de protection de document à l’adresse [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
 Vous pouvez également utiliser des contrôles de contenu pour protéger certaines parties d’un document. Pour plus d'informations, consultez [Comment : protéger des parties de documents à l'aide de contrôles de contenu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="protecting-a-document-that-is-part-of-a-document-level-customization"></a>Protection d’un document qui fait partie d’une personnalisation au niveau du document  
  
#### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Pour protéger un document qui fait partie d’une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> de la classe `ThisDocument` dans votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
#### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Pour exclure un contrôle Bookmark de la protection de document  
  
1.  Protégez le document entier à l’aide de la méthode <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> .  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
2.  Excluez `Bookmark1` de la protection de document.  
  
     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]  
  
### <a name="compiling-the-code"></a>Compilation du code  
 Pour utiliser ces exemples de code, exécutez-les à partir de la classe `ThisDocument` de votre projet. Ces exemples de code partent du principe qu’il existe un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> nommé `Bookmark1` dans le document dans lequel ce code apparaît.  
  
## <a name="protecting-a-document-by-using-an-vsto-add-in"></a>Protection d’un document à l’aide d’un complément VSTO  
  
#### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Pour protéger un document à l’aide d’un complément VSTO de niveau application  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> du <xref:Microsoft.Office.Interop.Word.Document> que vous souhaitez protéger.  
  
     L’exemple de code suivant protège le document actif. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]  
  
## <a name="see-also"></a>Voir aussi  
 [Protection des documents dans les Solutions au niveau du Document](../vsto/document-protection-in-document-level-solutions.md)   
 [Mot de passe sur des Documents Office](../vsto/password-protection-on-office-documents.md)   
 [Comment : permettre au Code de s’exécuter derrière des Documents avec des autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  