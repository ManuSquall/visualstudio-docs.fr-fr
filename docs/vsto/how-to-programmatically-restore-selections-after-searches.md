---
title: "Comment : restaurer par programme des sélections après des recherches | Documents Microsoft"
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
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
ms.assetid: 1e6131ad-0e5b-4189-be67-5b2ed87d193d
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 84e0a9c18d3af7956c90390e5447011d67369216
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Comment : restaurer des sélections après des recherches par programmation
  Si vous recherchez et remplacez du texte dans un document, vous souhaiterez restaurer la sélection d’origine de l’utilisateur une fois que la recherche est terminée.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Le code dans l’exemple de procédure utilise les deux <xref:Microsoft.Office.Interop.Word.Range> objets. Un magasins actuel <xref:Microsoft.Office.Interop.Word.Selection>, l’autre définit l’ensemble du document à utiliser comme plage de recherche.  
  
### <a name="to-restore-the-users-original-selection-after-a-search"></a>Pour restaurer la sélection d’origine de l’utilisateur après une recherche  
  
1.  Créer le <xref:Microsoft.Office.Interop.Word.Range> objets pour le document et la sélection actuelle.  
  
     [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
     [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2.  Effectuer la recherche et l’opération de remplacement.  
  
     [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
     [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3.  Sélectionnez la plage de début pour restaurer la sélection d’origine de l’utilisateur.  
  
     [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
     [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
 L'exemple suivant montre la méthode complète.  
  
## <a name="example"></a>Exemple  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : rechercher par programmation et remplacer du texte dans des Documents](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Comment : définir les Options de recherche dans Word par programmation](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Comment : Parcourir par programmation des éléments trouvés dans des Documents](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  