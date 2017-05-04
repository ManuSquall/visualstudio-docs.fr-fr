---
title: "Comment&#160;: d&#233;terminer l&#39;&#233;l&#233;ment Outlook actuel par programmation | Microsoft Docs"
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
  - "messagerie électronique (développement Office dans Visual Studio), élément actuel"
  - "éléments de messagerie (développement Office dans Visual Studio), actuels"
  - "Outlook (développement Office dans Visual Studio), élément actuel"
  - "SelectionChange (événement)"
ms.assetid: b4fb5ccd-b297-463e-9208-1fec42482531
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Comment&#160;: d&#233;terminer l&#39;&#233;l&#233;ment Outlook actuel par programmation
  Cet exemple utilise l'événement Explorer.SelectionChange pour afficher le nom du dossier actif ainsi que différentes informations à propos de l'élément sélectionné.  Le code affiche ensuite l'élément sélectionné.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Exemple  
 [!code-csharp[Trin_OL_CurrentItem#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/CS/thisaddin.cs#1)]
 [!code-vb[Trin_OL_CurrentItem#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/VB/thisaddin.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Un rendez\-vous, un contact et des éléments de courrier électronique dans Microsoft Office Outlook.  
  
## Voir aussi  
 [Vue d'ensemble du modèle d'objet Outlook](../vsto/outlook-object-model-overview.md)   
 [Comment : récupérer un dossier par nom par programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Comment : rechercher un contact spécifique par programmation](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  