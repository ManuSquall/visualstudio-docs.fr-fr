---
title: "Comment : accéder par programmation à des Contacts Outlook | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 4d4d88416507f7e63cd112df350dc93b2e13605f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
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
  
  