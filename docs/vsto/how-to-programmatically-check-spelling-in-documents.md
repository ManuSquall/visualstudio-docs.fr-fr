---
title: 'Comment : vérifier l’orthographe dans les Documents par programmation | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a7445b48dc936bf57a5c93426e9ffcc7f114eb32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Comment : vérifier l'orthographe dans les documents par programmation
  Pour vérifier l’orthographe dans un document, utilisez la <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> (méthode). Cette méthode retourne une valeur booléenne qui indique si le paramètre fourni est correctement orthographié.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Pour vérifier l’orthographe et afficher les résultats dans une boîte de message  
  
1.  Appelez le <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> méthode et lui passer une plage de texte pour rechercher les erreurs d’orthographe. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : définir par programme et sélectionner des plages dans des Documents](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  