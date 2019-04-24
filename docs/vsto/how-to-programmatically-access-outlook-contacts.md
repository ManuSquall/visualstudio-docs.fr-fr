---
title: 'Procédure : Accéder par programmation aux contacts Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a9fc9cf214a8aebd663a7de29528790aa3cc0b46
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104224"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Procédure : Accéder par programmation aux contacts Outlook
  Cet exemple recherche tous les contacts dont le nom contient une chaîne de recherche spécifié.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite :

- Les contacts dont le nom contient la chaîne «**Na «** (par exemple, Tzipi Butnaru) dans le **Contacts** dossier.

## <a name="see-also"></a>Voir aussi
- [Utiliser des éléments de contact](../vsto/working-with-contact-items.md)
- [Guide pratique pour Ajouter par programmation une entrée aux contacts Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Guide pratique pour Rechercher un contact spécifique par programmation](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Guide pratique pour Rechercher une adresse de messagerie dans les contacts par programmation](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Guide pratique pour Supprimer des contacts Outlook par programmation](../vsto/how-to-programmatically-delete-outlook-contacts.md)
