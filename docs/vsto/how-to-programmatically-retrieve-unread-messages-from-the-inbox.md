---
title: Obtenir des messages non lus à partir de la boîte de réception par programmation
description: Découvrez comment vous pouvez utiliser Visual Studio pour récupérer par programme des messages non lus dans votre boîte de réception dans Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], unread mail
- Outlook [Office development in Visual Studio], unread mail
- unread e-mail
- mail items [Office development in Visual Studio], unread mail
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 82bd595b76a03ee730995e546fd9c4e827c95a53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953849"
---
# <a name="how-to-programmatically-retrieve-unread-messages-from-the-inbox"></a>Comment : récupérer des messages non lus de la boîte de réception par programmation
  Cet exemple récupère des messages électroniques non lus à partir de la **boîte de réception** Outlook et affiche le nombre d’éléments.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-vb[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_UnreadItems/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_UnreadItems/thisaddin.cs#1)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des éléments de messagerie](../vsto/working-with-mail-items.md)
- [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Comment : créer un élément de courrier électronique par programmation](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Comment : envoyer un message électronique par programmation](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Comment : effectuer des actions par programmation lors de la réception d’un message électronique](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
