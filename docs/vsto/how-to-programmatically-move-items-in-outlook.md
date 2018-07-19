---
title: 'Comment : déplacer des éléments dans Outlook par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fced6a5e41d2b79d32575f20d224f75053acb988
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257720"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Comment : déplacer des éléments dans Outlook par programmation
  Cet exemple déplace les messages électroniques non lus à partir de la **boîte de réception** dans un dossier nommé **Test**. L’exemple déplace uniquement les messages qui contiennent le mot **Test** dans le `Subject` champ.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple nécessite :  
  
-   Un dossier de courrier Outlook nommé **Test**.  
  
-   Un message électronique entrant avec le mot **Test** dans le `Subject` champ.  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des dossiers](../vsto/working-with-folders.md)   
 [Comment : récupérer par programme un dossier par nom](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Comment : effectuer une recherche par programme dans un dossier spécifique](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Comment : effectuer des actions par programme lors de la réception d’un message électronique](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  