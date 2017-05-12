---
title: "Comment&#160;: remplir des tableaux Word avec des propri&#233;t&#233;s de document par programmation"
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
  - "propriétés du document, insérer dans des tableaux Word"
  - "documents (développement Office dans Visual Studio), propriétés du document"
ms.assetid: 7ed65a3d-58ed-43b3-92d6-dc10a2c331db
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Comment&#160;: remplir des tableaux Word avec des propri&#233;t&#233;s de document par programmation
  L'exemple suivant crée un tableau Microsoft Office Word en haut du document et le remplit avec les propriétés du document hôte.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Remplissage des tableaux dans une personnalisation au niveau du document  
  
#### Pour créer un tableau et le remplir avec des propriétés de document  
  
1.  Définissez la plage en haut du document.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#90](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#90)]
     [!code-vb[Trin_VstcoreWordAutomation#90](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#90)]  
  
2.  Insérez un titre pour le tableau et insérez des marques de paragraphe.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#91](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#91)]
     [!code-vb[Trin_VstcoreWordAutomation#91](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#91)]  
  
3.  Ajoutez le tableau au document au niveau de la plage.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#92](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#92)]
     [!code-vb[Trin_VstcoreWordAutomation#92](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#92)]  
  
4.  Mettez en forme le tableau et appliquez un style.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#93](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#93)]
     [!code-vb[Trin_VstcoreWordAutomation#93](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#93)]  
  
5.  Insérez les propriétés de document dans les cellules.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#94](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#94)]
     [!code-vb[Trin_VstcoreWordAutomation#94](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#94)]  
  
 L'exemple suivant montre la procédure complète.  Pour utiliser ce code, exécutez\-le à partir de la classe `ThisDocument` dans votre projet.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#89](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#89)]
 [!code-vb[Trin_VstcoreWordAutomation#89](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#89)]  
  
## Remplissage des tableaux dans un complément VSTO  
  
#### Pour créer un tableau et le remplir avec des propriétés de document  
  
1.  Définissez la plage en haut du document.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#90](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#90)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#90](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#90)]  
  
2.  Insérez un titre pour le tableau et insérez des marques de paragraphe.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#91](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#91)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#91](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#91)]  
  
3.  Ajoutez le tableau au document au niveau de la plage.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#92](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#92)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#92](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#92)]  
  
4.  Mettez en forme le tableau et appliquez un style.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#93](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#93)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#93](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#93)]  
  
5.  Insérez les propriétés de document dans les cellules.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#94](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#94)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#94](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#94)]  
  
 L'exemple suivant montre la procédure complète.  Pour utiliser ce code, exécutez\-le à partir de la classe `ThisAddIn` dans votre projet.  
  
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#89](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#89)]
 [!code-vb[Trin_VstcoreWordAutomationAddIn#89](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#89)]  
  
## Voir aussi  
 [Comment : créer des tableaux Word par programmation](../vsto/how-to-programmatically-create-word-tables.md)   
 [Comment : ajouter du texte et une mise en forme aux cellules des tableaux Word par programmation](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Comment : ajouter des lignes et des colonnes à des tableaux Word par programmation](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  