---
title: Effectuer des actions par programmation si un message électronique est reçu
description: Découvrez comment vous pouvez utiliser Visual Studio pour exécuter des actions personnalisées par programmation si un courrier électronique est reçu dans Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], actions when e-mail is received
- NewMail event
- mail items [Office development in Visual Studio], custom actions
- e-mail [Office development in Visual Studio], custom actions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 22dbd3ae72ac8c269de603ce22bbfebef669be08
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523881"
---
# <a name="how-to-programmatically-perform-actions-when-an-email-message-is-received"></a>Comment : effectuer des actions par programmation lors de la réception d’un message électronique
  Cet exemple effectue des actions personnalisées quand l’utilisateur reçoit un message électronique.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-vb[Trin_Outlook_RL_PerformActions#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_PerformActions/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_PerformActions#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_PerformActions/thisaddin.cs#1)]

## <a name="see-also"></a>Voir aussi
- [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Utiliser des éléments de messagerie](../vsto/working-with-mail-items.md)
- [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
