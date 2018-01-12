---
title: "Comment : définir les Options de recherche dans Word par programmation | Documents Microsoft"
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
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fa575f8c89e9aea125179c896c35b8ecc775965e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Comment : définir les options de recherche dans Word par programmation
  Il existe deux façons de définir les options de recherche pour les sélections dans les documents Microsoft Office Word :  
  
-   Définir des propriétés individuelles d’un <xref:Microsoft.Office.Interop.Word.Find> objet.  
  
-   Utilisez les arguments de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> méthode d’un <xref:Microsoft.Office.Interop.Word.Find> objet.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-properties-of-a-find-object"></a>À l’aide des propriétés d’un objet de recherche  
 Le code suivant définit les propriétés d’un <xref:Microsoft.Office.Interop.Word.Find> objet pour rechercher du texte dans la sélection actuelle. Notez que les critères de recherche, telles que la recherche avant, d’habillage et le texte à rechercher, sont des propriétés de la <xref:Microsoft.Office.Interop.Word.Find> objet.  
  
 Définition de chacune des propriétés de la <xref:Microsoft.Office.Interop.Word.Find> objet n’est pas utile lorsque vous écrivez du code c#, car vous devez spécifier les mêmes propriétés en tant que paramètres dans le <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> (méthode). Par conséquent, cet exemple contient uniquement du code Visual Basic.  
  
#### <a name="to-set-search-options-using-a-find-object"></a>Pour définir les options de recherche à l’aide d’un objet de recherche  
  
1.  Définir les propriétés d’un <xref:Microsoft.Office.Interop.Word.Find> objet à rechercher vers le bas dans une sélection pour le texte **me trouver**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="using-execute-method-arguments"></a>À l’aide des Arguments de la méthode Execute  
 Le code suivant utilise la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> méthode d’un <xref:Microsoft.Office.Interop.Word.Find> objet pour rechercher du texte dans la sélection actuelle. Notez que les critères de recherche, telles que la recherche avant, d’habillage et le texte à rechercher, sont passés comme paramètres de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> (méthode).  
  
#### <a name="to-set-search-options-using-execute-method-arguments"></a>Pour définir les options de recherche à l’aide des arguments de la méthode Execute  
  
1.  Passez les critères de recherche en tant que paramètres de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> méthode pour rechercher vers le bas dans une sélection pour le texte **me trouver**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : rechercher par programmation et remplacer du texte dans des Documents](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Comment : Parcourir par programmation des éléments trouvés dans des Documents](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Guide pratique pour restaurer des sélections après des recherches par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  