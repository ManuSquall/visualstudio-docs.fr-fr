---
title: 'Comment : Rechercher un contact spécifique par programmation'
description: Découvrez comment vous pouvez utiliser Visual Studio pour rechercher un contact spécifique dans Microsoft Outlook par programmation.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: afe17292db70f2d2fdd16e7c7b388343fbf9db9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841943"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>Comment : Rechercher un contact spécifique par programmation
  Cet exemple recherche dans un dossier de contacts Outlook un contact spécifique par nom et prénom. L’exemple suppose qu’un contact nommé **John Evans** existe dans le dossier de contacts.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des éléments de contact](../vsto/working-with-contact-items.md)
- [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
