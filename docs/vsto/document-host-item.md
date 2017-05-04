---
title: "&#201;l&#233;ment h&#244;te de document | Microsoft Docs"
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
  - "documents (développement Office dans Visual Studio)"
  - "documents Office (développement Office dans Visual Studio), éléments hôtes de document"
  - "éléments hôtes de document"
  - "Word (développement Office dans Visual Studio), documents Word"
  - "Word (développement Office dans Visual Studio)"
  - "documents Word"
  - "éléments hôtes (développement Office dans Visual Studio), Document"
ms.assetid: 4c1963f2-e88e-4c68-9f3d-13dedebddde4
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# &#201;l&#233;ment h&#244;te de document
  L’élément hôte <xref:Microsoft.Office.Tools.Word.Document> est un type qui étend le type <xref:Microsoft.Office.Interop.Word.Document> à partir de l’assembly PIA \(Primary Interop Assembly\) de Word. L’élément hôte <xref:Microsoft.Office.Tools.Word.Document> fournit les mêmes propriétés, méthodes et événements qu’un objet <xref:Microsoft.Office.Interop.Word.Document>, mais il expose également des événements supplémentaires et agit comme conteneur pour les contrôles hôtes et les contrôles Windows Forms.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Dans les projets au niveau du document se trouve un élément hôte <xref:Microsoft.Office.Tools.Word.Document> par défaut qui représente le document dans votre projet. Dans les projets de compléments VSTO, vous pouvez générer des éléments hôtes <xref:Microsoft.Office.Tools.Word.Document> au moment de l'exécution.  
  
## Présentation de l’élément hôte de document dans les projets au niveau du document  
 Pour accéder au document dans votre projet, utilisez la classe `ThisDocument`. Lorsque vous créez un projet au niveau du document, Visual Studio génère la classe `ThisDocument` pour servir de liaison entre Word et votre code de personnalisation. La classe `ThisDocument` vous permet d’accéder aux membres de l’élément hôte <xref:Microsoft.Office.Tools.Word.Document> pour effectuer des tâches de base dans votre personnalisation, comme l’exécution de code à l’ouverture ou la fermeture du document. Vous pouvez aussi utiliser la classe pour ajouter des contrôles au document. En combinant plusieurs jeux de contrôles et en écrivant du code, vous pouvez lier les contrôles à des données, recueillir des informations auprès de l’utilisateur et répondre aux actions de l’utilisateur. Pour plus d'informations, consultez [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md).  
  
 La classe `ThisDocument` fournit un emplacement dans lequel vous pouvez commencer à écrire du code dans votre projet. Étant donné que la classe fournit les mêmes propriétés, méthodes et événements que l’objet <xref:Microsoft.Office.Interop.Word.Document> dans l’assembly PIA pour Word, vous pouvez aussi utiliser `ThisDocument` pour accéder au modèle objet de Word. Pour plus d'informations, consultez [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md).  
  
### Limitations de l’élément hôte Document dans les projets au niveau du document  
 Un projet au niveau du document peut contenir un seul élément hôte <xref:Microsoft.Office.Tools.Word.Document> \(autrement dit, la classe `ThisDocument`\). Vous ne pouvez pas ajouter de nouveaux éléments hôtes <xref:Microsoft.Office.Tools.Word.Document> à votre projet au moment du design. Vous ne pouvez pas non plus créer des éléments hôtes <xref:Microsoft.Office.Tools.Word.Document> au moment de l’exécution à partir d’une personnalisation au niveau du document.  
  
 Si vous créez un document Word au moment de l’exécution, il sera de type <xref:Microsoft.Office.Interop.Word.Document>. Comme il ne s’agit pas d’un élément hôte, il ne peut pas contenir de contrôles hôtes ni de contrôles Windows Forms. Pour plus d’informations sur la création de documents au moment de l’exécution, consultez [Comment : créer des documents par programmation](../vsto/how-to-programmatically-create-new-documents.md).  
  
## Présentation des éléments hôtes Document dans les projets de niveau application  
 Dans les projets complément VSTO, vous pouvez générer un élément hôte <xref:Microsoft.Office.Tools.Word.Document> au moment de l’exécution pour tout document ouvert dans Word. Vous pouvez utiliser l’élément hôte <xref:Microsoft.Office.Tools.Word.Document> pour ajouter des contrôles au document associé ou pour gérer des événements qui ne sont pas disponibles sur des objets <xref:Microsoft.Office.Interop.Word.Document>.  
  
 Pour générer un élément hôte <xref:Microsoft.Office.Tools.Word.Document>, utilisez la méthode GetVstoObject. Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Voir aussi  
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  