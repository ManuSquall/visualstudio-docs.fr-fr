---
title: "Comment&#160;: d&#233;placer des &#233;l&#233;ments dans Outlook par programmation | Microsoft Docs"
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
  - "dossiers Outlook (développement Office dans Visual Studio), déplacer des éléments"
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Comment&#160;: d&#233;placer des &#233;l&#233;ments dans Outlook par programmation
  Cet exemple déplace des courriers électroniques non lus de la **Boîte de réception** vers un dossier nommé **Test**.  L'exemple déplace seulement les messages qui présentent le mot **Test** dans le champ `Subject`.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Exemple  
 [!code-csharp[Trin_OL_MoveItems#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_MoveItems/CS/thisaddin.cs#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Un dossier de courrier Outlook nommé **Test**.  
  
-   Un courrier électronique entrant avec le mot **Test** dans le champ `Subject`.  
  
## Voir aussi  
 [Utilisation des dossiers](../vsto/working-with-folders.md)   
 [Comment : récupérer un dossier par nom par programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Comment : rechercher dans un dossier spécifique par programmation](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Comment : exécuter des actions lors de la réception d'un message électronique par programmation](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  