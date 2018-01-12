---
title: "Comment : vérifier l’orthographe dans les Documents par programmation | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 357e92235f474392c3bdbe1ac1f19af8c9c1538a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
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
  
  