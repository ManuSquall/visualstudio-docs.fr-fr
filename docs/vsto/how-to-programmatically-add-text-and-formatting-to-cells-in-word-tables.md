---
title: "Comment : ajouter texte et mise en forme aux cellules des tableaux Word par programmation | Documents Microsoft"
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
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
ms.assetid: 3df6492a-dc9c-43ac-8fc3-0f944edd88b2
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2d75ef5ba59e9d2eead443fb69e1ab679f1d17f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Comment : ajouter du texte et une mise en forme aux cellules des tableaux Word par programmation
  Chaque tableau se compose d’une collection de cellules. Chaque objet <xref:Microsoft.Office.Interop.Word.Cell> représente une cellule dans le tableau. Vous faites référence à chaque cellule par son emplacement dans le tableau. Cet exemple fait référence à la cellule située dans la première ligne et la première colonne du tableau. Il ajoute du texte à la cellule et lui applique un format.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-add-text-and-formatting-to-cells"></a>Pour ajouter du texte et appliquer un format aux cellules  
  
1.  Faites référence à la cellule par son emplacement dans le tableau, ajoutez du texte à la cellule et appliquez-lui un format.  
  
     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document. Pour utiliser cet exemple, exécutez-le à partir de la classe `ThisDocument` dans votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]  
  
     L'exemple de code suivant peut être utilisé dans un complément VSTO. Cet exemple utilise le document actif. Pour utiliser l'exemple, exécutez-le à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer des tableaux Word par programmation](../vsto/how-to-programmatically-create-word-tables.md)   
 [Comment : ajouter par programmation des lignes et des colonnes à des tableaux Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Guide pratique pour remplir des tableaux Word avec des propriétés de document par programmation](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  