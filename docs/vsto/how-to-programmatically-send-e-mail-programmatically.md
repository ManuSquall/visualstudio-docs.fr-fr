---
title: 'Procédure : Envoyer par programmation un e-mail'
ms.date: 02/02/2017
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
ms.openlocfilehash: 280b4f526bad3e0ba646058b3e2410a98ca910fe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646003"
---
# <a name="how-to-programmatically-send-email"></a>Procédure : Envoyer par programmation un e-mail
  Cet exemple envoie un message électronique à des contacts dont le nom de domaine **example.com** dans leurs adresses de messagerie.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite :

-   Contacts dont le nom de domaine **example.com** dans leurs adresses de messagerie.

## <a name="robust-programming"></a>Programmation fiable
 Ne supprimez pas le code de filtre qui recherche le nom de domaine **example.com**. Votre solution enverra des messages électroniques à l’ensemble de vos contacts si vous supprimez le filtre.

## <a name="see-also"></a>Voir aussi
- [Travailler avec des éléments de messagerie](../vsto/working-with-mail-items.md)
- [Guide pratique pour Créer par programmation un élément de courrier électronique](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Guide pratique pour Accéder par programmation aux contacts Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Guide pratique pour Effectuer des actions par programme lorsqu’un message électronique est reçu.](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
