---
title: "Comment : enregistrer des pièces jointes à partir d’éléments de messagerie Outlook par programmation | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: f87b05b45fafab3ad28a6da6a98391b8d121be7e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
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
  
  