---
title: 'Procédure : Définir par programmation les options de recherche dans Word'
ms.date: 02/02/2017
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
ms.openlocfilehash: ec5b2f797371d19fea1b4fedc2064ab355ffac10
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853383"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Procédure : Définir par programmation les options de recherche dans Word
  Il existe deux façons de définir les options de recherche pour les sélections dans des documents Microsoft Office Word :  
  
- Définir les propriétés individuelles d’un <xref:Microsoft.Office.Interop.Word.Find> objet.  
  
- Utiliser des arguments de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> méthode d’un <xref:Microsoft.Office.Interop.Word.Find> objet.  
  
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
 [Guide pratique pour Rechercher et remplacer du texte dans les documents par programmation](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Guide pratique pour Parcourir par programmation des éléments trouvés dans les documents](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Guide pratique pour Restaurer des sélections après des recherches par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
