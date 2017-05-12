---
title: "Comment&#160;: envoyer un message &#233;lectronique par programmation"
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
  - "messagerie électronique (développement Office dans Visual Studio), envoyer"
  - "éléments de messagerie (développement Office dans Visual Studio), envoyer un message électronique"
  - "Outlook (développement Office dans Visual Studio), créer un message électronique"
  - "Outlook (développement Office dans Visual Studio), envoyer un message électronique"
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Comment&#160;: envoyer un message &#233;lectronique par programmation
  Cet exemple envoie un courrier électronique à des contacts dont l'adresse de messagerie a pour nom de domaine **example.com**.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Exemple  
 [!code-csharp[Trin_OL_ProgramEmail#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_ProgramEMail/CS/thisaddin.cs#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Des contacts dont l'adresse de messagerie a pour nom de domaine **example.com**.  
  
## Programmation fiable  
 Ne supprimez pas le code de filtre qui recherche le nom de domaine **example.com**.  Si vous supprimez le filtre, votre solution enverra des courriers électroniques à tous vos contacts.  
  
## Voir aussi  
 [Utilisation d'éléments de messagerie](../vsto/working-with-mail-items.md)   
 [Comment : créer un élément de messagerie par programmation](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Comment : accéder à des contacts Outlook par programmation](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Comment : exécuter des actions lors de la réception d'un message électronique par programmation](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  