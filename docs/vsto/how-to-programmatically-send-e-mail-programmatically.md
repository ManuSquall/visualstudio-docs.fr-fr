---
title: 'Procédure : Envoyer un courrier électronique par programmation'
ms.date: 08/14/2019
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 72d033add2ba8320b14eebd5af700ab225d34410
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551755"
---
# <a name="how-to-programmatically-send-email"></a>Procédure : Envoyer un courrier électronique par programmation
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
- [Guide pratique pour Créer un élément de messagerie par programmation](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Guide pratique pour Accéder par programme aux contacts Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Guide pratique : Effectuer des actions par programme lors de la réception d’un message électronique](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
