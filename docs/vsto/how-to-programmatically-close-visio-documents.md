---
title: "Comment : fermer des Documents Visio par programmation | Documents Microsoft"
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
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
ms.assetid: 59c0e215-a4c1-4b39-a491-37534f172705
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f59d4178e82cde6c476d9cab8d20a37dcb698262
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-close-visio-documents"></a>Comment : fermer des documents Visio par programmation
  Vous pouvez fermer le document Microsoft Office Visio actif à l’aide de la méthode Microsoft.Office.Interop.Visio.Document.Close.  
  
 Pour plus d’informations sur cette méthode, consultez la documentation de référence VBA de la méthode [Microsoft.Office.Interop.Visio.Document.Close](http://msdn.microsoft.com/library/office/ff767415.aspx) .  
  
## <a name="closing-the-active-document"></a>Fermeture du document actif  
  
#### <a name="to-close-the-active-document"></a>Pour fermer le document actif  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Document.Close pour fermer le document actif.  
  
     Pour utiliser l’exemple de code suivant, exécutez-le dans la classe `ThisAddIn` dans un projet de complément VSTO pour Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)   
 [Comment : créer par programme des Documents Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Comment : ouvrir des Documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Comment : enregistrer des Documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Guide pratique pour imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  