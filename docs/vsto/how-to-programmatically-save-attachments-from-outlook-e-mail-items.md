---
title: 'Comment : enregistrer des pièces jointes à partir d’éléments de messagerie Outlook par programmation | Documents Microsoft'
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
ms.openlocfilehash: b3ca0f8c86b31576fd5ce219a536725431b27007
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-save-attachments-from-outlook-e-mail-items"></a>Comment : enregistrer des pièces jointes à partir d'éléments de messagerie Outlook par programmation
  Cet exemple enregistre les pièces jointes de messagerie électronique dans un dossier spécifié lorsque le courrier est reçu dans la Boîte de réception.  
  
> [!IMPORTANT]  
>  Cet exemple fonctionne uniquement si vous ajoutez un dossier nommé **TestFileSave** à la racine du répertoire C.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des éléments de messagerie](../vsto/working-with-mail-items.md)   
 [Comment : récupérer un dossier par nom de programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Comment : effectuer des Actions par programme lors de la réception d’un Message électronique](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [Guide pratique pour effectuer des recherches dans un dossier spécifique par programmation](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  