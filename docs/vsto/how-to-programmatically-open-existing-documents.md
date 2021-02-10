---
title: 'Comment : ouvrir des documents existants par programmation'
description: Découvrez comment utiliser la méthode Open pour ouvrir un document Microsoft Word existant spécifié par un chemin d’accès complet et un nom de fichier.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 81d134c88d93b3da3b0f0e6c3ded3cbe0d6d3f89
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951678"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Comment : ouvrir des documents existants par programmation
  La <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> méthode ouvre le document Microsoft Office Word existant spécifié par un chemin d’accès complet et un nom de fichier. Cette méthode retourne un <xref:Microsoft.Office.Interop.Word.Document> qui représente le document ouvert.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Pour ouvrir un document

- Appelez la <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> méthode de la <xref:Microsoft.Office.Interop.Word.Documents> collection et fournissez un chemin d’accès au document.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>Pour ouvrir un document en lecture seule

- Appelez la <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> méthode, fournissez un chemin d’accès au document et affectez à l’argument *ReadOnly* la **valeur true** dans l’appel de méthode.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple de code doit respecter la condition suivante :

- Un document nommé *NewDocument.doc* doit exister dans un répertoire nommé *test* sur le lecteur C.

## <a name="see-also"></a>Voir aussi
- [Comment : créer des documents par programmation](../vsto/how-to-programmatically-create-new-documents.md)
- [Comment : fermer des documents par programmation](../vsto/how-to-programmatically-close-documents.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
