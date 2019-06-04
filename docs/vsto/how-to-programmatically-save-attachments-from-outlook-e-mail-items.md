---
title: 'Procédure : Enregistrer des pièces jointes à partir d’éléments de messagerie Outlook par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d222924e753db1b476a5d7729e2c794a8ab305e2
ms.sourcegitcommit: c6249a8f3054db881ba62f4e80bf006d440f5a2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66462123"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Procédure : Enregistrer des pièces jointes à partir d’éléments de messagerie Outlook par programmation

Cet exemple enregistre les pièces jointes de messagerie électronique dans un dossier spécifié lorsque le courrier est reçu dans la Boîte de réception.

> [!IMPORTANT]
> Cet exemple fonctionne uniquement si vous ajoutez un dossier nommé **TestFileSave** à la racine du répertoire C.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>Voir aussi

- [Travailler avec des éléments de messagerie](../vsto/working-with-mail-items.md)
- [Guide pratique pour Récupérer par programme un dossier par nom](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Guide pratique pour Effectuer des actions par programme lorsqu’un message électronique est reçu.](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Guide pratique pour Rechercher par programmation dans un dossier spécifique](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
