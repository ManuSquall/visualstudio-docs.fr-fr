---
title: 'Comment : associer par programme une page web à un dossier Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2cb1ef525917288dc44609b899611db884da9073
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256463"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Comment : associer par programme une page web à un dossier Outlook
  Cet exemple vérifie un dossier nommé `HtmlView` dans Microsoft Office Outlook. Si le dossier n’existe pas, le code crée le dossier et lui assigne une page Web. Si le dossier existe, le code affiche le contenu du dossier.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des dossiers](../vsto/working-with-folders.md)   
 [Comment : récupérer par programme un dossier par nom](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Comment : créer par programmation des éléments de dossier personnalisés](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  