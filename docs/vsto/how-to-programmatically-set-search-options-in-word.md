---
title: 'Comment : définir par programmation les options de recherche dans Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: b02adab3b0ba032a39ce73c08bd287213ef2ffc4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672685"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Comment : définir par programmation les options de recherche dans Word
  Il existe deux façons de définir les options de recherche pour les sélections dans des documents Microsoft Office Word :  
  
-   Définir les propriétés individuelles d’un <xref:Microsoft.Office.Interop.Word.Find> objet.  
  
-   Utiliser des arguments de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> méthode d’un <xref:Microsoft.Office.Interop.Word.Find> objet.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="use-properties-of-a-find-object"></a>Utilisez les propriétés d’un objet de recherche  
 Le code suivant définit les propriétés d’un <xref:Microsoft.Office.Interop.Word.Find> objet pour rechercher du texte dans la sélection actuelle. Notez que les critères de recherche, telles que la recherche directe, habillage et le texte à rechercher, sont des propriétés de la <xref:Microsoft.Office.Interop.Word.Find> objet.  
  
 Définition de chacune des propriétés de la <xref:Microsoft.Office.Interop.Word.Find> objet n’est pas utile lorsque vous écrivez du code c#, car vous devez spécifier les mêmes propriétés en tant que paramètres dans le <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> (méthode). Par conséquent, cet exemple contient uniquement du code Visual Basic.  
  
### <a name="to-set-search-options-using-a-find-object"></a>Pour définir les options de recherche à l’aide d’un objet Find  
  
1.  Définir les propriétés d’un <xref:Microsoft.Office.Interop.Word.Find> objet à rechercher vers le bas dans une sélection pour le texte **me trouver**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="use-execute-method-arguments"></a>Utiliser des arguments de méthode Execute  
 Le code suivant utilise la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> méthode d’un <xref:Microsoft.Office.Interop.Word.Find> objet pour rechercher du texte dans la sélection actuelle. Notez que les critères de recherche, telles que la recherche directe, habillage et le texte à rechercher, sont passés comme paramètres de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> (méthode).  
  
### <a name="to-set-search-options-using-execute-method-arguments"></a>Pour définir les options de recherche à l’aide des arguments de la méthode Execute  
  
1.  Passer des critères de recherche en tant que paramètres de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> méthode pour rechercher vers le bas dans une sélection pour le texte **me trouver**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : rechercher et remplacer du texte dans les documents par programmation](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Comment : Parcourir par programmation des éléments trouvés dans les documents](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Comment : restaurer des sélections après des recherches par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  