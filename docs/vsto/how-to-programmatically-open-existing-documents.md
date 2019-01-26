---
title: 'Procédure : Ouvrir des documents existants par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 670c4855806dcc5d781da8479963f6705ba99fd3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869146"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Procédure : Ouvrir des documents existants par programmation
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
 [Guide pratique pour Créer par programme des documents](../vsto/how-to-programmatically-create-new-documents.md)   
 [Guide pratique pour Fermer des documents par programmation](../vsto/how-to-programmatically-close-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
