---
title: 'Comment : imprimer des documents Visio par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4caf48d0268e653b7ce6f7a5c8e7efb1e2ec39e6
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257503"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Comment : imprimer des documents Visio par programmation
  Vous pouvez imprimer un document Microsoft Office Visio complet ou uniquement une page spécifique.  
  
 Pour plus d’informations sur les méthodes d’impression, consultez la documentation de référence de VBA pour la méthode [Microsoft.Office.Interop.Visio.Document.Print](https://msdn.microsoft.com/library/office/ff767996.aspx) et la méthode [Microsoft.Office.Interop.Visio.Page.Print](https://msdn.microsoft.com/library/office/ff765064.aspx) .  
  
## <a name="print-a-visio-document"></a>Imprimer un document Visio  
  
### <a name="to-print-a-complete-document"></a>Pour imprimer un document complet  
  
-   Appelez le `Microsoft.Office.Interop.Visio.Document.Print` méthode de la `Microsoft.Office.Interop.Visio.Document` objet que vous souhaitez imprimer.  
  
     L’exemple de code suivant imprime le document actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="print-a-page-of-a-visio-document"></a>Imprimer une page d’un document Visio  
  
### <a name="to-print-a-page-of-a-document"></a>Pour imprimer une page d’un document  
  
-   Appelez le `Microsoft.Office.Interop.Visio.Pages.Print` méthode de la `Microsoft.Office.Interop.Visio.Pages` objet que vous souhaitez imprimer.  
  
     L’exemple de code suivant imprime la première page du document actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)   
 [Comment : créer par programme des documents Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Comment : ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Comment : fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Comment : enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  