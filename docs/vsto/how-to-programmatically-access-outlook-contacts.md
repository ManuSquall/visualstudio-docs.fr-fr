---
title: 'Comment : accéder par programmation à des Contacts Outlook | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c48a58a4215ce73bcc6e9f4593819cbbdbed1693
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Comment : accéder à des contacts Outlook par programmation
  Cet exemple recherche tous les contacts dont le nom contient une chaîne de recherche spécifié.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Les contacts dont le nom contient la chaîne «**Na »** (par exemple, Tzipi Butnaru) dans le **Contacts** dossier.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des éléments de Contact](../vsto/working-with-contact-items.md)   
 [Comment : ajouter par programmation une entrée aux Contacts Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Comment : rechercher un Contact spécifique par programmation](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Comment : rechercher une adresse de messagerie dans les Contacts par programmation](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Guide pratique pour supprimer des contacts Outlook par programmation](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  