---
title: "Comment&#160;: ajouter des parties XML personnalis&#233;es &#224; des documents &#224; l&#39;aide de compl&#233;ments VSTO"
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
  - "compléments (développement Office dans Visual Studio), parties XML personnalisées"
  - "documents Office (développement Office dans Visual Studio), parties XML personnalisées"
  - "Word (développement Office dans Visual Studio), parties XML personnalisées"
  - "PowerPoint (développement Office dans Visual Studio), parties XML personnalisées"
  - "Excel (développement Office dans Visual Studio), parties XML personnalisées"
  - "parties XML personnalisées (développement Office dans Visual Studio), ajout"
  - "documents (développement Office dans Visual Studio), parties XML personnalisées"
  - "compléments de niveau application (développement Office dans Visual Studio), parties XML personnalisées"
ms.assetid: 872d2beb-193b-49f9-9a7b-dcebab91a73b
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Comment&#160;: ajouter des parties XML personnalis&#233;es &#224; des documents &#224; l&#39;aide de compl&#233;ments VSTO
  Vous pouvez stocker des données XML dans les types suivants de documents en créant une partie XML personnalisée dans un complément VSTO :  
  
-   un classeur Microsoft Office Excel,  
  
-   un document Microsoft Office Word,  
  
-   une présentation Microsoft Office PowerPoint.  
  
 Pour plus d'informations, consultez [Vue d'ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md).  
  
 **S'applique à :** les informations de cette rubrique s'appliquent aux projets de niveau application pour Excel, PowerPoint et Word. Pour plus d'informations, consultez [Fonctionnalités disponibles par type d'application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
### Pour ajouter une partie XML personnalisée à un classeur Excel  
  
1.  Ajoutez un nouvel objet <xref:Microsoft.Office.Core.CustomXMLPart> à la collection <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> figurant dans le classeur.<xref:Microsoft.Office.Core.CustomXMLPart> contient la chaîne XML que vous souhaitez stocker dans le classeur.  
  
     L'exemple de code suivant ajoute une partie XML personnalisée à un classeur spécifié.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Ajoutez la méthode `AddCustomXmlPartToWorkbook` à la classe `ThisAddIn` dans un projet de complément VSTO pour Excel.  
  
3.  Appelez cette méthode à partir d'un autre code dans votre projet. Par exemple, pour créer la partie XML personnalisée quand l'utilisateur ouvre un classeur, appelez la méthode à partir d'un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen>.  
  
### Pour ajouter une partie XML personnalisée à un document Word  
  
1.  Ajoutez un nouvel objet <xref:Microsoft.Office.Core.CustomXMLPart> à la collection <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> figurant dans le document.<xref:Microsoft.Office.Core.CustomXMLPart> contient la chaîne XML que vous souhaitez stocker dans le document.  
  
     L'exemple de code suivant ajoute une partie XML personnalisée à un document spécifié.  
  
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Ajoutez la méthode `AddCustomXmlPartToDocument` à la classe `ThisAddIn` dans un projet de complément VSTO pour Word.  
  
3.  Appelez cette méthode à partir d'un autre code dans votre projet. Par exemple, pour créer la partie XML personnalisée quand l'utilisateur ouvre un document, appelez la méthode à partir d'un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
### Pour ajouter une partie XML personnalisée à une présentation PowerPoint  
  
1.  Ajoutez un nouvel objet <xref:Microsoft.Office.Core.CustomXMLPart> à la collection <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A> figurant dans la présentation.<xref:Microsoft.Office.Core.CustomXMLPart> contient la chaîne XML que vous souhaitez stocker dans la présentation.  
  
     L'exemple de code suivant ajoute une partie XML personnalisée à une présentation spécifiée.  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartPowerPointAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartPowerPointAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Ajoutez la méthode `AddCustomXmlPartToPresentation` à la classe `ThisAddIn` dans un projet de complément VSTO pour PowerPoint.  
  
3.  Appelez cette méthode à partir d'un autre code dans votre projet. Par exemple, pour créer la partie XML personnalisée quand l'utilisateur ouvre une présentation, appelez la méthode à partir d'un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen>.  
  
## Programmation fiable  
 Par souci de simplicité, cet exemple utilise une chaîne XML définie comme variable locale dans la méthode. En règle générale, vous devez obtenir le code XML auprès d'une source externe, telle qu'un fichier ou une base de données.  
  
## Voir aussi  
 [Vue d'ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md)   
 [Comment : ajouter des parties XML personnalisées aux personnalisations au niveau du document](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  