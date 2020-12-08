---
title: 'Comment : accéder aux contacts Outlook par programmation'
description: Découvrez comment vous pouvez accéder aux contacts Outlook par programmation. Cet exemple recherche tous les contacts dont le nom contient une chaîne de recherche spécifiée.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 68fe58f2f70a68c37d9171eb01f9294bb5e4d4af
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844685"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Comment : accéder aux contacts Outlook par programmation
  Cet exemple recherche tous les contacts dont le nom contient une chaîne de recherche spécifiée.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a> Exemple
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite :

- Les contacts dont le nom contient la chaîne «**na »** (par exemple, Tzipi Butnaru) dans le dossier **contacts** .

## <a name="see-also"></a>Voir aussi
- [Utiliser des éléments de contact](../vsto/working-with-contact-items.md)
- [Comment : ajouter une entrée aux contacts Outlook par programmation](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Comment : Rechercher un contact spécifique par programmation](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Comment : Rechercher une adresse de messagerie dans les contacts par programmation](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Comment : supprimer des contacts Outlook par programmation](../vsto/how-to-programmatically-delete-outlook-contacts.md)
