---
title: 'Procédure : Imprimer des documents Visio par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bf492c866a43a0098fbcad5660a19c57fc90a3a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071540"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Procédure : Imprimer des documents Visio par programmation
  Vous pouvez imprimer un document Microsoft Office Visio complet ou uniquement une page spécifique.

 Pour plus d’informations sur les méthodes d’impression, consultez la documentation de référence de VBA pour la méthode [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) et la méthode [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) .

## <a name="print-a-visio-document"></a>Imprimer un document Visio

### <a name="to-print-a-complete-document"></a>Pour imprimer un document complet

- Appelez la méthode `Microsoft.Office.Interop.Visio.Document.Print` de l’objet `Microsoft.Office.Interop.Visio.Document` à imprimer.

     L’exemple de code suivant imprime le document actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]

## <a name="print-a-page-of-a-visio-document"></a>Imprimer une page d’un document Visio

### <a name="to-print-a-page-of-a-document"></a>Pour imprimer une page d’un document

- Appelez la méthode `Microsoft.Office.Interop.Visio.Pages.Print` de l’objet `Microsoft.Office.Interop.Visio.Pages` à imprimer.

     L’exemple de code suivant imprime la première page du document actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Voir aussi
- [Solutions Visio](../vsto/visio-solutions.md)
- [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)
- [Guide pratique pour Créer par programme des documents Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Guide pratique pour Ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)
- [Guide pratique pour Fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)
- [Guide pratique pour Enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)
