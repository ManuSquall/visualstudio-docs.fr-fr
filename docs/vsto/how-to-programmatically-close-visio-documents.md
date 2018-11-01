---
title: 'Comment : fermer des documents Visio par programmation'
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
ms.openlocfilehash: d800fbe0a6dda6fc7c5160d607d393afcb920cd9
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671571"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Comment : fermer des documents Visio par programmation
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
 [Comment : créer par programme des documents Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Comment : ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Comment : enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Comment : imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  