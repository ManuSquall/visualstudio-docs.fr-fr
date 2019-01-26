---
title: 'Procédure : Restaurer des sélections après des recherches par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 684c373204c5cfadd3cfcd705993aaa7a40bce5f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875210"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Procédure : Restaurer des sélections après des recherches par programmation
  Si vous recherchez et remplacez du texte dans un document, vous souhaiterez restaurer la sélection d’utilisateur d’origine une fois que la recherche est terminée.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Le code dans l’exemple de procédure utilise deux <xref:Microsoft.Office.Interop.Word.Range> objets. Un stocke actuel <xref:Microsoft.Office.Interop.Word.Selection>, l’autre définit l’ensemble du document à utiliser comme un intervalle de recherche.  
  
## <a name="to-restore-the-users-original-selection-after-a-search"></a>Pour restaurer la sélection d’origine de l’utilisateur après une recherche  
  
1. Créer le <xref:Microsoft.Office.Interop.Word.Range> objets pour le document et la sélection actuelle.  
  
    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2. Effectuer la recherche et l’opération de remplacement.  
  
    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3. Sélectionnez la plage de début pour restaurer la sélection d’origine de l’utilisateur.  
  
    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
   L'exemple suivant montre la méthode complète.  
  
## <a name="example"></a>Exemple  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Rechercher et remplacer du texte dans les documents par programmation](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Guide pratique pour Définir par programmation les options de recherche dans Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Guide pratique pour Parcourir par programmation des éléments trouvés dans les documents](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
