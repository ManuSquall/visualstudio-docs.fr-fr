---
title: 'Comment : imprimer des documents Visio par programmation'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 0e31a55e49d42311b5ec5fff82769584cc55ce09
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537798"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Comment : imprimer des documents Visio par programmation
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
- [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)
- [Comment : créer des documents Visio par programmation](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Comment : ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)
- [Comment : fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)
- [Comment : enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)
