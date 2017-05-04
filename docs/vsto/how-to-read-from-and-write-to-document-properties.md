---
title: "Comment&#160;: lire des propri&#233;t&#233;s de document et en &#233;crire | Microsoft Docs"
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
  - "Word (développement Office dans Visual Studio), propriétés de document"
  - "documents (développement Office dans Visual Studio), propriétés"
  - "propriétés de document (développement Office dans Visual Studio)"
  - "Excel (développement Office dans Visual Studio), propriétés de document"
ms.assetid: e9ef9fa3-36b9-48fb-8148-f5152463c03c
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Comment&#160;: lire des propri&#233;t&#233;s de document et en &#233;crire
  Vous pouvez stocker des propriétés de document avec un document. Les applications Office fournissent plusieurs propriétés intégrées, telles que l'auteur, le titre et l'objet. Cette rubrique indique comment définir des propriétés de document dans Microsoft Office Excel et Microsoft Office Word.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour visionner une vidéo de démonstration associée, consultez [Comment : accéder aux propriétés de document personnalisées et les manipuler dans Microsoft Word](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## Définition des propriétés de document dans Excel  
 Pour travailler avec des propriétés intégrées dans Excel, utilisez les propriétés suivantes :  
  
-   Dans un projet au niveau du document, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> de la classe `ThisWorkbook`.  
  
-   Dans un projet de complément VSTO, utilisez la propriété <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> d'un objet <xref:Microsoft.Office.Interop.Excel.Workbook>.  
  
 Ces propriétés retournent un objet <xref:Microsoft.Office.Core.DocumentProperties> qui est une collection d'objets <xref:Microsoft.Office.Core.DocumentProperty>. Vous pouvez utiliser la propriété `Item` de la collection pour récupérer une propriété particulière, par nom ou par index dans la collection.  
  
 L'exemple de code suivant indique comment modifier la propriété intégrée **Revision Number** dans un projet au niveau du document.  
  
#### Pour modifier la propriété Revision Number dans Excel  
  
1.  Assignez les propriétés de document intégrées à une variable.  
  
     [!code-csharp[Trin_VstcoreProgramming#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#7)]
     [!code-vb[Trin_VstcoreProgramming#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#7)]  
  
2.  Incrémentez la propriété `Revision Number` de un.  
  
     [!code-csharp[Trin_VstcoreProgramming#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#8)]
     [!code-vb[Trin_VstcoreProgramming#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#8)]  
  
## Définition des propriétés de document dans Word  
 Pour travailler avec des propriétés intégrées dans Word, utilisez les propriétés suivantes :  
  
-   Dans un projet au niveau du document, utilisez la propriété <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> de la classe `ThisDocument`.  
  
-   Dans un projet de complément VSTO, utilisez la propriété <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Document>.  
  
 Ces propriétés retournent un objet <xref:Microsoft.Office.Core.DocumentProperties> qui est une collection d'objets <xref:Microsoft.Office.Core.DocumentProperty>. Vous pouvez utiliser la propriété `Item` de la collection pour récupérer une propriété particulière, par nom ou par index dans la collection.  
  
 L'exemple de code suivant indique comment modifier la propriété intégrée **Subject** dans un projet au niveau du document.  
  
#### Pour modifier la propriété Subject  
  
1.  Assignez les propriétés de document intégrées à une variable.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#1)]  
  
2.  Remplacez la valeur de la propriété `Subject` par « Whitepaper ».  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#2)]  
  
## Programmation fiable  
 Les exemples supposent que vous avez écrit le code dans la classe `ThisWorkbook` dans un projet au niveau du document pour Excel et dans la classe `ThisDocument` dans un projet au niveau du document pour Word.  
  
 Bien que vous utilisiez Word et Excel ainsi que leurs objets, Microsoft Office fournit la liste des propriétés de document intégrées disponibles. Toute tentative d'accès à une propriété non définie lève une exception.  
  
## Voir aussi  
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Comment : créer et modifier des propriétés de document personnalisées](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  