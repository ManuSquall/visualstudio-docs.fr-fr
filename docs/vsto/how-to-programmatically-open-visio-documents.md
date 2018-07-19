---
title: 'Comment : ouvrir des documents Visio par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a3a7d2a9855abef0415661798c8a213eb748e22f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257850"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Comment : ouvrir des documents Visio par programmation
  Il existe deux méthodes pour ouvrir des documents Microsoft Office Visio : ouvrir et OpenEx. La méthode OpenEx est identique à la méthode Open, à ceci près qu’il fournisse des arguments dans lesquels l’appelant peut indiquer comment le document s’ouvre.  
  
 Pour plus d’informations sur le modèle objet, consultez la documentation de référence de VBA pour la méthode [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) et la méthode [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) .  
  
## <a name="open-a-visio-document"></a>Ouvrir un document Visio  
  
### <a name="to-open-a-visio-document"></a>Pour ouvrir un document Visio  
  
-   Appelez le `Microsoft.Office.Interop.Visio.Documents.Open` méthode et fournir le chemin d’accès qualifié complet du document Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="open-a-visio-document-with-specified-arguments"></a>Ouvrir un document Visio avec des arguments spécifiés  
  
### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Pour ouvrir un document Visio en lecture seule et ancré  
  
-   Appelez le `Microsoft.Office.Interop.Visio.Documents.OpenEx` (méthode), indiquez le chemin qualifié complet du document Visio et incluez les arguments que vous souhaitez utiliser, dans ce cas, ancré et en lecture seule.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Un document Visio nommé `myDrawing.vsd` doit se trouver dans un répertoire nommé `Test` dans le *Mes Documents* dossier (pour Windows XP et versions antérieures) ou le *Documents* dossier (Windows Vista).  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)   
 [Comment : créer par programme des documents Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Comment : fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Comment : enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Comment : imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  