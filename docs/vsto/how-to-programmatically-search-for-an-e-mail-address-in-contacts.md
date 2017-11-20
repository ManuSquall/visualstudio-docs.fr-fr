---
title: "Comment : rechercher une adresse de messagerie dans les Contacts par programmation | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
ms.assetid: e973a407-8b94-45c7-acdf-fe330115fb33
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 272a24a7d07e5a04ab4a92c06ee98a0c0efa5de8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-search-for-an-e-mail-address-in-contacts"></a>Comment : rechercher une adresse de messagerie dans les contacts par programmation
  Cet exemple recherche dans un dossier de contacts les contacts dont l’adresse de messagerie contient le nom de domaine **example.com** .  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Des contacts dont l’adresse de messagerie contient le nom de domaine **example.com** (par exemple, `somebody@example.com`) et qui possèdent un prénom et un nom.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des éléments de Contact](../vsto/working-with-contact-items.md)   
 [Comment : envoyer des messages électroniques par programmation](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Comment : accéder par programmation à des Contacts Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Guide pratique pour ajouter une entrée aux contacts Outlook par programmation](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  