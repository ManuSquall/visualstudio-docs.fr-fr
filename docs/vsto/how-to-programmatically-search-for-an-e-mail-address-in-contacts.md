---
title: Rechercher une adresse de messagerie dans les contacts par programmation
description: Découvrez comment vous pouvez utiliser Visual Studio pour rechercher par programme une adresse de messagerie dans vos contacts Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 43baafee82cf38dfd346ebe50e9b348857a3fdc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920459"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Comment : Rechercher une adresse de messagerie dans les contacts par programmation
  Cet exemple recherche dans un dossier de contacts les contacts dont l’adresse de messagerie contient le nom de domaine **example.com** .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite :

- Des contacts dont l’adresse de messagerie contient le nom de domaine **example.com** (par exemple, `somebody@example.com`) et qui possèdent un prénom et un nom.

## <a name="see-also"></a>Voir aussi
- [Utiliser des éléments de contact](../vsto/working-with-contact-items.md)
- [Comment : envoyer un message électronique par programmation](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Comment : accéder aux contacts Outlook par programmation](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Comment : ajouter une entrée aux contacts Outlook par programmation](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
