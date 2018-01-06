---
title: "Comment : ajouter par programmation des en-têtes et pieds de page aux Documents | Documents Microsoft"
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
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
ms.assetid: c7a5cc8a-d8c0-48e9-81d3-108aa6bfbb74
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b0f2651fc4bfedab3c7308c7fa7e8cef604666f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Comment : ajouter des en-têtes et des pieds de page aux documents par programmation
  Vous pouvez ajouter du texte aux en-têtes et pieds de page dans votre document à l'aide de la propriété <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> et de la propriété <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> de <xref:Microsoft.Office.Interop.Word.Section>. Chaque section d'un document contient trois en-têtes et pieds de page :  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 Les procédures sont différentes pour les personnalisations au niveau du document et les compléments VSTO.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customizations"></a>personnalisations au niveau du document  
 Pour utiliser les exemples de code suivants, exécutez-les à partir de la classe `ThisDocument` de votre projet.  
  
#### <a name="to-add-text-to-footers-in-the-document"></a>Pour ajouter du texte dans les pieds de page du document  
  
1.  L'exemple de code suivant définit la police du texte à insérer dans le pied de page principal de chaque section du document, puis insère le texte dans le pied de page.  
  
     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>Pour ajouter du texte dans les en-têtes du document  
  
1.  L'exemple de code suivant ajoute un champ pour afficher le numéro de page dans chaque en-tête du document, puis définit l'alignement du paragraphe afin d'aligner le texte à droite de l'en-tête.  
  
     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]  
  
## <a name="vsto-add-ins"></a>VSTO Add-ins  
 Pour utiliser les exemples de code suivants, exécutez-les à partir de la classe `ThisAddIn` de votre projet.  
  
#### <a name="to-add-text-to-footers-in-a-document"></a>Pour ajouter du texte dans les pieds de page d'un document  
  
1.  L'exemple de code suivant définit la police du texte à insérer dans le pied de page principal de chaque section du document, puis insère le texte dans le pied de page. Cet exemple de code utilise le document actif.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>Pour ajouter du texte dans les en-têtes du document  
  
1.  L'exemple de code suivant ajoute un champ pour afficher le numéro de page dans chaque en-tête du document, puis définit l'alignement du paragraphe afin d'aligner le texte à droite de l'en-tête. Cet exemple de code utilise le document actif.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer par programme des Documents](../vsto/how-to-programmatically-create-new-documents.md)   
 [Comment : étendre des plages dans des Documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Guide pratique pour parcourir les éléments trouvés dans les documents par programmation](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
   