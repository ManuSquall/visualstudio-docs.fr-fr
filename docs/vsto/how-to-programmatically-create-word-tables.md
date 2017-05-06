---
title: "Comment&#160;: cr&#233;er des tableaux Word par programmation"
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
  - "documents (développement Office dans Visual Studio), ajouter des tableaux"
  - "tableaux (développement Office dans Visual Studio), ajouter à des documents"
ms.assetid: fe1f9143-9622-45e8-b0a5-511336d99ad1
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Comment&#160;: cr&#233;er des tableaux Word par programmation
  La collection <xref:Microsoft.Office.Interop.Word.Tables> est membre des classes <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document><xref:Microsoft.Office.Interop.Word.Selection> et <xref:Microsoft.Office.Interop.Word.Range>, ce qui signifie que vous pouvez créer un tableau dans l'un de ces contextes.  La méthode <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> de la collection <xref:Microsoft.Office.Interop.Word.Tables> permet d'ajouter un tableau au niveau de la plage spécifiée.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Création de tableaux dans des personnalisations au niveau du document  
  
#### Pour ajouter un tableau simple à un document  
  
-   Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> pour ajouter un tableau comprenant trois lignes et quatre colonnes au début du document.  
  
     Pour utiliser l'exemple de code suivant, exécutez\-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomation#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#86)]  
  
 Lorsque vous créez un tableau, il est automatiquement ajouté à la collection <xref:Microsoft.Office.Interop.Word.Tables> de l'élément hôte <xref:Microsoft.Office.Tools.Word.Document>.  Vous pouvez alors faire référence au tableau par son numéro d'élément à l'aide de la propriété <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, comme illustré dans le code suivant.  
  
#### Pour faire référence à un tableau à l'aide de son numéro d'élément  
  
1.  Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> et fournissez le numéro d'élément du tableau auquel vous souhaitez faire référence.  
  
     Pour utiliser l'exemple de code suivant, exécutez\-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomation#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#87)]  
  
 Chaque objet <xref:Microsoft.Office.Interop.Word.Table> possède également une propriété <xref:Microsoft.Office.Interop.Word.Table.Range%2A> qui vous permet de définir des attributs de mise en forme.  
  
#### Pour appliquer un style à un tableau  
  
1.  Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Table.Style%2A> pour appliquer au tableau l'un des styles intégrés de Word.  
  
     Pour utiliser l'exemple de code suivant, exécutez\-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomation#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#88)]  
  
## Création de tableaux dans des compléments VSTO  
  
#### Pour ajouter un tableau simple à un document  
  
-   Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> pour ajouter un tableau comprenant trois lignes et quatre colonnes au début du document.  
  
     L'exemple de code suivant ajoute un tableau au document actif.  Pour utiliser cet exemple, exécutez\-le à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#86)]  
  
 Lorsque vous créez un tableau, il est automatiquement ajouté à la collection <xref:Microsoft.Office.Interop.Word.Tables> de l'élément <xref:Microsoft.Office.Interop.Word.Document>.  Vous pouvez alors faire référence au tableau par son numéro d'élément à l'aide de la propriété <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, comme illustré dans le code suivant.  
  
#### Pour faire référence à un tableau à l'aide de son numéro d'élément  
  
1.  Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> et fournissez le numéro d'élément du tableau auquel vous souhaitez faire référence.  
  
     L'exemple de code suivant utilise le document actif.  Pour utiliser cet exemple, exécutez\-le à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#87)]  
  
 Chaque objet <xref:Microsoft.Office.Interop.Word.Table> possède également une propriété <xref:Microsoft.Office.Interop.Word.Table.Range%2A> qui vous permet de définir des attributs de mise en forme.  
  
#### Pour appliquer un style à un tableau  
  
1.  Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Table.Style%2A> pour appliquer au tableau l'un des styles intégrés de Word.  
  
     L'exemple de code suivant utilise le document actif.  Pour utiliser cet exemple, exécutez\-le à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#88)]  
  
## Voir aussi  
 [Comment : ajouter du texte et une mise en forme aux cellules des tableaux Word par programmation](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Comment : ajouter des lignes et des colonnes à des tableaux Word par programmation](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Comment : remplir des tableaux Word avec des propriétés de document par programmation](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  