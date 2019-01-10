---
title: 'Procédure : Fermer des documents Visio par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 499cc399c1e23c6f045426e57f8e9a027b5c6537
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091791"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Procédure : Fermer des documents Visio par programmation
  Vous pouvez fermer le document Microsoft Office Visio actif à l’aide de la méthode `Microsoft.Office.Interop.Visio.Document.Close`.  
  
 Pour plus d’informations sur cette méthode, consultez la documentation de référence VBA de la méthode [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) .  
  
## <a name="close-the-active-document"></a>Fermer le document actif  
  
### <a name="to-close-the-active-document"></a>Pour fermer le document actif  
  
-   Appelez la méthode `Microsoft.Office.Interop.Visio.Document.Close` pour fermer le document actif.  
  
     Pour utiliser l’exemple de code suivant, exécutez-le la `ThisAddIn` classe dans un projet de complément VSTO pour Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)   
 [Guide pratique pour Créer par programme des documents Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Guide pratique pour Ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Guide pratique pour Enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Guide pratique pour Imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
