---
title: 'Procédure : Déplacer des éléments dans Outlook par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3dcbfbe7b6e6ac5bacb9e8e36e43d780d3051903
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108969"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Procédure : Déplacer des éléments dans Outlook par programmation
  Cet exemple déplace les messages électroniques non lus à partir de la **boîte de réception** dans un dossier nommé **Test**. L’exemple déplace uniquement les messages qui contiennent le mot **Test** dans le `Subject` champ.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite :

- Un dossier de courrier Outlook nommé **Test**.

- Un message électronique entrant avec le mot **Test** dans le `Subject` champ.

## <a name="see-also"></a>Voir aussi
- [Travailler avec des dossiers](../vsto/working-with-folders.md)
- [Guide pratique pour Récupérer par programme un dossier par nom](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Guide pratique pour Rechercher par programmation dans un dossier spécifique](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Guide pratique pour Effectuer des actions par programme lorsqu’un message électronique est reçu.](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
