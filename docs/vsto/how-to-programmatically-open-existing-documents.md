---
title: "Comment : ouvrir des Documents existants par programmation | Documents Microsoft"
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
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 151571ace6790f05c067f8dff641988301bc1b0e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-open-existing-documents"></a>Comment : ouvrir des documents existants par programmation
  Le <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> méthode ouvre le document Microsoft Office Word existant spécifié par un chemin d’accès et un nom qualifié complet. Cette méthode retourne un <xref:Microsoft.Office.Interop.Word.Document> qui représente le document ouvert.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-open-a-document"></a>Pour ouvrir un document  
  
-   Appelez le <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> méthode de la <xref:Microsoft.Office.Interop.Word.Documents> collection et fournissez un chemin d’accès au document.  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
### <a name="to-open-a-document-as-read-only"></a>Pour ouvrir un document en lecture seule  
  
-   Appelez le <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> (méthode), indiquez un chemin d’accès au document et définissez la *ReadOnly* l’argument de **True** dans l’appel de méthode.  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Un document nommé NouveauDocument.doc doit exister dans un répertoire nommé Test sur le lecteur C.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer par programme des Documents](../vsto/how-to-programmatically-create-new-documents.md)   
 [Comment : fermer des Documents par programmation](../vsto/how-to-programmatically-close-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  