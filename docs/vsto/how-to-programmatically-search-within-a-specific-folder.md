---
title: "Comment : rechercher dans un dossier spécifique par programmation | Documents Microsoft"
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
helpviewer_keywords: Outlook folders [Office development in Visual Studio], searching
ms.assetid: 8f2cdc8b-f757-412c-aa2b-ebd5bc52f697
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 97776e667333d00ecbd10feeb12620b16f2d3ac9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Comment : rechercher dans un dossier spécifique par programmation
  Cet exemple de code utilise le `Find` et `FindNext` méthodes pour rechercher du texte dans le champ objet des messages électroniques qui se trouvent dans le **boîte de réception**. Cette méthode utilise un filtre de chaîne pour vérifier la lettre T en tant que la lettre de départ de la `Subject` texte.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des dossiers](../vsto/working-with-folders.md)   
 [Vue d’ensemble du modèle d’objet Outlook](../vsto/outlook-object-model-overview.md)   
 [Guide pratique pour récupérer un dossier par nom par programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  