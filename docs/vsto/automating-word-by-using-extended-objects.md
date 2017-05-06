---
title: "Automatisation de Word &#224; l&#39;aide d&#39;objets &#233;tendus"
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
  - "Word (développement Office dans Visual Studio), automatisation"
  - "objets étendus (développement Office dans Visual Studio), Word"
  - "automation (développement Office dans Visual Studio), Word"
  - "éléments hôtes (développement Office dans Visual Studio), Word"
  - "automatiser Word"
  - "contrôles (développement Office dans Visual Studio), contrôles hôtes Word"
  - "contrôles hôtes, Word"
  - "contrôles hôtes (développement Office dans Visual Studio), Word"
  - "Word (développement Office dans Visual Studio), contrôles hôtes"
ms.assetid: 3911c7cd-7092-468d-bd82-2fdec53a2d9b
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Automatisation de Word &#224; l&#39;aide d&#39;objets &#233;tendus
  Quand vous développez des solutions Word dans Visual Studio, vous pouvez également utiliser des *éléments hôtes* et des *contrôles hôtes* dans vos solutions. Il s’agit d’objets qui étendent certains objets couramment utilisés dans le modèle objet Word \(autrement dit, le modèle objet exposé par l’assembly PIA \(Primary Interop Assembly\) pour Word\), par exemple les objets <xref:Microsoft.Office.Interop.Word.Document> et <xref:Microsoft.Office.Interop.Word.ContentControl>. Les objets étendus se comportent comme les objets Word sur lesquels ils sont basés, mais ils ajoutent des événements supplémentaires et des fonctionnalités de liaison de données aux objets.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Les éléments hôtes et les contrôles hôtes sont disponibles dans les compléments VSTO et les personnalisations au niveau du document. Toutefois, le contexte dans lequel ils peuvent être utilisés est différent pour chaque type de solution. Pour plus d'informations, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
## Élément hôte de document  
 Les projets Word vous donnent accès à l’élément hôte <xref:Microsoft.Office.Tools.Word.Document>. L’élément hôte <xref:Microsoft.Office.Tools.Word.Document> sert de conteneur pour d’autres contrôles, notamment les contrôles hôtes et les contrôles Windows Forms. En outre, il gère les informations relatives aux contrôles sur sa surface. L’élément hôte <xref:Microsoft.Office.Tools.Word.Document> fournit aussi la plupart des mêmes membres que la classe <xref:Microsoft.Office.Interop.Word.Document>, qui est la classe correspondante dans le modèle objet de Word.  
  
 Pour plus d'informations, consultez [Élément hôte de document](../vsto/document-host-item.md).  
  
## Contrôles hôtes Word  
 Il existe plusieurs contrôles hôtes pour Word qui vous aident à créer, organiser et automatiser des documents. La plupart de leurs fonctionnalités concernent l’importation, la présentation et la protection des données. Ces contrôles hôtes fournissent des événements et des fonctionnalités de liaison de données dont ne disposent pas leurs équivalents dans le modèle objet Word natif.  
  
 Dans les projets au niveau du document, vous pouvez ajouter n’importe quel contrôle hôte à votre document au moment du design, ou vous pouvez ajouter des contrôles de contenu et de signet au moment de l’exécution. Dans les projets de complément VSTO, vous pouvez ajouter des contrôles de contenu et de signet à tout document ouvert au moment de l’exécution.  
  
 Pour plus d’informations sur les contrôles hôtes que vous pouvez utiliser dans les projets Word, consultez les rubriques suivantes :  
  
-   [Contrôles de contenu](../vsto/content-controls.md)  
  
-   [Bookmark, contrôle](../vsto/bookmark-control.md)  
  
-   [XMLNode, contrôle](../vsto/xmlnode-control.md)  
  
-   [XMLNodes, contrôle](../vsto/xmlnodes-control.md)  
  
## Voir aussi  
 [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Comment : ajouter des contrôles XMLNode à des documents Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Comment : ajouter des contrôles XMLNodes à des documents Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Comment : redimensionner les contrôles Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Procédure pas à pas : création d'un modèle à l'aide de contrôles de contenu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Procédure pas à pas : liaison de contrôles de contenu à des parties XML personnalisées](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [Procédure pas à pas : création de menus contextuels pour les signets](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Solutions Word](../vsto/word-solutions.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  