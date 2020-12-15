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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6813a137558a245c66d4b24deac07b1a6a77796a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524603"
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
