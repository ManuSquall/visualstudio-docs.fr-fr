---
title: 'Comment : enregistrer des pièces jointes à partir d’éléments de messagerie Outlook par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd564b71622ad5f9ee6500ddc3864bad0b21686b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671184"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Comment : enregistrer des pièces jointes à partir d’éléments de messagerie Outlook par programmation
  Cet exemple enregistre les pièces jointes de messagerie électronique dans un dossier spécifié lorsque le courrier est reçu dans la Boîte de réception.  
  
> [!IMPORTANT]  
>  Cet exemple fonctionne uniquement si vous ajoutez un dossier nommé **TestFileSave** à la racine du répertoire C.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des éléments de messagerie](../vsto/working-with-mail-items.md)   
 [Comment : récupérer par programme un dossier par nom](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Comment : effectuer des actions par programme lors de la réception d’un message électronique](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [Comment : effectuer une recherche par programme dans un dossier spécifique](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  