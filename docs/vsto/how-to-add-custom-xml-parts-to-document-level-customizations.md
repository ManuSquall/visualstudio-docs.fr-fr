---
title: "Comment&#160;: ajouter des parties XML personnalis&#233;es aux personnalisations au niveau du document"
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
  - "personnalisations au niveau du document (développement Office dans Visual Studio), parties XML personnalisées"
  - "documents Office (développement Office dans Visual Studio), parties XML personnalisées"
  - "Word (développement Office dans Visual Studio), parties XML personnalisées"
  - "Excel (développement Office dans Visual Studio), parties XML personnalisées"
  - "parties XML personnalisées (développement Office dans Visual Studio), ajouter"
  - "documents (développement Office dans Visual Studio), parties XML personnalisées"
ms.assetid: e305a3d6-3a0e-4e72-ab8c-6a87a3590068
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Comment&#160;: ajouter des parties XML personnalis&#233;es aux personnalisations au niveau du document
  Vous pouvez stocker des données XML dans un classeur Microsoft Office Excel ou un document Microsoft Office Word en créant une partie XML personnalisée dans une personnalisation au niveau du document. Pour plus d'informations, consultez [Vue d'ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Visual Studio ne fournit pas de projets au niveau du document pour Microsoft Office PowerPoint. Pour plus d’informations sur l’ajout d’une partie XML personnalisée à une présentation PowerPoint à l’aide d’un complément VSTO, consultez [Comment : ajouter des parties XML personnalisées à des documents à l'aide de compléments VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
### Pour ajouter une partie XML personnalisée à un classeur Excel  
  
1.  Ajoutez un nouvel objet <xref:Microsoft.Office.Core.CustomXMLPart> à la collection <xref:Microsoft.Office.Core.CustomXMLParts> figurant dans le classeur.<xref:Microsoft.Office.Core.CustomXMLPart> contient la chaîne XML que vous souhaitez stocker dans le classeur.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelDocLevel/CS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelDocLevel/VB/ThisWorkbook.vb#1)]  
  
2.  Ajoutez la méthode `AddCustomXmlPartToWorkbook` à la classe `ThisWorkbook` dans un projet au niveau du document pour Excel.  
  
3.  Appelez cette méthode à partir d'un autre code dans votre projet. Par exemple, pour créer la partie XML personnalisée quand l’utilisateur ouvre le classeur, appelez la méthode à partir du gestionnaire d’événements `ThisWorkbook_Startup`.  
  
### Pour ajouter une partie XML personnalisée à un document Word  
  
1.  Ajoutez un nouvel objet <xref:Microsoft.Office.Core.CustomXMLPart> à la collection <xref:Microsoft.Office.Core.CustomXMLParts> figurant dans le document.<xref:Microsoft.Office.Core.CustomXMLPart> contient la chaîne XML que vous souhaitez stocker dans le document.  
  
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordDocLevel/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordDocLevel/VB/ThisDocument.vb#1)]  
  
2.  Ajoutez la méthode `AddCustomXmlPartToDocument` à la classe `ThisDocument` dans un projet au niveau du document pour Word.  
  
3.  Appelez cette méthode à partir d'un autre code dans votre projet. Par exemple, pour créer la partie XML personnalisée quand l’utilisateur ouvre le document, appelez la méthode à partir du gestionnaire d’événements `ThisDocument_Startup`.  
  
## Programmation fiable  
 Par souci de simplicité, cet exemple utilise une chaîne XML définie comme variable locale dans la méthode. En règle générale, vous devez obtenir le code XML auprès d'une source externe, telle qu'un fichier ou une base de données.  
  
## Voir aussi  
 [Vue d'ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md)   
 [Comment : ajouter des parties XML personnalisées à des documents à l'aide de compléments VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
  