---
title: "Comment&#160;: rechercher une adresse de messagerie dans les contacts par programmation"
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
  - "courrier électronique (développement Office dans Visual Studio), rechercher"
  - "contacts (développement Office dans Visual Studio), rechercher"
  - "rechercher des contacts"
ms.assetid: e973a407-8b94-45c7-acdf-fe330115fb33
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Comment&#160;: rechercher une adresse de messagerie dans les contacts par programmation
  Cet exemple recherche dans un dossier de contacts les contacts dont l’adresse de messagerie contient le nom de domaine **example.com**.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Exemple  
 [!code-csharp[Trin_OL_SearchEmail#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_SearchEmail/CS/thisaddin.cs#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Des contacts dont l’adresse de messagerie contient le nom de domaine **example.com** \(par exemple, `somebody@example.com`\) et qui possèdent un prénom et un nom.  
  
## Voir aussi  
 [Utilisation des éléments de contact](../vsto/working-with-contact-items.md)   
 [Comment : envoyer un message électronique par programmation](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Comment : accéder à des contacts Outlook par programmation](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Comment : ajouter une entrée aux contacts Outlook par programmation](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  