---
title: 'Comment : accéder par programmation aux contacts Outlook'
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
ms.openlocfilehash: 6ee09e0d0a51675bc00b19aedd0508276cb0cb09
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255939"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Comment : accéder par programmation aux contacts Outlook
  Cet exemple recherche tous les contacts dont le nom contient une chaîne de recherche spécifié.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple nécessite :  
  
-   Les contacts dont le nom contient la chaîne «**Na «** (par exemple, Tzipi Butnaru) dans le **Contacts** dossier.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des éléments de contact](../vsto/working-with-contact-items.md)   
 [Comment : ajouter par programmation une entrée aux contacts Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Comment : rechercher un contact spécifique par programmation](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Comment : rechercher une adresse de messagerie dans les contacts par programmation](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Comment : supprimer des contacts Outlook par programmation](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  