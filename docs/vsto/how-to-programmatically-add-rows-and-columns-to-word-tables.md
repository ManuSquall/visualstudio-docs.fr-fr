---
title: "Comment&#160;: ajouter des lignes et des colonnes &#224; des tableaux Word par programmation"
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
  - "colonnes (développement Office dans Visual Studio), ajouter à des tableaux Word"
  - "lignes (développement Office dans Visual Studio), ajouter à des tableaux Word"
  - "tableaux (développement Office dans Visual Studio), ajouter des lignes et des colonnes"
ms.assetid: 01a9b6ca-1373-4a6e-b9e6-2225a1321daf
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Comment&#160;: ajouter des lignes et des colonnes &#224; des tableaux Word par programmation
  Dans un tableau Microsoft Office Word, les cellules sont organisées en lignes et en colonnes.  Vous pouvez utiliser la méthode <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Rows> pour ajouter des lignes au tableau et la méthode <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Columns> pour ajouter des colonnes.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Exemples de personnalisation au niveau du document  
 Les exemples de code suivants peuvent être utilisés dans une personnalisation au niveau du document.  Pour utiliser ces exemples, exécutez\-les à partir de la classe `ThisDocument` de votre projet.  Ces exemples supposent que le document associé à votre personnalisation possède déjà au moins un tableau.  
  
> [!IMPORTANT]  
>  Ce code s'exécute uniquement dans les projets que vous créez à l'aide des modèles de projet suivants :  
>   
>  -   Document Word 2013  
> -   Modèle Word 2013  
> -   Document Word 2010  
> -   Modèle Word 2010  
>   
>  Si vous souhaitez effectuer cette tâche dans un autre type de projet, vous devez ajouter une référence à l'assembly **Microsoft.Office.Interop.Word**, puis vous devez utiliser les classes de cet assembly pour ajouter des lignes et des colonnes aux tableaux.  Pour plus d'informations, consultez [Comment : cibler les applications Office via les assemblys PIA &#40;Primary Interop Assembly&#41;](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) et [Référence de l'assembly PIA Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### Pour ajouter une ligne à un tableau  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> pour ajouter une ligne à un tableau.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomation#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#95)]  
  
#### Pour ajouter une colonne à un tableau  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>, puis utilisez la méthode <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> pour que toutes les colonnes aient la même largeur.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomation#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#96)]  
  
## Exemples de complément VSTO  
 Les exemples de code suivants peuvent être utilisés dans un complément VSTO.  Pour utiliser les exemples, exécutez\-les à partir de la classe `ThisAddIn` de votre projet.  Ces exemples supposent que le document actif possède déjà au moins un tableau.  
  
> [!IMPORTANT]  
>  Ce code s'exécute uniquement dans les projets que vous créez à l'aide des modèles de complément VSTO Word :  
>   
>  Si vous souhaitez effectuer cette tâche dans un autre type de projet, vous devez ajouter une référence à l'assembly **Microsoft.Office.Interop.Word**, puis vous devez utiliser les classes de cet assembly pour ajouter des lignes et des colonnes aux tableaux.  Pour plus d'informations, consultez [Comment : cibler les applications Office via les assemblys PIA &#40;Primary Interop Assembly&#41;](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) et [Référence de l'assembly PIA Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### Pour ajouter une ligne à un tableau  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> pour ajouter une ligne à un tableau.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#95)]  
  
#### Pour ajouter une colonne à un tableau  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>, puis utilisez la méthode <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> pour que toutes les colonnes aient la même largeur.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#96)]  
  
## Voir aussi  
 [Comment : créer des tableaux Word par programmation](../vsto/how-to-programmatically-create-word-tables.md)   
 [Comment : ajouter du texte et une mise en forme aux cellules des tableaux Word par programmation](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Comment : remplir des tableaux Word avec des propriétés de document par programmation](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  