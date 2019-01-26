---
title: 'Procédure : Ouvrir des documents Visio par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8c9e9eb6a298270deb4f66c38662b0c52d7ee76f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864447"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Procédure : Ouvrir des documents Visio par programmation
  Il existe deux méthodes pour ouvrir des documents Microsoft Office Visio : Ouvrez et OpenEx. La méthode OpenEx est identique à la méthode Open, à ceci près qu’il fournisse des arguments dans lesquels l’appelant peut indiquer comment le document s’ouvre.  
  
 Pour plus d’informations sur le modèle objet, consultez la documentation de référence de VBA pour la méthode [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) et la méthode [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) .  
  
## <a name="open-a-visio-document"></a>Ouvrir un document Visio  
  
### <a name="to-open-a-visio-document"></a>Pour ouvrir un document Visio  
  
-   Appelez la méthode `Microsoft.Office.Interop.Visio.Documents.Open` et fournissez le chemin complet du document Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="open-a-visio-document-with-specified-arguments"></a>Ouvrir un document Visio avec des arguments spécifiés  
  
### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Pour ouvrir un document Visio en lecture seule et ancré  
  
-   Appelez la méthode `Microsoft.Office.Interop.Visio.Documents.OpenEx`, fournissez le chemin complet du document Visio et incluez les arguments à utiliser. Dans le cas présent, Docked et RO (read-only, en lecture seule).  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Un document Visio nommé `myDrawing.vsd` doit se trouver dans un répertoire nommé `Test` dans le *Mes Documents* dossier (pour Windows XP et versions antérieures) ou le *Documents* dossier (Windows Vista).  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)   
 [Guide pratique pour Créer par programme des documents Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Guide pratique pour Fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Guide pratique pour Enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Guide pratique pour Imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
