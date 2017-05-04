---
title: "Comment&#160;: associer une page Web &#224; un dossier Outlook par programmation | Microsoft Docs"
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
  - "dossiers (développement Office dans Visual Studio), pages Web et"
  - "Outlook (développement Office dans Visual Studio), pages Web attachées à des dossiers"
  - "pages Web (développement Office dans Visual Studio), dossiers Outlook"
ms.assetid: b211b1b2-11e4-4316-87b7-98a3d10f95d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Comment&#160;: associer une page Web &#224; un dossier Outlook par programmation
  Cet exemple vérifie la présence d'un dossier nommé `HtmlView` dans Microsoft Office Outlook.  Si le dossier n'existe pas, le code crée le dossier et lui assigne une page Web.  Si le dossier existe, le code en affiche le contenu.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Exemple  
 [!code-csharp[Trin_OL_HTMLFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_HTMLFolder/CS/thisaddin.cs#1)]  
  
## Voir aussi  
 [Utilisation des dossiers](../vsto/working-with-folders.md)   
 [Comment : récupérer un dossier par nom par programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Comment : créer des éléments de dossier personnalisés par programmation](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  