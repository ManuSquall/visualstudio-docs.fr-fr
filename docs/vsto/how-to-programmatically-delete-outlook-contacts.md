---
title: 'Comment : supprimer des contacts Outlook par programmation'
description: Découvrez comment vous pouvez supprimer des contacts par programmation dans Microsoft Outlook. Cet exemple supprime un contact.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deleting contacts
- contacts [Office development in Visual Studio], deleting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 98ee7773c86e85fa9ced0274bc37c4db3f8aacc2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963890"
---
# <a name="how-to-programmatically-delete-outlook-contacts"></a>Comment : supprimer des contacts Outlook par programmation
  Cet exemple supprime un contact. L’exemple suppose qu’un contact nommé "Armando Pinto" existe dans le dossier **Contacts** .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-vb[Trin_Outlook_RL_DeleteContacts#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_DeleteContacts/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_DeleteContacts#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_DeleteContacts/thisaddin.cs#1)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des éléments de contact](../vsto/working-with-contact-items.md)
- [Comment : Rechercher un contact spécifique par programmation](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Comment : accéder aux contacts Outlook par programmation](../vsto/how-to-programmatically-access-outlook-contacts.md)
