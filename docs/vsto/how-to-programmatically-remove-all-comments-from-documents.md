---
title: "Comment : supprimer par programmation de tous les commentaires des Documents | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f22dd675cd6e247f2f6fd6c17f69ea6370230aa0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Comment : supprimer tous les commentaires des documents par programmation
  Utilisez la méthode SupprimerTousCommentaires pour supprimer tous les commentaires d’un document Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Pour supprimer tous les commentaires d’un document qui fait partie d’une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> de la classe `ThisDocument` dans votre projet. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` .  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
### <a name="to-remove-all-comments-from-a-document-by-using-an-vsto-add-in"></a>Pour supprimer tous les commentaires d’un document à l’aide d’un complément VSTO  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> du <xref:Microsoft.Office.Interop.Word.Document> à partir duquel vous souhaitez supprimer les commentaires.  
  
     L’exemple de code suivant supprime tous les commentaires du document actif. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : ajouter par programmation des commentaires à du texte dans des Documents](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Élément hôte de document](../vsto/document-host-item.md)  
  
  