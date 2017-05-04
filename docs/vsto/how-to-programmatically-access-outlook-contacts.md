---
title: "Comment&#160;: acc&#233;der &#224; des contacts Outlook par programmation | Microsoft Docs"
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
  - "contacts (développement Office dans Visual Studio), rechercher"
ms.assetid: ea2297ea-6802-40e4-af1a-1e511a71ec75
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Comment&#160;: acc&#233;der &#224; des contacts Outlook par programmation
  Cet exemple recherche tous les contacts dont le nom contient une chaîne de recherche spécifiée.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Exemple  
 [!code-csharp[Trin_OL_AccessContacts#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/CS/trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/CS/backup/trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/VB/thisaddin.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Des contacts dont le nom contient la chaîne "**Na"** \(par exemple, Tzipi Butnaru\), dans le dossier **Contacts**.  
  
## Voir aussi  
 [Utilisation des éléments de contact](../vsto/working-with-contact-items.md)   
 [Comment : ajouter une entrée aux contacts Outlook par programmation](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Comment : rechercher un contact spécifique par programmation](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Comment : rechercher une adresse de messagerie dans les contacts par programmation](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Comment : supprimer des contacts Outlook par programmation](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  