---
title: Associer une page Web à un dossier Outlook
description: Découvrez comment associer une page Web à Microsoft Office dossier Outlook. Cet exemple recherche un dossier nommé HtmlView dans Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 35fad43f78d654cfaf9e06c1f432c620da830dd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885571"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Associer une page Web à un dossier Outlook

  Cet exemple recherche un dossier nommé `HtmlView` dans Microsoft Office Outlook. Si le dossier n’existe pas, le code crée le dossier et lui attribue une page Web. Si le dossier existe, le code affiche le contenu du dossier.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des dossiers](../vsto/working-with-folders.md)
- [Comment : récupérer un dossier par nom par programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Comment : créer des éléments de dossier personnalisés par programmation](../vsto/how-to-programmatically-create-custom-folder-items.md)
