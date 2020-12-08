---
title: 'Comment : ajouter des commentaires à du texte dans des documents par programmation'
description: Ajoutez par programmation des commentaires à du texte dans des documents. La propriété Comments de la classe document ajoute un commentaire à une plage de texte dans un document Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a39c02cfb7b170fd923e8e7409a0f4215d67583
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844593"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Comment : ajouter des commentaires à du texte dans des documents par programmation
  La propriété Comments de la classe document ajoute un commentaire à une plage de texte dans un document Word Microsoft Office.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 L’exemple suivant ajoute un commentaire au premier paragraphe du document.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Pour ajouter un nouveau commentaire à du texte dans une personnalisation au niveau du document

1. Appelez la méthode <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> de la propriété <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> et spécifiez une plage et le texte du commentaire. Pour utiliser l'exemple de code suivant, exécutez-le à partir de la classe `ThisDocument` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>Pour ajouter un nouveau commentaire à du texte dans un complément VSTO

1. Appelez la méthode <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> de la propriété <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> et spécifiez une plage et le texte du commentaire.

     L’exemple de code suivant ajoute un commentaire au document actif. Pour utiliser cet exemple, exécutez-le à partir de la classe `ThisAddIn` dans votre projet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]

## <a name="robust-programming"></a>Programmation fiable
 Pour modifier les initiales de l’utilisateur que Word ajoute aux commentaires, utilisez la propriété <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> .

## <a name="see-also"></a>Voir aussi
- [Comment : supprimer tous les commentaires des documents par programmation](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [Élément hôte de document](../vsto/document-host-item.md)
