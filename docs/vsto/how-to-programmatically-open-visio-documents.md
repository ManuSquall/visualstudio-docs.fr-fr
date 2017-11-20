---
title: "Comment : ouvrir des Documents Visio par programmation | Documents Microsoft"
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
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4aa949d1ff2a8d9954c29314a85363d04d09b1a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-open-visio-documents"></a>Comment : ouvrir des documents Visio par programmation
  Il existe deux méthodes pour ouvrir des documents Microsoft Office Visio : ouvrir et OpenEx. La méthode OpenEx est identique à la méthode d’ouverture, à ceci près qu’il fournisse des arguments dans lequel l’appelant peut indiquer comment le document s’ouvre.  
  
 Pour plus d’informations sur le modèle objet, consultez la documentation de référence de VBA pour la méthode [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) et la méthode [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) .  
  
## <a name="opening-a-visio-document"></a>Ouverture d’un document Visio  
  
#### <a name="to-open-a-visio-document"></a>Pour ouvrir un document Visio  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Documents.Open et fournir le chemin d’accès qualifié complet du document Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="opening-a-visio-document-with-specified-arguments"></a>Ouverture d’un document Visio avec des arguments spécifiés  
  
#### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Pour ouvrir un document Visio en lecture seule et ancré  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Documents.OpenEx, fournissez le chemin d’accès qualifié complet du document Visio et incluez les arguments que vous souhaitez utiliser, dans ce cas, ancré et en lecture seule.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Un document Visio nommé `myDrawing.vsd` doit se trouver dans un répertoire nommé `Test` du dossier Mes documents (Windows XP ou version antérieure) ou du dossier Documents (Windows Vista).  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)   
 [Comment : créer par programme des Documents Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Comment : fermer des Documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Comment : enregistrer des Documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Guide pratique pour imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  