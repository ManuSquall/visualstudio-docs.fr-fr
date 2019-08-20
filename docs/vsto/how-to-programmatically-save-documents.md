---
title: 'Procédure : Enregistrer des documents par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4fbf8e4cb67d5216dc17c325911bb243fae6e1c
ms.sourcegitcommit: 5b34052a1c7d86179d7898ed532babb2d9dad4a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490606"
---
# <a name="how-to-programmatically-save-documents"></a>Procédure : Enregistrer des documents par programmation

Il existe plusieurs façons d’enregistrer Microsoft Office documents Word. Vous pouvez enregistrer un document sans modifier le nom du document, ou vous pouvez enregistrer un document sous un nouveau nom.

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Enregistrer un document sans modifier son nom

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Pour enregistrer le document associé à une personnalisation au niveau du document

1. Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.Save%2A> de la classe <xref:Microsoft.Office.Tools.Word.Document> . Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]

### <a name="to-save-the-active-document"></a>Pour enregistrer le document actif

1. Appelez la <xref:Microsoft.Office.Interop.Word._Document.Save%2A> méthode pour le document actif. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.

    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]

   Si vous ne savez pas si le document que vous souhaitez enregistrer est le document actif, vous pouvez y faire référence par son nom.

### <a name="to-save-a-document-specified-by-name"></a>Pour enregistrer un document spécifié par son nom

1. Utilisez le nom du document comme argument de la <xref:Microsoft.Office.Interop.Word.Documents> collection. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]

## <a name="save-a-document-with-a-new-name"></a>Enregistrer un document sous un nouveau nom

Utilisez la `SaveAs` méthode pour enregistrer un document sous un nouveau nom. Vous pouvez utiliser cette méthode de l' <xref:Microsoft.Office.Tools.Word.Document> élément hôte dans un projet Word au niveau du document ou d’un objet <xref:Microsoft.Office.Interop.Word.Document> natif dans n’importe quel projet Word. Cette méthode requiert que vous spécifiiez le nouveau nom de fichier, mais les autres arguments sont facultatifs.

> [!NOTE]
> Si vous affichez la boîte de dialogue **Enregistrer** sous dans <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> le gestionnaire d' `ThisDocument` événements de et que vous définissez le paramètre *Cancel* sur **false**, l’application peut se fermer de manière inattendue. Si vous affectez la **valeur true**au paramètre *Cancel* , un message d’erreur s’affiche pour indiquer que l’enregistrement automatique a été désactivé.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Pour enregistrer le document associé à une personnalisation au niveau du document sous un nouveau nom

1. Appelez la `SaveAs` méthode de la `ThisDocument` classe dans votre projet, à l’aide d’un chemin d’accès qualifié complet et d’un nom de fichier. Si un fichier du même nom existe déjà dans ce dossier, il est automatiquement remplacé. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` .

    > [!NOTE]
    > La `SaveAs` méthode lève une exception si un répertoire cible n’existe pas ou s’il existe d’autres problèmes lors de l’enregistrement d’un fichier. Il est recommandé d’utiliser un`try...catch` bloc autour de la `SaveAs` méthode ou à l’intérieur d’une méthode d’appel.

     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]

### <a name="to-save-a-native-document-with-a-new-name"></a>Pour enregistrer un document natif sous un nouveau nom

1. Appelez la <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> méthode <xref:Microsoft.Office.Interop.Word.Document> du que vous souhaitez enregistrer, à l’aide d’un chemin d’accès qualifié complet et d’un nom de fichier. Si un fichier du même nom existe déjà dans ce dossier, il est automatiquement remplacé.

     L’exemple de code suivant enregistre le document actif sous un nouveau nom. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.

    > [!NOTE]
    > La <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> méthode lève une exception si un répertoire cible n’existe pas ou s’il existe d’autres problèmes lors de l’enregistrement d’un fichier. Il est recommandé d’utiliser un **bloc try... bloc catch** autour de <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> la méthode ou à l’intérieur d’une méthode d’appel.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]

## <a name="compile-the-code"></a>Compiler le code

Cet exemple de code doit respecter la condition suivante :

- Pour enregistrer un document par nom, un document nommé *NewDocument. doc* doit exister dans un répertoire nommé *test* sur le lecteur C.

- Pour enregistrer un document sous un nouveau nom, un répertoire nommé *test* doit exister sur le lecteur C.

## <a name="see-also"></a>Voir aussi

- [Guide pratique : Fermer des documents par programmation](../vsto/how-to-programmatically-close-documents.md)
- [Guide pratique : Ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)
- [Élément hôte de document](../vsto/document-host-item.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
