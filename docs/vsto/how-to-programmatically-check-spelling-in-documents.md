---
title: 'Procédure : Vérifier l’orthographe dans les documents par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 19dc596851ba8ca8b2ea3ef50e7d151220354e3b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087761"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Procédure : Vérifier l’orthographe dans les documents par programmation
  Pour vérifier l’orthographe dans un document, utilisez le <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> (méthode). Cette méthode retourne une valeur booléenne qui indique si le paramètre fourni est correctement orthographié.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Pour vérifier l’orthographe et afficher les résultats dans une boîte de message  
  
1.  Appelez le <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> (méthode) et lui passer une plage de texte pour rechercher les erreurs d’orthographe. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
