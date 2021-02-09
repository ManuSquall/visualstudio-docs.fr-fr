---
title: 'Comment : envoyer un message électronique par programmation'
description: Utilisez Visual Studio pour envoyer par programme un e-mail à partir de Microsoft Outlook. Cet exemple envoie un message électronique aux contacts dont le nom de domaine est example.com.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c2b702d2986315ce32a9ab489db239f2c784f3e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877861"
---
# <a name="how-to-programmatically-send-email"></a>Comment : envoyer un message électronique par programmation
  Cet exemple envoie un message électronique aux contacts dont le nom de domaine est **example.com** dans leurs adresses e-mail.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite :

- Contacts dont le nom de domaine est **example.com** dans leurs adresses e-mail.

## <a name="robust-programming"></a>Programmation fiable
 Ne supprimez pas le code de filtre qui recherche le nom de domaine **example.com**. Votre solution enverra des messages électroniques à tous vos contacts si vous supprimez le filtre.

## <a name="see-also"></a>Voir aussi
- [Utiliser des éléments de messagerie](../vsto/working-with-mail-items.md)
- [Comment : créer un élément de courrier électronique par programmation](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Comment : accéder aux contacts Outlook par programmation](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Comment : effectuer des actions par programmation lors de la réception d’un message électronique](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
