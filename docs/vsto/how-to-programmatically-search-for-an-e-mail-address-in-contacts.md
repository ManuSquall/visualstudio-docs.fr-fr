---
title: 'Comment : rechercher une adresse de messagerie dans les Contacts par programmation | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 16b79f5f14f1e0d8c5c82a00f5f2ccf2412b991b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
  