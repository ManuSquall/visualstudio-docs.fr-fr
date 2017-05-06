---
title: "Comment&#160;: cr&#233;er et modifier des propri&#233;t&#233;s de document personnalis&#233;es"
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
  - "propriétés de documents personnalisés"
  - "documents (développement Office dans Visual Studio), propriétés"
  - "propriétés de document (développement Office dans Visual Studio)"
ms.assetid: 99d9dfaf-891f-4f3b-a580-67362afdaf34
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Comment&#160;: cr&#233;er et modifier des propri&#233;t&#233;s de document personnalis&#233;es
  Les applications Microsoft Office répertoriées ci\-dessus fournissent des propriétés intégrées qui sont stockées avec les documents. En outre, vous pouvez créer et modifier des propriétés de document personnalisées si vous souhaitez stocker des informations supplémentaires avec le document.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Utilisez la propriété CustomDocumentProperties d'un document pour utiliser des propriétés personnalisées. Par exemple, dans un projet au niveau du document pour Microsoft Office Excel, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> de la classe `ThisWorkbook`. Dans un projet de complément VSTO pour Excel, utilisez la propriété <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> d'un objet <xref:Microsoft.Office.Interop.Excel.Workbook>. Ces propriétés retournent un objet <xref:Microsoft.Office.Core.DocumentProperties>, qui est une collection d'objets <xref:Microsoft.Office.Core.DocumentProperty>. Vous pouvez utiliser la propriété `Item` de la collection pour récupérer une propriété particulière, par nom ou par index dans la collection.  
  
 L'exemple suivant illustre l'ajout d'une propriété personnalisée dans une personnalisation au niveau du document pour Excel et l'affectation d'une valeur à cette propriété.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour visionner la vidéo de démonstration associée, consultez [omment : accéder aux propriétés de document personnalisées et les manipuler dans Microsoft Word](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## Exemple  
 [!code-csharp[Trin_VstcoreProgramming#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#6)]
 [!code-vb[Trin_VstcoreProgramming#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#6)]  
  
## Programmation fiable  
 Toute tentative d'accès à la propriété `Value` pour des propriétés non définies lève une exception.  
  
## Voir aussi  
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Comment : lire des propriétés de document et en écrire](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  