---
title: 'Procédure : Ajouter par programmation des en-têtes et pieds de page aux documents'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: d6baf57f8b34f6dc591a8e1a131bd665671322e9
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803374"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Procédure : Ajouter par programmation des en-têtes et pieds de page aux documents
  Vous pouvez ajouter du texte aux en-têtes et pieds de page dans votre document à l'aide de la propriété <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> et de la propriété <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> de <xref:Microsoft.Office.Interop.Word.Section>. Chaque section d'un document contient trois en-têtes et pieds de page :  
  
- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
  Les procédures sont différentes pour les personnalisations au niveau du document et les compléments VSTO.  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customizations"></a>Personnalisations au niveau du document  
 Pour utiliser les exemples de code suivants, exécutez-les à partir de la classe `ThisDocument` de votre projet.  
  
### <a name="to-add-text-to-footers-in-the-document"></a>Pour ajouter du texte dans les pieds de page du document  
  
1.  L'exemple de code suivant définit la police du texte à insérer dans le pied de page principal de chaque section du document, puis insère le texte dans le pied de page.  
  
     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]  
  
### <a name="to-add-text-to-headers-in-the-document"></a>Pour ajouter du texte dans les en-têtes du document  
  
1.  L'exemple de code suivant ajoute un champ pour afficher le numéro de page dans chaque en-tête du document, puis définit l'alignement du paragraphe afin d'aligner le texte à droite de l'en-tête.  
  
     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]  
  
## <a name="vsto-add-ins"></a>Compléments VSTO  
 Pour utiliser les exemples de code suivants, exécutez-les à partir de la classe `ThisAddIn` de votre projet.  
  
### <a name="to-add-text-to-footers-in-a-document"></a>Pour ajouter du texte dans les pieds de page d'un document  
  
1.  L'exemple de code suivant définit la police du texte à insérer dans le pied de page principal de chaque section du document, puis insère le texte dans le pied de page. Cet exemple de code utilise le document actif.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]  
  
### <a name="to-add-text-to-headers-in-the-document"></a>Pour ajouter du texte dans les en-têtes du document  
  
1.  L'exemple de code suivant ajoute un champ pour afficher le numéro de page dans chaque en-tête du document, puis définit l'alignement du paragraphe afin d'aligner le texte à droite de l'en-tête. Cet exemple de code utilise le document actif.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Créer par programme des documents](../vsto/how-to-programmatically-create-new-documents.md)   
 [Guide pratique pour Étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Guide pratique pour Parcourir par programmation des éléments trouvés dans les documents](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
   