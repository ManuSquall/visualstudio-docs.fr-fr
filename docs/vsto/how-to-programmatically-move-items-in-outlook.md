---
title: 'Comment : déplacer des éléments dans Outlook par programmation'
description: Découvrez comment déplacer des éléments par programmation dans Microsoft Outlook. Cet exemple déplace les messages électroniques non lus de la boîte de réception vers un dossier nommé test.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 770f056dc681e1ee2cd6704f9bd1d42afae4957b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888860"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Comment : déplacer des éléments dans Outlook par programmation
  Cet exemple déplace les messages électroniques non lus de la **boîte de réception** vers un dossier nommé **test**. L’exemple déplace uniquement les messages qui contiennent le mot **test** dans le `Subject` champ.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite :

- Un dossier de messagerie Outlook nommé **test**.

- Message électronique qui arrive avec le mot **test** dans le `Subject` champ.

## <a name="see-also"></a>Voir aussi
- [Utiliser des dossiers](../vsto/working-with-folders.md)
- [Comment : récupérer un dossier par nom par programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Comment : effectuer une recherche par programmation dans un dossier spécifique](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Comment : effectuer des actions par programmation lors de la réception d’un message électronique](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
