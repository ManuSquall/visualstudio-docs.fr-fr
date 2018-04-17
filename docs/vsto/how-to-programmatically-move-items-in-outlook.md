---
title: 'Comment : déplacer par programmation des éléments dans Outlook | Documents Microsoft'
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
ms.openlocfilehash: a9eca20d533ba429db8b4227d5620c507fd805a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Comment : déplacer des éléments dans Outlook par programmation
  Cet exemple déplace les messages électroniques non lus à partir de la **boîte de réception** dans un dossier nommé **Test**. L’exemple déplace uniquement les messages qui ont le mot **Test** dans le `Subject` champ.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Un dossier de messagerie Outlook nommé **Test**.  
  
-   Un message entrant avec le mot **Test** dans le `Subject` champ.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des dossiers](../vsto/working-with-folders.md)   
 [Comment : récupérer un dossier par nom de programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Comment : rechercher dans un dossier spécifique par programmation](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Guide pratique pour exécuter des actions lors de la réception d’un message électronique par programmation](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  