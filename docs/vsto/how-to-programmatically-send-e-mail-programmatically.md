---
title: 'Comment : envoyer par programme un e-mail'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32977852ffbc4bb1411ed699cc97bb54035fada4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673589"
---
# <a name="how-to-programmatically-send-email"></a>Comment : envoyer par programme un e-mail  
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
 [Travailler avec des éléments de messagerie](../vsto/working-with-mail-items.md)   
 [Comment : créer par programmation un élément de courrier électronique](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Comment : accéder par programmation aux contacts Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Comment : effectuer des actions par programme lors de la réception d’un message électronique](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  