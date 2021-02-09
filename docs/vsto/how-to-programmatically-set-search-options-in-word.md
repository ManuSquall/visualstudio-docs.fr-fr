---
title: 'Comment : définir des options de recherche dans Word par programmation'
description: Découvrez comment vous pouvez utiliser Visual Studio pour définir par programmation des options de recherche pour des sélections dans Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e583b7deb9fbe37f40e582d2c8a946332dd00ffa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913467"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Comment : définir des options de recherche dans Word par programmation
  Il existe deux façons de définir des options de recherche pour des sélections dans des documents Word Microsoft Office :

- Définir les propriétés individuelles d’un <xref:Microsoft.Office.Interop.Word.Find> objet.

- Utilisez les arguments de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> méthode d’un <xref:Microsoft.Office.Interop.Word.Find> objet.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Utiliser les propriétés d’un objet Find
 Le code suivant définit les propriétés d’un <xref:Microsoft.Office.Interop.Word.Find> objet pour rechercher du texte dans la sélection actuelle. Notez que les critères de recherche, tels que Rechercher dans le sens, l’habillage et le texte à rechercher, sont des propriétés de l' <xref:Microsoft.Office.Interop.Word.Find> objet.

 La définition de chacune des propriétés de l' <xref:Microsoft.Office.Interop.Word.Find> objet n’est pas utile quand vous écrivez du code C#, car vous devez spécifier les mêmes propriétés que les paramètres de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> méthode. Par conséquent, cet exemple contient uniquement Visual Basic code.

### <a name="to-set-search-options-using-a-find-object"></a>Pour définir des options de recherche à l’aide d’un objet Find

1. Définissez les propriétés d’un <xref:Microsoft.Office.Interop.Word.Find> objet pour effectuer une recherche vers l’avant dans la sélection du texte **Rechercher**.

     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]

## <a name="use-execute-method-arguments"></a>Utiliser les arguments de la méthode Execute
 Le code suivant utilise la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> méthode d’un <xref:Microsoft.Office.Interop.Word.Find> objet pour rechercher du texte dans la sélection actuelle. Notez que les critères de recherche, tels que Rechercher dans le sens, le renvoi et le texte à rechercher, sont passés comme paramètres de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> méthode.

### <a name="to-set-search-options-using-execute-method-arguments"></a>Pour définir des options de recherche à l’aide d’arguments de méthode Execute

1. Transmettez les critères de recherche en tant que paramètres de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> méthode pour effectuer une recherche vers l’avant dans la sélection du texte **Rechercher**.

     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]

## <a name="see-also"></a>Voir aussi
- [Comment : Rechercher et remplacer du texte dans des documents par programmation](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Comment : parcourir les éléments trouvés dans les documents par programmation](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Comment : restaurer des sélections après des recherches par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)
