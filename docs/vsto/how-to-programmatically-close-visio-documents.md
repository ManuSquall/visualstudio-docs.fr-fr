---
title: 'Comment : fermer des Documents Visio par programmation | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 314d8e5bfd40e1e45d4795a6e4523db19124741a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
  