---
title: "Comment : Parcourir par programmation des éléments trouvés dans des Documents | Documents Microsoft"
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
- loops, through found items in documents
- documents [Office development in Visual Studio], searching
- text [Office development in Visual Studio], searching in documents
ms.assetid: 68dc41b1-eb96-4697-ac93-1a88c862ebad
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7c45d25aeb548b45e032d09eb99cb289d0e2933
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Comment : parcourir les éléments trouvés dans les documents par programmation
  La classe <xref:Microsoft.Office.Interop.Word.Find> a une propriété <xref:Microsoft.Office.Interop.Word.Find.Found%2A> , qui retourne **true** chaque fois qu’un élément recherché est trouvé. Vous pouvez exécuter en boucle toutes les instances trouvées dans un <xref:Microsoft.Office.Interop.Word.Range> à l’aide de la méthode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> .  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-loop-through-found-items"></a>Pour exécuter en boucle les éléments trouvés  
  
1.  Déclarez un objet <xref:Microsoft.Office.Interop.Word.Range> .  
  
     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.  
  
     [!code-vb[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#79)]
     [!code-csharp[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#79)]  
  
     L’exemple de code suivant peut être utilisé dans un complément VSTO. Cet exemple utilise le document actif.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#79)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#79)]  
  
2.  Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Find.Found%2A> d’une boucle pour rechercher toutes les occurrences de la chaîne dans le document, puis incrémentez une variable entière de 1 chaque fois que la chaîne est trouvée.  
  
     [!code-vb[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#80)]
     [!code-csharp[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#80)]  
  
3.  Affichez le nombre de fois où que la chaîne a été trouvée dans une boîte de message.  
  
     [!code-vb[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#81)]
     [!code-csharp[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#81)]  
  
 Les exemples suivants montrent la méthode complète.  
  
## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document  
  
#### <a name="to-loop-through-items-in-a-document-level-customization"></a>Pour exécuter en boucle les éléments d’une personnalisation au niveau du document  
  
1.  L'exemple suivant montre le code complet pour une personnalisation au niveau du document. Pour utiliser ce code, exécutez-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#78)]  
  
## <a name="vsto-add-in-example"></a>Exemple de complément VSTO  
  
#### <a name="to-loop-through-items-in-an-vsto-add-in"></a>Pour exécuter en boucle les éléments d’un complément VSTO  
  
1.  L’exemple suivant présente le code complet pour un complément VSTO. Pour utiliser ce code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#78)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : rechercher par programmation et remplacer du texte dans des Documents](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Comment : définir les Options de recherche dans Word par programmation](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Comment : définir par programme et sélectionner des plages dans des Documents](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Comment : restaurer des sélections après des recherches de par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  