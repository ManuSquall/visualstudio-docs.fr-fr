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
ms.openlocfilehash: b8e951ab393d09506ad4f2d593962ea1826eff09
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826731"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Comment : déplacer des éléments dans Outlook par programmation
  Cet exemple déplace les messages électroniques non lus de la **boîte de réception** vers un dossier nommé **test**. L’exemple déplace uniquement les messages qui contiennent le mot **test** dans le `Subject` champ.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite :

- Un dossier de messagerie Outlook nommé **test**.

- Message électronique qui arrive avec le mot **test** dans le `Subject` champ.

## <a name="see-also"></a>Voir aussi
- [Utiliser des dossiers](../vsto/working-with-folders.md)
- [Comment : récupérer un dossier par nom par programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Comment : effectuer une recherche par programmation dans un dossier spécifique](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Comment : effectuer des actions par programmation lors de la réception d’un message électronique](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
