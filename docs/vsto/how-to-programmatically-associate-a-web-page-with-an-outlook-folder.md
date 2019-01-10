---
title: 'Procédure : Associer par programme une page web à un dossier Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6dc6bec7ecbf872d10045cb24e007edec893585
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089633"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Procédure : Associer par programme une page web à un dossier Outlook
  Cet exemple vérifie un dossier nommé `HtmlView` dans Microsoft Office Outlook. Si le dossier n’existe pas, le code crée le dossier et lui assigne une page Web. Si le dossier existe, le code affiche le contenu du dossier.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des dossiers](../vsto/working-with-folders.md)   
 [Guide pratique pour Récupérer par programme un dossier par nom](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Guide pratique pour Créer par programmation des éléments de dossier personnalisés](../vsto/how-to-programmatically-create-custom-folder-items.md)  
