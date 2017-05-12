---
title: "Comment&#160;: ajouter du texte et une mise en forme aux cellules des tableaux Word par programmation"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "cellules, ajouter texte et mise en forme"
  - "mettre en forme (développement Office dans Visual Studio)"
  - "tableaux (développement Office dans Visual Studio), ajouter texte et mise en forme"
  - "texte (développement Office dans Visual Studio), ajouter à des tableaux Word"
ms.assetid: 3df6492a-dc9c-43ac-8fc3-0f944edd88b2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Comment&#160;: ajouter du texte et une mise en forme aux cellules des tableaux Word par programmation
  Chaque tableau se compose d'un ensemble de cellules.  Chaque objet <xref:Microsoft.Office.Interop.Word.Cell> représente une cellule dans le tableau.  Vous faites référence à chaque cellule par son emplacement dans le tableau.  Cet exemple fait référence à la cellule située dans la première ligne et la première colonne du tableau. Il ajoute du texte à la cellule et lui applique un format.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Pour ajouter du texte et appliquer un format aux cellules  
  
1.  Faites référence à la cellule par son emplacement dans le tableau, ajoutez du texte à la cellule et appliquez\-lui un format.  
  
     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.  Pour utiliser cet exemple, exécutez\-le à partir de la classe `ThisDocument` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomation#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#97)]  
  
     L'exemple de code suivant peut être utilisé dans un complément VSTO.  Cet exemple utilise le document actif.  Pour utiliser l'exemple, exécutez\-le à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#97)]  
  
## Voir aussi  
 [Comment : créer des tableaux Word par programmation](../vsto/how-to-programmatically-create-word-tables.md)   
 [Comment : ajouter des lignes et des colonnes à des tableaux Word par programmation](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Comment : remplir des tableaux Word avec des propriétés de document par programmation](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  