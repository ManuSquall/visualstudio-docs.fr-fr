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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9059e0f066cbd1dc6ced5f11f1139d7687afacf3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597205"
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
- [Solutions Visio](../vsto/visio-solutions.md)
- [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)
- [Guide pratique pour Créer par programme des documents Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Guide pratique pour Ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)
- [Guide pratique pour Enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)
- [Guide pratique pour Imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)
