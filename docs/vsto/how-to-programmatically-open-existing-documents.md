---
title: 'Comment : ouvrir des documents existants par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd9e120283c392978a21fa9f796f9eed5e3dab31
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258721"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Comment : ouvrir des documents existants par programmation
  Le <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> méthode ouvre le document Microsoft Office Word existant spécifié par un chemin d’accès et un nom qualifié complet. Cette méthode retourne un <xref:Microsoft.Office.Interop.Word.Document> qui représente le document ouvert.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-open-a-document"></a>Pour ouvrir un document  
  
-   Appelez le <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> méthode de la <xref:Microsoft.Office.Interop.Word.Documents> collection et fournir un chemin d’accès au document.  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
## <a name="to-open-a-document-as-read-only"></a>Pour ouvrir un document en lecture seule  
  
-   Appeler le <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> (méthode), fournissez un chemin d’accès au document et définissez le *ReadOnly* l’argument de **True** dans l’appel de méthode.  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Un document nommé *NouveauDocument.doc* doit exister dans un répertoire nommé *Test* sur le lecteur C.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer par programme des documents](../vsto/how-to-programmatically-create-new-documents.md)   
 [Comment : fermer des documents par programmation](../vsto/how-to-programmatically-close-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  