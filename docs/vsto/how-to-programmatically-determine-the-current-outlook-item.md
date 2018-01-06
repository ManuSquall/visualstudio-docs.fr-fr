---
title: "Comment : déterminer par programme l’élément Outlook actuel | Documents Microsoft"
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
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
ms.assetid: b4fb5ccd-b297-463e-9208-1fec42482531
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 112a2c1273b0087eea98736a4e47ac5de8787149
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Comment : déterminer l'élément Outlook actuel par programmation
  Cet exemple utilise l’événement Explorer.SelectionChange pour afficher le nom du dossier actuel et des informations sur l’élément sélectionné. Le code affiche ensuite l’élément sélectionné.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Rendez-vous, contacts et éléments de messagerie dans Microsoft Office Outlook.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du modèle d’objet Outlook](../vsto/outlook-object-model-overview.md)   
 [Comment : récupérer un dossier par nom de programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Guide pratique pour rechercher un contact spécifique par programmation](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  